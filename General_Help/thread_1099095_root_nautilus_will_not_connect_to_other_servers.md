---
title: "root nautilus will not connect to other servers"
date: 2009-03-17
forum: General Help
---

### Post by MountainX on 2009-03-17
As a standard user I can connect to various servers with nautilus such as SSH, FTP, Windows Share and WebDAV.

When I run as "*gksu nautilus*", the only option is "custom location" and when I try to manually define an SSH (sftp) server connection, I get the error:

Couldn't display "sftp://myuser@myserver".
**"Nautilus cannot handle sftp: locations."**

What is the solution for this?

_[COLOR=Red]**UPDATE:**[/COLOR]_
I tried the following approach (without really understanding what it does):
 ```
gksu "dbus-launch nautilus --no-desktop"
```

The result was:
```
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension

** (nautilus:28057): WARNING **: Unable to add monitor: Not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```
However, Nautilus did open and it did have all the expected choices for connecting to remote servers.

Any ideas what is going on?

---

### Post by dcstar on 2009-03-17
> **MountainX said:**
> As a standard user I can connect to various servers with nautilus such as SSH, FTP, Windows Share and WebDAV.

When I run as "*gksu nautilus*", the only option is "custom location" and when I try to manually define an SSH (sftp) server connection, I get the error:

Couldn't display "sftp://myuser@myserver".
**"Nautilus cannot handle sftp: locations."**

What is the solution for this?

_[COLOR=Red]**UPDATE:**[/COLOR]_
I tried the following approach (without really understanding what it does):
 ```
gksu "dbus-launch nautilus --no-desktop"
```

The result was:
```
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension

** (nautilus:28057): WARNING **: Unable to add monitor: Not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```
However, Nautilus did open and it did have all the expected choices for connecting to remote servers.

Any ideas what is going on?

Create a desktop launcher using "gksudo" ilo "gksu" and all will be well.

You shouldn't launch nautilus from a terminal anyway so those messages mean little.

---

### Post by MountainX on 2009-03-17
> **dcstar said:**
> Create a desktop launcher using "gksudo" ilo "gksu" and all will be well.

You shouldn't launch nautilus from a terminal anyway so those messages mean little.

When I create a launcher as you described, I am back to the original problem -- nautilus will not allow me to connect to remote servers via SSH (or anything else I've tried).

---

### Post by dcstar on 2009-03-18
> **MountainX said:**
> When I create a launcher as you described, I am back to the original problem -- nautilus will not allow me to connect to remote servers via SSH (or anything else I've tried).

I can browse Windows networks and connect to them, but I don't have others to test.

---

### Post by MountainX on 2009-03-18
> **dcstar said:**
> I can browse Windows networks and connect to them, but I don't have others to test.

Thanks for your feedback. I have a Windows network and I cannot connect/browse when I open Nautilus as root. I'll assume this is either a bug in Hardy (what version are you running?) or a problem with my installation itself.

---

