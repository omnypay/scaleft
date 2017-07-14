scaleft Cookbook
================
Installs and configures ScaleFT server tools

Requirements
------------
Only works with RHEL and Debian based distros.

Attributes
----------

** NOTE: if the Default is `nil` below, that means it does not override the
default of the ScaleFT options as described at
https://www.scaleft.com/docs/sftd/#common-configuration-options**

#### scaleft::default
<table>
  <tr>
    <th>Key</th>
    <th>Type</th>
    <th>Description</th>
    <th>Attribute Default</th>
    <th>ScaleFT Default</th>
  </tr>
  <tr>
    <td><tt>['scaleft']['initial_url']</tt></td>
    <td>String</td>
    <td>your scaleft endpoint</td>
    <td>nil</td>
    <td>unset</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['access_address']</tt></td>
    <td>String</td>
    <td>For hosts with multiple interfaces, or behind DNATs; specifies the address clients will use when connecting to this host</td>
    <td>nil</td>
    <td>unset</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['alt_names']</tt></td>
    <td>String</td>
    <td>A list of alternative hostnames for this server. These names can be used as targetnames in sft ssh</td>
    <td>nil</td>
    <td>unset</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['auto_enroll'] </tt></td>
    <td>String</td>
    <td>When true, sftd will attempt to automatically enroll with ScaleFT on initial startup</td>
    <td>nil</td>
    <td>true</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['bastion']</tt></td>
    <td>String</td>
    <td>Specifies the bastion-host clients will automatically use when connecting to this host</td>
    <td>nil</td>
    <td>unset</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['canonical_name']</tt></td>
    <td>String</td>
    <td>Specifies the name clients should use/see when connecting to this host. Overrides the name found with `hostname`</td>
    <td>nil</td>
    <td>unset</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['log_level']</tt></td>
    <td>String</td>
    <td>Controls the logging verbosity. Valid values are WARN, INFO or DEBUG. Runing sftd with the --debug flag is equivalent to configuring a level of DEBUG, and will override values from the config file</td>
    <td>nil</td>
    <td>`INFO`</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['buffer_file']</tt></td>
    <td>String</td>
    <td>Path-prefix to the file(s) that sftd will use for it’s local buffer store. Individual buffers will have a ‘.’ and an incrementing number will be appended to the path-prefix. BufferFiles which have been synchronized will be removed automatically</td>
    <td>nil</td>
    <td>`/var/lib/sftd/buffer.db`</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['enrollment_token_file']</tt></td>
    <td>String</td>
    <td>Path to the file containing a secret token for token based enrollment. This file is deleted after a successful enrollment to the platform</td>
    <td>nil</td>
    <td>`/var/lib/sftd/enrollment.token`</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['server_file']</tt></td>
    <td>String</td>
    <td>Path to the file that sftd uses to store the server URL that it will connect to</td>
    <td>nil</td>
    <td>`/var/lib/sftd/device.server`</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['sshd_config_file']</tt></td>
    <td>String</td>
    <td>Path to sshd configuration file. *Note sftd will modify this file*</td>
    <td>nil</td>
    <td>`/etc/ssh/sshd_config`</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['token_file']</tt></td>
    <td>String</td>
    <td>Path to file that sftd uses to store its secret token for authentication to ScaleFT</td>
    <td>nil</td>
    <td>`/var/lib/sftd/device.token`</td>
  </tr>
  <tr>
    <td><tt>['scaleft']['trusted_user_ca_file']</tt></td>
    <td>String</td>
    <td>Path for sftd to write the list of trusted SSH Certificate authorities to</td>
    <td>nil</td>
    <td>`/var/lib/sftd/ssh_ca.pub`</td>
  </tr>
</table>

Usage
-----
#### scaleft::default

Just include `scaleft` in your node's `run_list`:

```json
{
  "name":"my_node",
  "normal": {
    "scaleft": {
      "initial_url": "https://scaleft.company.com"
    }
  },
  "run_list": [
    "recipe[scaleft]"
  ]
}
```

Contributing
------------
1. Fork the repository on Github
2. Create a named feature branch (like `add_component_x`)
3. Write your change
4. Write tests for your change (if applicable)
5. Run the tests, ensuring they all pass
6. Submit a Pull Request using Github

License and Authors
-------------------
Authors:: Jim Rosser (jim.rosser@rackspace.com)
