---
title: "new to nubunu &amp; having trouble!"
date: 2006-01-06
forum: Desktop Environments
---

### Post by jimmyxx on 2006-01-06
Hi everyone, a lad at work suggested I give nubuntu a go so I first installed it as a virtual machine on my work computer - for which it worked fine and really impressed me so I took the disc home (last night).

As soon as I got home and i wacked the disc in, installed it over my old debian pure partition, it seemed to install fine the only difference was that my home was not connected to the internet - my ISP was playing up last night. After installation I started playing with it - changing the theme etc, then when i put a cd in to play it opened JUK and said "reading track list from the internet", and frooze. I could move the cursor, but nothing else (note even escape to console).

I put the first freeze down to juk being stupid not realising I don't have the itnernet, i booted back up and used a different media player - this time the cd played fine, then a few minutes later while browsing nautilus the computer frooze again (the cursor still worked and music still played but nothing else).

I've been through all my log files the only thing that looks supicious is possibley the gconfd which seems to appear in the kernel logs just before the crashes. nothing else jumped out. I've tried as much as i know how to, mem-test, unmounting my unnesseary devices.

does anyone have any ideas?

thanks!

---

### Post by nalmeth on 2006-01-06
That sucks..
No idea man, but thought I'd bump your post.

---

### Post by endy on 2006-01-06
Have you tried setting up the net connection via:

System > Administration > Networking

I think the CD player fails because it tried to connect to the freedb, it shouldn't crash but I can't say I use I much so I don't know :S

If you still get stuck post the relevant part of the log file to help us diagnose the problem :)

---

### Post by Ubluntu on 2006-01-06
[quote=endy]Have you tried setting up the net connection via:

System > Administration > Networking

[/quote]

For some reason eth0 is deactivated by default on install, you just need to select it and click activate.

---

### Post by jimmyxx on 2006-01-09
Hi guys, thanks for you replies, well over the weekend I actually reinstalled the whole thing, this time i made sure that the ethernet cable was unplugged during install as my inet at home is still not fixed and i wanted to make sure the os didn't get confussed.

This time i thought it worked, however 20 minutes into using it the whole thing frooze again! :( the only thing I had done during this first 20 minutes was mount a fat32 file system and coppied some files across.

I think i'll have to go back to debian pure as i have no idea whats making my system freeze :( I was so looking forward to ubuntu!

---

### Post by firehead on 2006-01-09
since i don't know your system specs i have no idea wether this might be of any help to you,but i had a very similar problem when i first installed kubuntu on my pc. i could fix it by installing a new nvidia-driver (version 7667 i think). don't ask me why this worked (since i'm quite a linux-noob), but it did ;)

good luck

---

### Post by jimmyxx on 2006-01-10
ah-ha, ill defo give that a go as soon as my net is back up (as long as it doesn't freeze half way through!)

A guy at work suggested it might not be related to that though as I think it once crashed while i was in gnome-fail-safe mode. but i can't remeber if it was actually in that mode or if I just escaped to console.

but thanks anyway, ill give it a try.

---

