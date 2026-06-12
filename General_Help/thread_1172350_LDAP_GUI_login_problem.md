---
title: "LDAP GUI login problem"
date: 2009-05-28
forum: General Help
---

### Post by guedesav on 2009-05-28
I'm trying to configure a machine with Ubuntu 8.10 so it can perform login via LDAP authentication. The configuration works right, getent gives me the entities I need, etc. and I  even can perform login in the terminal. But I can't login via GDM, for reason unknown. After inputting my username and password, it gives me this error mesage:

> 
You must be a member of cn=g_lcc_ati_reitoria_funcionarios,ou=group,dc=ufmg,dc=br to login


Here is my ldap.conf archive(minus password configuration line, of course):

```

uri ldaps://oldap1.grude.ufmg.br
base dc=ufmg,dc=br
binddn cn=nssuser,ou=lcc,dc=ufmg,dc=br
bindpw ***********
pam_grouddn cn=g_lcc_ati_reitoria_funcionarios,ou=group,dc=ufmg,dc=br
pam_member_attribute member
ssl yes
tls_cacertfile /etc/ldap/ca.cert

nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,daemon,games,gdm,gnats,haldaemon,hplip,irc,klog,libuuid,list,lp,mail,man,messagebus,mysql,news,openldap,polkituser,proxy,pulse,root,saned,sshd,sync,sys,syslog,uucp,www-data

```

As I said, terminal login is possible, and I can also find the users information with ldapsearch and all... I've found some info here on a similar topic about some tutorial, but I wasn't able to find it.

Anyone knows what's wrong?

---

### Post by guedesav on 2009-06-02
Hello, again.

Fortunately, i've found my problem. The user's home directory wasn't being created. Adding the line

```
session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
```

to the pam.d/common-session file solved it.

Unfortuntely, the login starts, Gnome starts opening, and then it gives me an error message. On .xsession-error, the message:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=pt_BR.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Could not get password database information for UID of current process: User "???" unknown or no memory to allocate password entry

Failed to start message bus: Memory allocation failure in message bus
EOF in dbus-launch reading address from bus daemon

```

Any clues on why this happens?

---

### Post by guedesav on 2009-07-01
Turns out the problem was that nscd was not installed. Now my only problem is some weird error that HAL cannot start at the GNOME startup.

---

