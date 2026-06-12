---
title: "The configuration could not be loaded"
date: 2008-12-26
forum: General Help
---

### Post by Brausen on 2008-12-26
I can't change settings in **Users and groups**, **Services** and **Time and Date**. When I try open them I get this message:
> **The configuration could not be loaded**
You are not allowed to access the systema configuration
Even logged as root (running gksu) I get the same error. I tried many suggestions that I found searching in google, but without success. I found several threads about this issue but no one gives a definite answer -- especifically in Ubuntu 8.10.

Someone has any ideas to fix this problem?

PS. My user is in group "admin"

---

### Post by taurus on 2008-12-26
You can definitely use sudo.

```
sudo apt-get update
```

---

### Post by Brausen on 2008-12-26
I get the same problem when I use **sudo** or **gksu**

---

### Post by taurus on 2008-12-26
What is the exact error message when you run

```
sudo apt-get update
```
Can you post the outputs of these commands from a terminal?

```
id
cat /etc/hostname
cat /etc/host
```
You didn't by any change playing around with the file /etc/sudoers?

---

### Post by Brausen on 2008-12-26
I get this error:
> The configuration could not be loaded
You are not allowed to access the systema configuration

Just when I try open _Administration > Services_ or _Users and groups_. **sudo apt-get update** run properly, with no errors.

Here the outputs:
> $ id
uid=1000(asterion) gid=1000(asterion) groups=3(sys),4(adm),20(dialout),24(cdrom),29(audio),46(plugdev),108(lpadmin),123(admin),124(sambashare),126(lastfm),1000(asterion)

$ cat /etc/hostname 
cafarnaum

$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	cafarnaum
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I didn't any change in sudoers: 
> -r--r----- 1 root root 557 2008-12-26 20:17 /etc/sudoers

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


---

