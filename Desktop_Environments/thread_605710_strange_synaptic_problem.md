---
title: "strange synaptic problem"
date: 2007-11-07
forum: Desktop Environments
---

### Post by jaskah on 2007-11-07
hello

i am getting a strange message now when i try to install software with synaptic:

Please insert the disk labeled:
Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)
in drive /cdrom/

i had just run the following commands in the terminal to enable real-time use of the kernel:

sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'

could this have something to do with the message i'm getting in synaptic?
can anyone suggest a way to use synaptic again?

thanks in advance for any help!

---

### Post by taurus on 2007-11-07
Why don't you just edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, it will not ask you to insert the CD into a drive again.

Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jaskah on 2007-11-07
that's great...thanks so much for your help!

---

