---
title: "iPod won't mount"
date: 2009-06-24
forum: General Help
---

### Post by prettymess on 2009-06-24
When I plug in my iPod, it charges and shows the "Do not disconnect." screen, however ubuntu (9.04) doesn't read my iPod anymore.  It shows up as "USB Drive" in the Computer folder, but I can't eject it or mount it.  It used to work, but up until two days ago it stopped.  It's a 30 gb iPod video.  Rhythmbox doesn't pick it up either.  I've searched but I wasn't able to find any answers.

---

### Post by pi.theta on 2009-06-24
Does ubuntu show the eject icon next to USB Drive in the Places section of the File Browser?

---

### Post by prettymess on 2009-06-24
No, it doesn't.
[IMG]http://img141.imageshack.us/img141/5611/screenshotwfd.png[/IMG]

Also, when I used to plug my iPod in, an icon for it would pop up on the desktop, but it doesn't anymore.

---

### Post by LowSky on 2009-06-24
have you tried the ipod reset trick, slide the hod switch to hold then back, the hold the center and menu keys at the same time, until the ipod reboots.

at least yours still plays music, my 5.5 gen decided a week ago that it would not play audio anymore, this is about 6 months after it decided that it couldn't play itunes downloaded tv shows as well.

I'm considering ripping out the hard drive for a useful project.

---

### Post by prettymess on 2009-06-24
Yeah, I've tried resetting it and still nothing.  I connected it to a laptop with XP and it read it fine, so I'm not sure what's going on.

---

### Post by LowSky on 2009-06-24
reboot the ubuntu machine, then plug in the ipod, open a terminal and type 

```
lsusb
```
see if the device is shown on that list


or check nautilus and see if its listed on the side panel if it is but not mounted, well just mount the sucker.

---

### Post by prettymess on 2009-06-24
Okay, I did lsusb and got this:

Bus 002 Device 003: ID 05ac:1209 Apple, Inc. iPod Video

So, I guess it's on there, right?  What should I do now?

Also, is nautilus "Nautilus Actions Configuration?"  I installed it, but I'm not sure how to use it, 'cause I can't find where it's installed.

EDIT: Okay, I figure out what Nautilus is, and the iPod's not showing up on the side panel.

---

### Post by prettymess on 2009-06-25
Okay, so I just tried it with gtkpod, and it read it; however, it still isn't read by anything else.  I clicked Repository Options in gtkpod and in the general section it says the iPod mountpoint is /tmp/ipodS6zxcn .  Does that help anyone figure out what the problem is?  Is there a way to manually mount it, and if so, will that make it so Rythmbox can read it?

---

### Post by prettymess on 2009-06-25
Anybody?

---

### Post by chinaCat86 on 2009-06-27
Identical Problem. Help would be appreciated.

Also, this being my first post, hello ):P


EDIT:

Well, I really wish I knew how I fixed this, but I went through a lot of threads that suggested a lot of different ideas. I tried a lot, and being a newb learned a little. However, I solved the problem thanks to microsoft =\ I plugged it into an XP machine, opened itunes and ejected. I came back and rebooted my Ubunutu 9.04 and it worked like a charm. Odd, I really wish I knew what happened, but it seems to be a possible fix.

---

### Post by Max Williams on 2009-08-13
I just had this problem and solved it by accident.

The ipod was showing up in my nautilus side pane, but wasn't in my /media folder, and wasn't showing up in rhythmbox.  I'd tried unplugging it and resetting it with no luck.

I double-clicked on it in the side pane, and it opened ok.  Then, i happened to click on rhythmbox and noticed it was visible now.  It was also showing up in the media folder.

At a guess, i'd say that opening it forced some sort of device update to happen, and the system mounted it properly.  Although, my home NAS drive is also showing up in the media folder, even though i'm at work.  If i open that, it opens into an empty folder.  Odd.

---

### Post by muhammadg on 2009-08-13
while its plugged in try typing in the terminal **dmesg **then post all what you have

---

### Post by log1c on 2010-05-25
i was having the same problem (more or less) in lucid. i made a thread about it here: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9333982](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9333982) , but have still yet to get an answer

---

