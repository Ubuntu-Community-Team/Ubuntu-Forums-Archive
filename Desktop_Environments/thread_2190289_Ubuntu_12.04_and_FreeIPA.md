---
title: "Ubuntu 12.04 and FreeIPA"
date: 2013-11-26
forum: Desktop Environments
---

### Post by andrewprecht06 on 2013-11-26
Hi all,
I have installed the freeipa client and sssd from: ppa:freeipa/ppa and ppa:sssd/updates. With a little work, I got it to install, all but one of the SSH host keys (The host_mod: 2.58 client incompatible with 2.46 server, issue) That's OK I'll deal with that later.

I need some help getting my Ubuntu 12.04 client to use the IPA server for login. I can retrieve user account information from the ipa server at my Ubuntu workstation with the command: [COLOR=#0000ff]sudo id *username*[/COLOR]  However, when I try to login with this same *username* I get a:[COLOR=#ff0000] Invalid password please try again[/COLOR].

 I have tried this with several user accounts in the IPA database, however I can only log in with local accounts.
 

 Any help is appreciated.

---

### Post by andrewprecht06 on 2013-11-26
No replies:mad:
Has anyone got Ubuntu to work with FreeIPA?  Goggling the subject, it doesn't look promising.
Seems like a deal-breaker for Ubuntu in the enterprise...

---

### Post by andrewprecht06 on 2013-12-02
Here is what I'm seeing in the /var/log/auth.log

Dec  2 08:58:12 ubuntuap lightdm: PAM adding faulty module: pam_sss.so
Dec  2 08:58:17 ubuntuap lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "andrew"
Dec  2 08:58:25 ubuntuap lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=andrew
Dec  2 08:58:27 ubuntuap lightdm: PAM unable to dlopen(pam_sss.so): /lib/security/pam_sss.so: cannot open shared object file: No such file or directory

If I  run: sudo id andrew
I get:  uid=188000005(andrew) gid=188000005(andrew) groups=188000005(andrew),188000000(admins)

So, It looks to me that PAM is not using the FreeIPA server for authentication.

Can anyone assist?

---

### Post by andrewprecht06 on 2013-12-03
[FONT=arial]I've done some poking around on my Ubuntu client and found this interesting.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]From my Ubuntu client if I try to su (substitute user) to a user account on the IPA server (let's call it ipauser) I am promoted for a password. With the correct password I still get the response "su: Authentication failure"[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]If I try to su to a made-up name, I get the response "Unknown id:" So, it is safe to assume that the Ubuntu client is able to communicate with the IPA server to check for a valid user name. But, for some reason the password is not validated.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Now, If I run: sudo su ipauser I am prompted for the password of the local user I'm logged in as and after that a home directory is created for the ipauser, and I'm logged in as ipauser. If I run sudo as ipauser I am prompted for the ipsuser password, and that always responses with "Sorry, try again."[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Any clue as to why the Ubuntu client can check for user names on the IPA server but not passwords?[/FONT]

---

### Post by imotor on 2013-12-05
Have you tried a Fedora 17 client to auth to your free-ipa server? That at least might rule out a mis-configuration on the server. 

I sincerely hope you get this working&#8211;we are planning for a similar setup in our network.

---

### Post by Lee_Machine on 2014-02-25
Any luck with this? I'm in the process of setting up an isolated Linux only network with RHEL5/6 Fedora 18/19/20 and Ubuntu 12.04+ and would like to use FreeIPA client. It works just fine on RHEL and Fedora but not Ubuntu. 

I'm tempted to just setup a Windows DC and continue using PBIS to login with Windows Domain credentials like we are now. 

I don't have to time to dive into the nuts and bolts of setting up openLDAP and Kerberos whereas IPA is supposed to do all the work for me.

---

### Post by Lee_Machine on 2014-02-26
After much tinkering and rebooting I got it to work but the ipa-client process crashes sometimes.

I'll have to reproduce and document.

I write a howto and post it here

---

### Post by kill4killin on 2014-04-01
I realize this thread is a few weeks old now but hopefully by posting this someone, maybe OP, will see this and find it useful...

I'm running FreeIPA on a Redhat server and authenticating a mix of clients: Redhat, Fedora and Ubuntu. I've gotten this to work on Ubuntu using the following configuration files (sensitive information redacted).

/etc/sssd/sssd.conf:
The majority of this file was generated using the "ipa-client-install" command. I then modified the "ipa_server" line to remove "_srv_," and added the "ipa_hostname =" line.
```

[domain/example.domain.com]

cache_credentials = True
krb5_store_password_if_offline = True
ipa_domain = example.domain.com
id_provider = ipa
auth_provider = ipa
access_provider = ipa
ipa_hostname = hostname.example.domain.com
chpass_provider = ipa
ipa_server = ipaserver.example.domain.com
ldap_tls_cacert = /etc/ipa/ca.crt
[sssd]
services = nss, pam, ssh
config_file_version = 2

domains = example.domain.com
[nss]

[pam]

[sudo]

[autofs]

[ssh]

```

/etc/nsswitch.conf:
The below file is incomplete and probably still contains a lot of unecessary information since I'm still working on migrating from our old LDAP server to IPA but the above file is currently in production and working.
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

# pre_auth-client-config # passwd:         compat
passwd: files sss
#passwd: files ldap [NOTFOUND=return] db
# pre_auth-client-config # group:          compat
group: files sss
#group: files ldap  [NOTFOUND=return] db
# pre_auth-client-config # shadow:         compat
shadow: files ldap [NOTFOUND=return] db

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

# pre_auth-client-config # netgroup:       nis
netgroup: nis sss

```

If there are any other file examples that might be useful to anyone trying to solve this issue, I'm happy to post them. I believe these are the only really relevant ones. I've also got the following ldap/ipa/auth packages installed, not all of them may be necessary as I'm currently migrating from using openLDAP to IPA:

[LIST]
[*] freeipa-client
[*] nscd
[*] nslcd
[*] libnss-ldapd
[*] libpam-ldapd
[*] nss-updatedb
[*] libnss-db
[*] libpam-ccreds
[/LIST]

EDIT:
OH! I also forgot to mention that we have the following line in /etc/pam.d/common-account:
```
session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
```
and the a file in /usr/share/pam-configs/my_mkhomedir containing the following:
```

Name: activate mkhomedir
Default: yes 
Priority: 900 
Session-Type: Additional
Session:
    required        pam_mkhomedir.so umask=0022 skel=/etc/skel

```

---

