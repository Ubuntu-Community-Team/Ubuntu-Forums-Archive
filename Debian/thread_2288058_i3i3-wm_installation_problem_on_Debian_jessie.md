---
title: "i3/i3-wm installation problem on Debian jessie"
date: 2015-07-24
forum: Debian
---

### Post by nabz0r on 2015-07-24
Hi guys,

As the title says, I can't install this WM on my fresh new machine. I have been googling for the past 48h but I couldn't find any useful information that would help me resolve the issue.
Can you guys help me out here? All the help and inputs are appreciated, thanks!

Mods, sorry if I have posted in the wrong forum and feel free to move it to more suitable forum.

---

### Post by howefield on 2015-07-24
Thread moved to the "Debian" forum.

---

### Post by arochester on 2015-07-24
It's very odd that you have been Googling for 48 hours without finding an answer.

1) Connect to the Internet
2) Become Root by inputting into a Terminal: su 
3) Input you password
4) Input to the Terminal: apt-get install i3

---

### Post by nabz0r on 2015-07-24
I followed i3's steps:
> echo 'deb [http://build.i3wm.org/debian/sid](http://build.i3wm.org/debian/sid) sid main' > /etc/apt/sources.list.d/i3-autobuild.lis
apt-get update
apt-get --allow-unauthenticated install i3-autobuild-keyring
apt-get update
apt-get install i3

but I get the following error:

> walwar@debian:~$ sudo apt-get install i3Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 i3 : Depends: i3-wm (= 4.10.3-1+g4.10.2-234-ge89f3911) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


> walwar@debian:~$ sudo apt-get install i3-wmReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 i3-wm : Depends: libxkbcommon-x11-0 (>= 0.5.0) but 0.4.3-2 is to be installed
         Depends: libxkbcommon0 (>= 0.5.0) but 0.4.3-2 is to be installed
         Recommends: libanyevent-i3-perl (>= 0.12) but it is not going to be installed
         Recommends: libjson-xs-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages

---

### Post by arochester on 2015-07-24
Unable to correct problems, you have held broken packages.


Try, as Root: apt-get -f install

---

### Post by nabz0r on 2015-07-24
Already done that and it didn't resolve the issue. I even installed
> 
[COLOR=#000000][I]ibxkbcommon-x11-0 0.5.0 
[/I][/COLOR][COLOR=#000000]*libxkbcommon0 *[/COLOR][COLOR=#000000]*0.5.0*[/COLOR]

But still have the problem

---

### Post by arochester on 2015-07-24
Are you using Sid?  Why Sid?

What is the result of: cat /etc/debian_version

---

### Post by nabz0r on 2015-07-27
Sorry for the late reply, didn't have time in the weekend. 
I don't know what Sid is and those commands are from their website. I just followed their guide for installing i3 on Debian.

> walwar@debian:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Debian
Description:    Debian GNU/Linux 8.1 (jessie)
Release:    8.1
Codename:    jessie


---

### Post by arochester on 2015-07-27
Common advice on Debian User Forums is not to mix your sources list, which can break Debian for the inexperienced.  Debian basically comes in three forms STABLE currently Jessie, TESTING currently Stretch and UNSTABLE which is always Sid. You have added a bit of Sid to your sources list but you are using Jessie. [https://wiki.debian.org/DontBreakDebian/](https://wiki.debian.org/DontBreakDebian/)

Try removing the offending bit. 
In a Terminal (as Root)  use the command: nano  /etc/apt/sources.list.d
Delete any reference to Sid there.  Save. Close.
Then do (as Root): 
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get install i3

If it still doesn't work then ask at [http://forums.debian.net/](http://forums.debian.net/) ...

---

### Post by nabz0r on 2015-07-28
I had already done that before posting here. Removed the source, updated, upgraded, etc and tried to install i3 but it was then when I got the msg above about dependencies, etc.

Anyway, I have solved it, reinstalled Debian and installed i3 and everything is as it supposed to be. Thanks for your help good sir.

nabz0r

---

