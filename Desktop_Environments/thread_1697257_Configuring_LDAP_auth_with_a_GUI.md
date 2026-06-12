---
title: "Configuring LDAP auth with a GUI"
date: 2011-02-28
forum: Desktop Environments
---

### Post by tnine on 2011-02-28
Hi all,
  I've been using CentOS for quite a long time, and I've recently switched to Ubuntu 10.10 as a desktop.  I'm having one small stumbling block, I can't seem to setup LDAP authentication via a GUI.  I found this post here.

[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

Is there a GUI application that allows LDAP configuration similar to the Cent OS one?

Thanks,
Todd

---

### Post by tnine on 2011-03-07
Bump.  Anyone?

---

### Post by Xenomorph on 2011-07-28
I'm looking for the same.

Fedora/Red Hat/CentOS:

1) Install
2) Open Authentication page and add LDAP & Kerberos information.

Ubuntu:

1) Install
2) Google search LDAP HowTo pages
3) apt-get install a bunch of additional packages
4) Start hand-editing configuration files
5) Test, trial, and error.

---

### Post by scorp123 on 2011-07-29
Other distros such as RHEL, CentOS and SUSE are much friendlier in this regard, there you have GUI tools to quickly enable LDAP authentication when and where you need it ... Not so in Ubuntu unfortunately.

The best thing you could try is this Wiki which you have already found:
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)


In the "apt" repositories there is a package called **ldap-auth-config** and installing that one will cause the system to ask you a few things (in text mode) such as "Bind DN" etc. and in theory it should then auto-configure your system for LDAP authentication based on your answers .... Again: *in theory*. My experience with this package was rather disappointing, it seems to be buggy. Last time I looked at it was around Ubuntu 8.10 ... so maybe they fixed it now? You could try that.

What I do: Configure LDAP authentication with a contemporary SUSE system and then copy those config files over. This works pretty well and it's less frustrating.

If you have Active Directory you can use **LikeWise Open** ... there are packages in the repositories. And LikeWise Open does have a GUI which will allow you to easily join (and unjoin) an Ubuntu system to an Active Directory domain (packages: **likewise-open, likewise-open-gui**). So at least in the case of AD*authentication there would be no need to mess with LDAP and "winbind" etc., LikeWise Open can do all that automatically via a friendly GUI.

Pure LDAP (e.g. anything but Microsoft's AD) however is still pretty much a terminal and vi affair here on Ubuntu.

---

