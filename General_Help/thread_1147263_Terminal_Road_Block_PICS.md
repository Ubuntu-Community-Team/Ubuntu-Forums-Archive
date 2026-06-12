---
title: "Terminal Road Block? *PICS*"
date: 2009-05-03
forum: General Help
---

### Post by ToyotaGuy23 on 2009-05-03
Dell 1721 Inspiron 17"
802.11n, 17" 2.0GB / 250 GB / AMD

I am having quite a time installing anything from terminal.
There is some kind of problem with apt-get, dpkg, and java.

It doesn't matter what I try to install, the installation only goes so far, and then goes into an EULA screen (in terminal.)
I am unable to click "OK" or "AGREE" because ..... I'm in terminal.

Here are the visuals:

**matt@matt-laptop:~$ sudo apt-get install numlockx** [COLOR="Red"](Or any program for that matter)[/COLOR][b]
[sudo] password for matt:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
matt@matt-laptop:~$ sudo dpkg --configure -a
matt@matt-laptop:~$ sudo apt-get install numlockx
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
sun-java6-bin sun-java6-jre
Suggested packages:
sun-java6-fonts sun-java6-plugin ia32-sun-java6-plugin
Recommended packages:
libnss-mdns gsfonts-x11
The following NEW packages will be installed:
numlockx
The following packages will be upgraded:
sun-java6-bin sun-java6-jre
2 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0B/33.6MB of archives.
After this operation, 96.5MB of additional disk space will be used.
Do you want to continue [Y/n]?[/b]

I answer Yes, and get this screen.

[img]http://i3.photobucket.com/albums/y78/ToyotaGuy23/Screenshot-mattmatt-laptop.png[/img]

I can scroll through the entire thing, pg up/down whatever, I cannot click OK to proceed on through.  Cannot press enter, The thing won't accept my input while in terminal.  
What's going on?
What can I do?

Thanks

---

### Post by Barriehie on 2009-05-03
Have you tried using TAB to highlight what you're to enter?

Barrie

---

### Post by MaxIBoy on 2009-05-03
TAB/arrow keys to move between buttons, "enter" to select the button you've highlighted.

You can do the same thing in any graphical environment if your touchpad suddenly goes nuts at random intervals (yeah, I'm looking at *you*, xorg!)

---

