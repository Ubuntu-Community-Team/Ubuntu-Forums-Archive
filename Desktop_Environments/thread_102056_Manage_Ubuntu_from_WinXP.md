---
title: "Manage Ubuntu from WinXP"
date: 2005-12-11
forum: Desktop Environments
---

### Post by zwartg on 2005-12-11
Hi Folks,
Today I installed my first Linux-distribution ever, Ubuntu 5.10.
Never knew its that simple. Even was able to use my WLAN usb-dongle. Worked perfectly.
Now I'd like to take over the Ubuntu desktop from my Winxp laptop. I am able to ping the ubuntu machine, enable rdp on my winxp laptop and on the ubuntu system I enabled remote use (under Remote Desktop Preferences). But when I start the rdp-connection, I get the message "The client could not connect to the remote computer".
I am very sure my Firewall on my laptop is related to this problem, because I switched it off (temporarely).
Someone any ideas?

---

### Post by M3ta7h3ad on 2005-12-11
the MSTSC client deals with Terminal services (a microsoft thing :)), as opposed to VNC (the thing you just enabled on ubuntu) try a VNC client and use that... "should" (I say should as I havent tried it myself) work then. :)

---

### Post by zwartg on 2005-12-11
I might be missing one thing. Thought that VNC clients are fore connecting from a linux-system (ubuntu) to a Windows System with a VNC-server (f.i. TightVNC) running.
Are there VNC clients for windows also? :confused:

---

### Post by Kangaroo on 2005-12-11
Yes, try [http://www.ultravnc.com]("http://www.ultravnc.com")

---

### Post by johso on 2005-12-11
Well, you're right, but that's not the whole truth! :-)
VNC is for connecting from anything, to anything (that can run VNC servers and clients). I use UltraVNC to connect from Windows XP to my Ubuntu server ([http://ultravnc.sourceforge.net/](http://ultravnc.sourceforge.net/)). And a similar program to connect from OS X.
So just download UltraVNC, and type in the ip of your Ubuntu machine.
The Windows remote desktop doesn't work that way; that's only for Windows machines.

---

### Post by simplyw00x on 2005-12-11
You need to enable 'Remote Desktop' in System/Preferences/Remote Desktop in Gnome on Ubuntu. Then get a VNC client on the Windows machine and whack in the IP address of the Linux comp and you're away.

Guide [here]("http://ubuntuguide.org/#remotedesktop") (from unofficial HOWTO).

---

### Post by zwartg on 2005-12-11
Hi Guys, You have been all evry helpfull. This did the trick.
Thanks a lot.
Maybe till another time.
Greetz . Gerard

---

