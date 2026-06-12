---
title: "USB Raid"
date: 2009-03-14
forum: General Help
---

### Post by unplugged23 on 2009-03-14
Hey there, 

I was just experimenting with some usb;s and a usb hub, and thought it would be fun to make them into a raid group. My only problem is I don't know how. I opened the gnome partition editor (g-parted) and formatted all of the drives to the same file system, and applied the raid flag to all of them. I'm not quite sure where I should go from here. yes I know its a bit unpractical, but it would be of some assistance to me. Could anyone help me out?

---

### Post by cariboo on 2009-03-14
[This]("http://ubuntuforums.org/showthread.php?t=408461") is probably what you are looking for.

Jim

---

### Post by Weidbrewer on 2009-03-16
Funny thing is...I was having this same silly idea, myself...

---

### Post by Weidbrewer on 2009-03-16
Okay, so I got bored tonight and threw three USB drives into my laptop created a USB RAID.  A.)  I'm not an expert, and B.)  I didn't read all of the instructions above in detail.  They seem more geared towards a primary drive with backup, and the software RAIDs that I have done have always just been mass storage.   That being such, I can't say my method is better or worse - it's just the only one I can speak to.

[_These instructions_]("http://nodebox.metaforix.net/articles/running-software-raid-on-ubuntu") are short and simple.  The ones linked above give you much, much more information on the hows and whys.  To really understand what you're doing (and to not just do it) I'd read through those.

When I was finished, my RAID auto mounted without any problems on my next three boots.  Main thing I had to do in addition to the instructions was to chown the drive so that I had the permissions to write to it.

I hope this helps, and here's to doing pointless things just to see if they work.

---

