---
title: "Help!!!  Broken Remote Desktop"
date: 2010-01-27
forum: Desktop Environments
---

### Post by ZooDirt on 2010-01-27
Help!!!  I seem to have shanked Remote Desktop on my Ubuntu server.  Can you help?

So, I had it working just like I wanted.  I don't have a monitor, keyboard, or mouse attached. And I used to connect to my server via VNC when I needed a GUI crutch.  Things went south while I was tinkering around and I installed Mythbuntu.   Whoops!  Mythbuntu didn't work the way I thought it would and now I can't connect via VNC after I've removed Mythbuntu.

So, I've done “sudo apt-get purge” on several packages and then turned right around and did “sudo apt-get install” on the packages that I thought that I needed (minus Mythbuntu).  I went through the steps of  enabling vino-server like I have done before but to no avail.

Steps for enabling vino-server (Remote Desktop)

1.sudo vi /etc/gdm/gdm.conf 

[INDENT]I set AutomaticLoginEnabled to true and AutomaticLogin to the user that I want to be when I connect to the desktop.[/INDENT]

2.sudo restart gdm
3.gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
4.gconftool-2 -s -t bool /desktop/gnome/remote_access/prompt_enabled false
5.echo <my password> > /tmp/passwd
6.gconftool-2 -s -t string /desktop/gnome/remote_access/vnc_password `base 64 /tmp/passwd`
7.rm /tmp/passwd
8.sudo reboot

So previously after taking these steps, I would have been able to connect via “Chicken of the VNC”  (I'm a mac user).  But I get nothing.   I thought I would just try to fall back on the GUI, so I tried “ssh -X mycrappyserver “vino-preferences” and enabled the proper checkboxes, but still get nothing.  

My VNC port (5900) isn't open as I'm getting connection refused.   telnet mycrappyserver 5900 

Does anyone have any experience with getting this stuff fixed?    Any help will be much appreciated.

---

### Post by myth1914 on 2010-01-29
First, try rebooting.  (I know, you prob already have) 

If that doesn't work, but you still need to get some sort of VNC, I would reccommend ssh into the box and run:

> sudo aptitude -y install vnc4server && vnc4server

which will install a different vnc 4 server and prompt you to set up the screen.

Hopefully you have access to open 5901 if needed.  then connect to the screen with your viewer at <mycrappyserver>:5901 or whatever screen you've set

---

### Post by myth1914 on 2010-01-29
NOTE:  I've had my VNC vino kick me out as you describe when connected from a Win machine and copying with the mouse.  It kills the connection and will give me the connection refused until reboot.  Odd, but not devastating as I've just resorted to the cp command when needed.

---

