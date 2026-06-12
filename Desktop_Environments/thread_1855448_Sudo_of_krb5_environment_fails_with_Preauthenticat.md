---
title: "Sudo of krb5 environment fails with Preauthentication error message"
date: 2011-10-06
forum: Desktop Environments
---

### Post by Ginkel on 2011-10-06
I am setting up an 10.04 LTS environment for the software development party of my company. At the moment they are still using 8.04, and are dying for the 10.04 release (yes, I know 12.04 will be with us within 6 months, but they want to upgrade now).

We are using Windows 2008 AD as authentication, with two local accounts for management and offsite access. The LDAP authentication is handled through the combination of krb5, pam and yp. I am fairly familiar with Linux, but on the krb5/pam/yp department I am lacking a lot of knowledge.

At the moment it is possible to login using your AD account. However if a user who is listed in the sudoers file tries to sudo, it denies the password (though it is entered correctly). When we use a local account which is also in the sudoers file, we can sudo to root to manage the environment.

I am suspecting something inside pam.d, however I am puzzled to what it might be.

First the configuration files:

**krb5.conf**
```

[libdefaults]
	default_realm = SOME.DOMAIN.COM
	clockskew = 300
	krb4_config = /etc/krb.conf
	krb4_realms = /etc/krb.realms
	kdc_timesync = 1
	ccache_type = 4
	forwardable = true
	proxiable = true
	v4_instance_resolve = false
	v4_name_convert = {
		host = {
			rcmd = host
			ftp = ftp
		}
		plain = {
			something = something-else
		}
	}
	fcc-mit-ticketflags = true

[realms]
	SOME.DOMAIN.COM = {
		kdc = win2003ad.some.domain.com
		default_domain = SOME.DOMAIN.COM
		admin_server = win2003ad.some.domain.com
	}

[domain_realm]
	.SOME.DOMAIN.COM = SOME.DOMAIN.COM

[appdefaults]
    pam = {
debug = true
            ticket_lifetime = 10h
            renew_lifetime = 9h
            forwardable = true
            proxiable = false
            retain_after_close = false
            minimum_uid = 0
            try_first_pass = true
    }

[logging]
    default = FILE:/var/log/krb5.log

[login]
	krb4_convert = true
	krb4_get_tickets = false


```

**yp.conf**
```

domain internal server 10.10.10.1

```

**pam.d/common-password**
```

password	requisite			pam_krb5.so minimum_uid=1000
password	[success=2 default=ignore]	pam_unix.so obscure use_authtok try_first_pass sha512
password	[success=1 default=ignore]	pam_winbind.so use_authtok try_first_pass
password	requisite			pam_deny.so
password	required			pam_permit.so
password	optional			pam_smbpass.so nullok use_authtok use_first_pass
password	optional	pam_gnome_keyring.so 

```

**pam.d/common-auth**
```

auth	[success=3 default=ignore]	pam_krb5.so minimum_uid=1000
auth	[success=2 default=ignore]	pam_unix.so nullok_secure try_first_pass
auth	[success=1 default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
auth	requisite			pam_deny.so
auth	required			pam_permit.so
auth	optional			pam_smbpass.so migrate

```
**pam.d/common-account**
```

account	[success=2 new_authtok_reqd=done default=ignore]	pam_unix.so 
account	[success=1 new_authtok_reqd=done default=ignore]	pam_winbind.so 
account	requisite			pam_deny.so
account	required			pam_permit.so
account	required			pam_krb5.so minimum_uid=1000

```

**pam.d/sudo**
```

@include common-auth
@include common-account
@include common-password

```

Snip from /var/log/auth.log:
```

Oct  6 14:22:29 lxdevenvnx sudo: pam_krb5(sudo:auth): pam_sm_authenticate: entry (0x8000)
Oct  6 14:22:29 lxdevenvnx sudo: pam_krb5(sudo:auth): (user user123) attempting authentication as user123@SOME.DOMAIN.COM
Oct  6 14:22:32 lxdevenvnx sudo: pam_krb5(sudo:auth): (user user123) krb5_get_init_creds_password: Preauthentication failed
Oct  6 14:22:32 lxdevenvnx sudo: pam_krb5(sudo:auth): authentication failure; logname=user123 uid=0 euid=0 tty=/dev/pts/1 ruser= rhost=
Oct  6 14:22:32 lxdevenvnx sudo: pam_krb5(sudo:auth): pam_sm_authenticate: exit (failure)
Oct  6 14:22:32 lxdevenvnx sudo: pam_unix(sudo:auth): authentication failure; logname=user uid=0 euid=0 tty=/dev/pts/1 ruser= rhost=  user=user123
Oct  6 14:22:33 lxdevenvnx sudo: pam_krb5(sudo:auth): pam_sm_authenticate: entry (0x8000)
Oct  6 14:22:33 lxdevenvnx sudo: pam_krb5(sudo:auth): (user user123) attempting authentication as user123@SOME.DOMAIN.COM
Oct  6 14:22:35 lxdevenvnx sudo: pam_krb5(sudo:auth): (user user123) error getting password: Authentication failure
Oct  6 14:22:35 lxdevenvnx sudo: pam_krb5(sudo:auth): authentication failure; logname=user123 uid=0 euid=0 tty=/dev/pts/1 ruser= rhost=
Oct  6 14:22:35 lxdevenvnx sudo: pam_krb5(sudo:auth): pam_sm_authenticate: exit (failure)
Oct  6 14:22:36 lxdevenvnx sudo: pam_unix(sudo:auth): conversation failed
Oct  6 14:22:36 lxdevenvnx sudo: pam_unix(sudo:auth): auth could not identify password for [user123]

```


Edit: I have tested it with a colleague, who has an account of 8 characters (I have tested it previously with my own account, 9 characters long - user123 is a replacement of the actual value due to company restrictions), and it functions like a charm. So I am now looking at the NIS server, perhaps there is something bogus with the Windows - UNIX account mapping there for my account.

---

