---
title: "Debian packages?"
date: 2005-04-29
forum: Desktop Environments
---

### Post by trotsky on 2005-04-29
Hi.

I'm a Debian user, and I'm considering changing to Ubuntu. I have some questions though.

Can I install debian packages with ubuntu's apt-get/synaptic? I do understand that debian system related packages may not be compatible with Ubuntu, but what about smaller programs and games, can I install them on Ubuntu?

Does Ubuntu have additional CD's with packages like debian?

Is there no root user in Ubuntu? I've read about the "sudo" command and it confuses me a bit.

Can I install and use KDE on Ubuntu? What is Kubuntu?

I must add that I've downloaded your Live Cd, and I liked it very much. I guess it's mostly Gnome 2.10 that's attractive.

Thank you
/Trotsky

---

### Post by defkewl on 2005-04-29
Can I install debian packages with ubuntu's apt-get/synaptic? I do understand that debian system related packages may not be compatible with Ubuntu, but what about smaller programs and games, can I install them on Ubuntu?
- Yes you can. I've tried installing few packages I've downloaded from debian repo

Does Ubuntu have additional CD's with packages like debian?
- I don't think so. CMIIW

Is there no root user in Ubuntu? I've read about the "sudo" command and it confuses me a bit.
- By default there isn't. But you can use root terminal and change the root password

Can I install and use KDE on Ubuntu?
- Yes you can 

What is Kubuntu?
- An Ubuntu distribution with KDE as WM

I must add that I've downloaded your Live Cd, and I liked it very much. I guess it's mostly Gnome 2.10 that's attractive.

---

### Post by MaX on 2005-04-29
[QUOTE=trotsky]Hi.

I'm a Debian user, and I'm considering changing to Ubuntu. I have some questions though.

Can I install debian packages with ubuntu's apt-get/synaptic? I do understand that debian system related packages may not be compatible with Ubuntu, but what about smaller programs and games, can I install them on Ubuntu?[/QUOTE]

Yes you can
[QUOTE=trotsky]
Does Ubuntu have additional CD's with packages like debian?[/QUOTE]
No not at the moment, probably in the upcoming DVD version
[QUOTE=trotsky]Is there no root user in Ubuntu? I've read about the "sudo" command and it confuses me a bit.[/QUOTE]
You can ```
sudo passwd root
``` to enable the root account

[QUOTE=trotsky]Can I install and use KDE on Ubuntu? What is Kubuntu?[/QUOTE]
Kubuntu is Ubuntu with KDE, you should apt-get Kubuntu if KDE is what you want to use
[QUOTE=trotsky]
I must add that I've downloaded your Live Cd, and I liked it very much. I guess it's mostly Gnome 2.10 that's attractive.

Thank you
/Trotsky[/QUOTE]

---

### Post by az on 2005-04-29
"Can I install debian packages with ubuntu's apt-get/synaptic? I do understand that debian system related packages may not be compatible with Ubuntu, but what about smaller programs and games, can I install them on Ubuntu"

No.  Do not.  Use Universe.

This did not work with Warty and the only reason it currently works with Hoary is luck.  In a little while, Sarge or Sid will become incompatible enough with Ubuntu to screw you up.  Do not do it.  Use backports.

---

### Post by az on 2005-04-29
I told you so:

[http://ubuntuforums.org/showthread.php?p=152585#post152585](http://ubuntuforums.org/showthread.php?p=152585#post152585)

---

### Post by c_dog on 2005-04-29
> Can I install debian packages with ubuntu's apt-get/synaptic? I do understand that debian system related packages may not be compatible with Ubuntu, but what about smaller programs and games, can I install them on Ubuntu?
Yes you can, but if you start mixing in debian versions of programs Ubuntu already has you will quickly run into a bloated Dependency Hell because the Ubuntu's and Debian's libraires are not always named the same conventions  for nearly identical code.

> 
Does Ubuntu have additional CD's with packages like debian?
Yes and No, The Ubuntu Hoary 5.04 DVD release has the Live, Ubuntu, Kubuntu, the Main repository and some of the Restricted repository all on 1 disk. The rest of the  Restricted, Universe , and Multiverse repositories are only available via FTP or HTTP.

> 
Is there no root user in Ubuntu? I've read about the "sudo" command and it confuses me a bit.
The first primary user is by default given super user access with their password and the Super User password being the same. Root commands are entered within 'sudo' shells. You can set up a "root" account, but it's not necessary in Ubuntu or advisable. There isn't any housekeeping setup in in Ubuntu for things you may do in a pure "/root" account if you activate it. In other words, you'll have to take out your own .trash.

---

