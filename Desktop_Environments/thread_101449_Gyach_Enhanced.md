---
title: "Gyach Enhanced"
date: 2005-12-09
forum: Desktop Environments
---

### Post by mztriz on 2005-12-09
Has anyone used this before? Does it work in ubuntu? 

This is the website [http://www.phrozensmoke.com/projects/pyvoicechat/index.php](http://www.phrozensmoke.com/projects/pyvoicechat/index.php)
I have no idea how to install it so yeah... but what would you recommend for yahoo chatrooms (with voice).

---

### Post by leech on 2005-12-09
use 'sudo alien <package name>' to convert an rpm to .deb, then of course just 'sudo dpkg -i <package name>' to install it.  Though unfortunately dpkg will not resolve dependecies, so you may have to 'sudo apt-get -f install' and it will either install the depedencies for you, or will remove the package that does not have the right dependencies.  In the case of gyache, it should have the dependencies in the repositories, so you should have no problems with this :D

Hope that helps.  Leech

---

### Post by mztriz on 2005-12-09
[QUOTE=leech]use 'sudo alien <package name>' to convert an rpm to .deb, then of course just 'sudo dpkg -i <package name>' to install it.  Though unfortunately dpkg will not resolve dependecies, so you may have to 'sudo apt-get -f install' and it will either install the depedencies for you, or will remove the package that does not have the right dependencies.  In the case of gyache, it should have the dependencies in the repositories, so you should have no problems with this :D

Hope that helps.  Leech[/QUOTE]

Oh, cool thanks! I'm trying it right now. :)

---

### Post by mztriz on 2005-12-09
ok I *think* I got it to install.
But, **where** did it install to? lol

```
root@ubuntu2:/home/mztriz# cd /home/mztriz/mztriz
root@ubuntu2:/home/mztriz/mztriz# sudo alien Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586
File "Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586" not found.
root@ubuntu2:/home/mztriz/mztriz# sudo alien /home/mztriz/mztriz/Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm

gyach-enhanced-pyvoicechat_1.0.7-2_i386.deb generated
root@ubuntu2:/home/mztriz/mztriz#
root@ubuntu2:/home/mztriz/mztriz# sudo dpkg -i /home/mztriz/mztriz/gyach-enhanced-pyvoicechat_1.0.7-2_i386.deb
Selecting previously deselected package gyach-enhanced-pyvoicechat.
(Reading database ... 64375 files and directories currently installed.)
Unpacking gyach-enhanced-pyvoicechat (from .../gyach-enhanced-pyvoicechat_1.0.7-2_i386.deb) ...
Setting up gyach-enhanced-pyvoicechat (1.0.7-2) ...
root@ubuntu2:/home/mztriz/mztriz# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by mztriz on 2005-12-10
Anyone have any ideas? :confused:

thanks.

---

### Post by albuquerque on 2007-07-29
I managed to install it on my feisty fawn. 
Type gyach at command prompt to launch GyachE.

i think the location must be '/usr/local/bin/gyach' at least it is on mine :)

Unable to get Room List thou. Gyache core dumps :(

---

