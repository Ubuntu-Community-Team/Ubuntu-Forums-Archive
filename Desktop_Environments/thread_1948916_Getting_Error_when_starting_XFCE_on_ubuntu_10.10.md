---
title: "Getting Error when starting XFCE on ubuntu 10.10"
date: 2012-03-29
forum: Desktop Environments
---

### Post by Ravi5kumar on 2012-03-29
Hi, I yesterday installed XFCE desktop environment on Ubuntu 10.10. But whenever I start XFCE on ubuntu it display a dialog saying : 

[B]"Could not look up internet address for Ubuntu 10.10.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
Ubuntu 10.10 to the file /etc/hosts on your system."[/B]

So what can I done to remove this annoying dialog box:mad:??

Also I cannot log out or turn off my computer. When I click on shut down or log off my computer nothing happens. If I again click on log off or shut down button it says:

[B]"Failed to receive a reply from the session manager

Session manager must be in idle state when requesting a shutdown"[/B]

So please tell me how to fix;)!

Regards,
Ravi

---

### Post by Krytarik on 2012-03-29
In Lucid 10.04, I can replicate that error message, plus a broken Logout icon at the panel, when I try to change the system's "hostname" to "Ubuntu 10.10", or "Ubuntu 10.04", for that matter: you cannot use spaces, as well as no underscores, in the hostname!

So if you insist on reflecting the current Ubuntu version in your system's hostname, you can set it like that: "Ubuntu-10.10". Or else, just choose an entirely different name, of course.

After settling for a new, proper hostname, set up both your "/etc/hostname" and your "/etc/hosts" like this:

[LIST]
[*]```
sudo nano /etc/hostname
```"/etc/hostname":
```
Ubuntu-10.10
```
[/LIST]

[LIST]
[*]```
sudo nano /etc/hosts
```"/etc/hosts":
```
127.0.0.1    localhost
127.0.1.1    Ubuntu-10.10

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
[/LIST]
Thereafter, just reboot to make the changes take effect.

Regards.

---

### Post by mörgæs on 2012-03-29
A different approach is to ditch 10.10, as it has only one month of support left, and install 11.10 (or 12.04 beta).

---

### Post by Krytarik on 2012-03-29
> **mörgæs said:**
> A different approach is to ditch 10.10, as it has only one month of support left, and install 11.10 (or 12.04 beta).
Yeah, but that obviously wouldn't help if the OP does the same with those, too :P - that is, tinkering with the hostname after the installation in an improper manner. So it's better to know the source of that issue, and know how to fix it. ;-)

---

### Post by Ravi5kumar on 2012-03-31
Thank You [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") it solved my problem\\:D/! Market the thread a solved as you said!

> A different approach is to ditch 10.10, as it has only one month of support left, and install 11.10 (or 12.04 beta).

It is also a solution but I love Gnome 2 than Unity or Gnome 3! I hate unity because :
1) It is more optimised for touch screen not desktops!
2) If you add too many launchers in unity dock you will get a horrible dock with a ugly icons.
3) Cannot control windows. That is cannot maximise or minimise windows.
4) Global Menu is really bad!

This makes to switch to switch me to KDE or XFCE! So I will install Kubuntu 12.04 or Xubuntu 12.04! Still I will try ubuntu 12.04 as I heard it got lot of improvement! Thanks for replying!!):P

---

