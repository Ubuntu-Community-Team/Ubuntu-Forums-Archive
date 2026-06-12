---
title: "GNOME Setting Daemon startup error"
date: 2008-08-09
forum: Desktop Environments
---

### Post by Greenknight04 on 2008-08-09
I'm running Ubuntu 8.04 on the HP 2133 mini-note, the little laptop from HP. Every time I boot up, it gets to the login screen fine, and I log in. Then, it creates a white square in the top right corner of the screen, and starts loading up. It loads up to the main screen, and I am presented with the following error message as a pop-up.

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

After a short period I can close it and proceed normally, but if I force quit it restarts the system. Is this an issue with Ubuntu, GNOME, or something else? Thanks in advance to anyone who might help.

---

### Post by phidia on 2008-08-09
There are some posts here that claim opening System->Administration->Network and changing it back to localhost then rebooting will fix this.

You can try that-hope it helps.

---

### Post by Greenknight04 on 2008-08-10
> **phidia said:**
> There are some posts here that claim opening System->Administration->Network and changing it back to localhost then rebooting will fix this.

You can try that-hope it helps.

I tried it- thanks for the suggestion- but it didn't work. I changed it to localhost, then restarted. It did exactly the same thing as before.

---

### Post by Greenknight04 on 2008-08-11
I had a realization on this issue. When I was first configuring the internet, I was using an ethernet cable to connect. Whenever I started the computer with the ethernet cable plugged in, it would go to the same screen with a blank white square in the corner at load-up, and then stop. Does that help at all?

---

### Post by adam_kimber on 2008-08-11
Check this forum thread and its links. Especially the blog link one [http://ubuntuforums.org/showthread.php?t=577946&page=3]("http://ubuntuforums.org/showthread.php?t=577946&page=3")

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by Greenknight04 on 2008-08-12
> **adam_kimber said:**
> Check this forum thread and its links. Especially the blog link one [http://ubuntuforums.org/showthread.php?t=577946&page=3]("http://ubuntuforums.org/showthread.php?t=577946&page=3")

That doesn't quite seem to solve the problem- all the people who had such issues were missing something in their etc/network/interfaces file. Mine looks like;

"auto lo
iface lo inet loopback


iface eth0 inet dhcp
<info here>




iface wlan0 inet dhcp
<info here>
auto eth0

auto wlan0
"

Is there something wrong with that configuration in my /etc/network/interfaces file?

---

### Post by CrusaderAD on 2008-08-12
I've got the same issue. It seems to be connected to the LAN but no internet connection, no way to remote desktop a connection either... will post if I find anything.

---

### Post by CrusaderAD on 2008-08-12
I got the gnome-settings-daemon error and found a resolution... well it seems to have worked. Refer to the last few posts in:

[http://ubuntuforums.org/showthread.php?t=868450&page=2](http://ubuntuforums.org/showthread.php?t=868450&page=2)

Unplugging the machine for a few minutes seems to reset the card. There's no error when logging back in, but still no internet connection. My network interfaces file looks to be ok... getting there.

---

### Post by Greenknight04 on 2008-08-12
> **raptormanad said:**
> I got the gnome-settings-daemon error and found a resolution... well it seems to have worked. Refer to the last few posts in:

[http://ubuntuforums.org/showthread.php?t=868450&page=2](http://ubuntuforums.org/showthread.php?t=868450&page=2)

Unplugging the machine for a few minutes seems to reset the card. There's no error when logging back in, but still no internet connection. My network interfaces file looks to be ok... getting there.

Good luck with that. I'm in a slightly different situation- for one, I have an internet connection- but I'll check out the page. Thanks again- I'll let you know if I find anything.

Edit: Seems that that thread addresses an issue of internet connection, not of said error message. Not entirely what I was looking for.

---

### Post by Greenknight04 on 2008-08-12
Bump

---

### Post by CrusaderAD on 2008-08-13
Unplugging the machine for a few minutes resolved the error message for me. As for the internet connection, it was my switch. I just plugged it into another router. All seems well now.

---

### Post by CrusaderAD on 2008-08-13
Unplugging the machine for a few minutes resolved my error message issue. As for my internet connection, it was my switch throwing it off. I plugged it into a new router and all is well now.

---

### Post by Greenknight04 on 2008-08-21
> **raptormanad said:**
> Unplugging the machine for a few minutes resolved my error message issue. As for my internet connection, it was my switch throwing it off. I plugged it into a new router and all is well now.

My problem is I'm using a laptop, so I can't unplug the machine. That doesn't seem to help.

---

### Post by Greenknight04 on 2008-08-28
Bump

---

### Post by peterius on 2008-08-31
I'm really annoyed by the GNOME Settings Daemon thing.  But I think its just a bug in gnome.  I read elsewhere here a bunch of posts about renaming config files, etc.. maybe.

For me, it occurs if I stop and start X, its like if X exits, gnome doesn't properly clean everything up so when you try to start it up again, the gnome settings daemon is still running or something.  Its just an annoyance but it is a bug.

Although this network stuff is probably separate.

---

