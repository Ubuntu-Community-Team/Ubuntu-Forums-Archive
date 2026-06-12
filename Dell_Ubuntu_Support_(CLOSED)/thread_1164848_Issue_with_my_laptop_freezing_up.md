---
title: "Issue with my laptop freezing up"
date: 2009-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jikkujj on 2009-05-20
Hey everyone
I am having some trouble with my Dell 1420 laptop recently.
I had installed ubuntu 8.10 on my machine and have updated my machine
with all the latest updates.
Right now what happens is that unexpectedly, the screen starts flashing with
green and white lights and behind that you can see the desktop. But the keys dont
respond anymore. Once I reboot the laptop, things return to normal, till the next "flashing" episode.
Could anyone who has faced the same issue or knows what's wrong point out if this is
a software or hardware issue? 
Thanks for your consideration
JJJ

---

### Post by jikkujj on 2009-05-20
Bump.

---

### Post by jikkujj on 2009-05-23
bump .....
Come on people I know there are some really people out there who could venture a pretty good guess.

---

### Post by michael37 on 2009-05-23
Are you absolutely sure that it doesn't happen with other OS versions?  I suspect a hardware problem.

---

### Post by shiningkenmonster on 2009-05-23
the samething happen to be before. I have the dell mini 9 with the LPIA Ubuntu 8.04 installed. It has happen to be before!

From powerdown to powerup.. from the startscreen.. it turns from red to green to yellow than to white.. and it repeats. I would have to reboot it.

it happens to me about 1 out of every 30 times when i turn on my computer.

I have wrote something like this on the post. but people have just ignored me. I thought i had a minor thing.

I am running the dell mini 9 with the Ubuntu 9.04 netbook remix now. It still does that. but it rarely happens

---

### Post by jsonder on 2009-05-23
The one out of every 30 startups sounds like it is the checkdisk (disk integrity check) causing the visual problem.

I run metacity, no graphics enhancements.  Are you using compiz?

Anyway, the frequency sounds like it is related to the disk checks.

Have you tried going to /boot/grub/menu.lst and deleting "splash" from the top entry?  I routinely do this to my machines to avoid the splash screen and see the boot process.  {that has to be done as root; use "sudo gedit /boot/grub/menu.lst" for a gnome version of ubuntu}

---

### Post by shiningkenmonster on 2009-05-24
don't use compiz what so ever. Never turn it by default upon start up.

---

