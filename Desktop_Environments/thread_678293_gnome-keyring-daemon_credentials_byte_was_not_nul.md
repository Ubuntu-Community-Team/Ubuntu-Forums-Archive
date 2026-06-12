---
title: "gnome-keyring-daemon credentials byte was not nul"
date: 2008-01-25
forum: Desktop Environments
---

### Post by hackhawk on 2008-01-25
I am unable to connect to windows shares from my freshly installed Ubuntu 7.10 desktop system.  I previously had it working, but for some reason, I can't track down what has gone wrong.

Basically, it keeps prompting me to enter my network password, then never accepts it.  The error message in the log files is as follows.
```

Jan 15 15:18:21 LWS gnome-keyring-daemon[####]: Credentials byte was not nul

```
I have the system configured to logon to the windows network authenticating against active directory.  Any advice on this problem would be much appreciated.

/etc/nsswitch.conf
```
passwd:         compat winbind
group:          compat winbind
shadow:         compat
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

```

/etc/krb5.conf
```
[logging]

	default = FILE:/var/log/krb5.log

[libdefaults]
	default_realm = MYDOM.LOCAL
	ticket_lifetime	= 24000
	clock_skew	= 300

[realms]
MYDOM.LOCAL = {
	kdc = myserver
	admin_server = myserver
	default_domain = mydom.local
}

[domain_realm]
.mydom.local = MYDOM.LOCAL
mydom.local  = MYDOM.LOCAL

```

/etc/samba/smb.conf
```
[global]

kernel oplocks = yes
client use spnego = yes
client ntlmv2 auth = yes
encrypt passwords = yes
restrict anonymous = 2
server signing = auto
client signing = auto
template shell = /bin/bash
nt acl support = yes
winbind use default domain = yes
#change notify timeout = 0

domain master = no
local master = no
preferred master = 0
os level = 0

inherit permissions = yes
inherit acls = yes
acl compatibility = auto
force create mode = 0760

security = ADS
realm = MYDOM.LOCAL
workgroup = stva
password server = 10.#.#.#
wins support = no
wins server = 10.#.#.#
invalid users = root
winbind enum groups = no
winbind enum users = no

idmap uid = 10000-20000
idmap gid = 10000-20000

debuglevel = 2

server string = lws

```

/etc/pam.d/common-account
```
account	sufficient	pam_winbind.so
account	required	pam_unix.so
```

/etc/pam.d/common-auth
```
auth	sufficient	pam_winbind.so
auth	required	pam_unix.so nullok_secure use_first_pass
```

/etc/pam.d/common-password
```
password   required   pam_unix.so nullok obscure min=4 max=50 md5
```

/etc/pam.d/common-session
```
session	required	pam_unix.so
session	optional	pam_foreground.so
session	required	pam_mkhomedir.so umask=0022 skel=/etc/skel
```

---

