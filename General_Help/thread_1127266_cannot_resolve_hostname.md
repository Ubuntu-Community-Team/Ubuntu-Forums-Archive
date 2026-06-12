---
title: "cannot resolve hostname"
date: 2009-04-16
forum: General Help
---

### Post by theevilhamster on 2009-04-16
I have recently changed my hostname, and now, whenever I try to run a command, (e.g. "ifup" "aptitude" "ifconfig" etc.) it tells me my hostname cannot be found. In most cases, the command runs anyway, but how can I resolve this?

Thanks.

---

### Post by taurus on 2009-04-16
What are the outputs of these two commands from a terminal?

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by theevilhamster on 2009-04-16
cat /etc/hostname gives

toast


cat /etc/hosts gives

127.0.0.1	linux	localhost.localdomain	localhost
127.0.1.1	linux

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts




("toast" is my new hostname, "linux" my old one (yeah, i know, it sucked, thats why i changed it :)))

---

### Post by taurus on 2009-04-16
> **theevilhamster said:**
> cat /etc/hostname gives

[COLOR="Red"]toast[/COLOR]


cat /etc/hosts gives

127.0.0.1	**[COLOR="Red"]linux[/COLOR]**	localhost.localdomain	localhost
127.0.1.1	**[COLOR="Red"]linux[/COLOR]**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts




("toast" is my new hostname, "linux" my old one (yeah, i know, it sucked, thats why i changed it :)))

Then you need to change linux in /etc/hosts (both lines) to toast since the name of your computer needs to be the same in both, /etc/hostname & /etc/hosts.

To do that, you need to boot into recovery mode from GRUB menu and drop into root shell.  Then, edit /etc/hosts as

```
nano -Bw /etc/hosts
```
Once you are done with editing, save and exit with <Ctrl>x.

Then, reboot and see if it works now.

---

### Post by theevilhamster on 2009-04-16
Thanks! It appears that i hadnt changed the hosts file when i changed my hostname.;)

been a while since ive been on the forums, what happened to the "thanks" button and the "resolved" button? im sure its pretty obvious, but im quite busy and cant quite remember this.

thanks again!

---

### Post by Iowan on 2009-04-16
> **theevilhamster said:**
> been a while since ive been on the forums, what happened to the "thanks" button and the "resolved" button? im sure its pretty obvious, but im quite busy and cant quite remember this.
[http://ubuntuforums.org/showthread.php?t=1044714]("http://ubuntuforums.org/showthread.php?t=1044714")

---

### Post by theevilhamster on 2009-04-18
Ah well, thanks anyway guys!

(this will have to do as your thanks for now:))

---

