sa-ftp
======

[![Build Status](https://travis-ci.org/softasap/sa-ftp.svg?branch=master)](https://travis-ci.org/softasap/sa-ftp)

Note: FTP is considered extremely insecure nowadays. This role mostly indended for internal use, for example, with ONVIF cameras capable to
upload regular screenshots to some internal FTP server. If you need public facing ftp server - consider secure SFTP or SCP based access.


Example of use: check box-example

Configuration:
```YAML

custom_vsftpd_default_props:
    - {regexp: "^[#]?anonymous_enable=*", line: "anonymous_enable=NO"}
    - {regexp: "^[#]?local_enable=*", line: 'local_enable=YES'}
    - {regexp: "^[#]?write_enable=*", line: 'write_enable=YES'}
    - {regexp: "^[#]?chroot_local_user=*", line: 'chroot_local_user=YES'}

custom_vsftpd_users:
    - {
      username: ftp_user,
      password: ftp_password,
      comment: "This is ftp user"
      }   

```

Simple:

```YAML


     - {
         role: "sa-ftp",
         vsftpd_users: "{{custom_vsftpd_users}}"
       }

```


Advanced:

```YAML


     - {
         role: "sa-ftp",
         vsftpd_default_props: "{{custom_vsftpd_default_props}}",
         vsftpd_users: "{{custom_vsftpd_users}}"         
       }

```



Copyright and license
---------------------

Code licensed under the [BSD 3 clause] (https://opensource.org/licenses/BSD-3-Clause) or the [MIT License] (http://opensource.org/licenses/MIT).

Subscribe for roles updates at [FB] (https://www.facebook.com/SoftAsap/)
