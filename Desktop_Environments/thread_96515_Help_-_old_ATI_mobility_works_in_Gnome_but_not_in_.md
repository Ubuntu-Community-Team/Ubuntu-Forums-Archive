---
title: "Help - old ATI mobility works in Gnome but not in Xubuntu"
date: 2005-11-29
forum: Desktop Environments
---

### Post by videodrome on 2005-11-29
Hi.

I need help please. I did a plain install of Breezy on my older P3 Dell Inspiron 5000 laptop and everything worked fine. The ATI Rage Mobility P/M video card was detected fine and worked properly.

I then copied the xorg.conf file to a diskette.

Then I erased the hard disk and did a server install with Xubuntu-desktop and no Gnome.

After it installed, Xubuntu was running is VESA mode. It was very choppy looking and all of the fonts and edges were jagged and awful looking and slow.

So I copied the xorg.conf file back into the X11 directory, rebooted, and I've got a black screen now.

I've tried reconfiguring and editing the xorg.conf file resolution and all that with no luck.

Clearly the standard Gnome install installed something that the Xubuntu & the Server install didn't. What is it? This is not an instance of installing those newer ATI drivers or anything like that, because I never did any of that under Gnome.

I can't post my xorg.conf because the machine it is on is offline right now.

Thoughts? 

Thanks

---

### Post by videodrome on 2005-11-29
FYI Xorg.0.log is stating that there's an Inconsistent panel horizontal dimension: 1400 and 1401, even though it's set correctly afaik. Weird.

---

### Post by videodrome on 2005-11-29
Anyone have any thoughts before I am forced to put Gnome back on this machine? THanks

---

### Post by ranf on 2005-11-29
[QUOTE=videodrome]FYI Xorg.0.log is stating that there's an Inconsistent panel horizontal dimension: 1400 and 1401, even though it's set correctly afaik. Weird.[/QUOTE]
Post the log and your xorg.conf. Otherwise no one can really help.

---

