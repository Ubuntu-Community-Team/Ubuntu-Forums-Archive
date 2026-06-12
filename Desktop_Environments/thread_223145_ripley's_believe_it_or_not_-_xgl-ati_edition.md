---
title: "ripley's believe it or not - xgl-ati edition"
date: 2006-07-26
forum: Desktop Environments
---

### Post by cptnapalm on 2006-07-26
This is so strange i must share.

for most of today, i have been trying to get xgl to work.  please excuse the all lowercase as i am paranoid about this thing crashing.  anyhow, i missed the box, so i decided to reinstall xgl and compiz, but have it run all the time instead of just as a session.

so, i'm tearing my hair out, right and i'm getting nowhere.  xgl would run, but not compiz and it was nowhere near usable.  deciding one more howto could not hurt, i began following one dealing with mesa gl being used instead of ati's.

the howto said to uninstall the fglrx xserver and the linux restricted modules.  so i did.  after also setting my xorg.conf file to ati instead of fglrx.  also according to instructions. finally, it said reboot so down the rabbit hole i went.

now comes the oddness.  i sign in and xgl is running.  initially compiz is not but that gets fixed very quickly.  baffled, i look at my xorg.conf file.  indeed this is the ati driver.  there is no fglrx on my system.  and it is running much better than it did when i was previously using xgl as a session.  in someplaces, the mouse is the red wine color in other places it is the human cursor.  unfortunately, xgl crashes to gdm at the drop of a hat, though i think it is related to the shift key.

now for the crowning oddity.  xgl crashed to gdm.  that is where i am typing this in firefox.  gdm.  i am not logged in.  nautilus and a post it note were left over from the crash.  so i opened up a terminal with a right click, fired up firefox and am here to relate this very bizarre occurence.

alpha software can be amusing.

---

### Post by jimmygoon on 2006-07-26
> **cptnapalm said:**
> This is so strange i must share.

for most of today, i have been trying to get xgl to work.  please excuse the all lowercase as i am paranoid about this thing crashing.  anyhow, i missed the box, so i decided to reinstall xgl and compiz, but have it run all the time instead of just as a session.

so, i'm tearing my hair out, right and i'm getting nowhere.  xgl would run, but not compiz and it was nowhere near usable.  deciding one more howto could not hurt, i began following one dealing with mesa gl being used instead of ati's.

the howto said to uninstall the fglrx xserver and the linux restricted modules.  so i did.  after also setting my xorg.conf file to ati instead of fglrx.  also according to instructions. finally, it said reboot so down the rabbit hole i went.

now comes the oddness.  i sign in and xgl is running.  initially compiz is not but that gets fixed very quickly.  baffled, i look at my xorg.conf file.  indeed this is the ati driver.  there is no fglrx on my system.  and it is running much better than it did when i was previously using xgl as a session.  in someplaces, the mouse is the red wine color in other places it is the human cursor.  unfortunately, xgl crashes to gdm at the drop of a hat, though i think it is related to the shift key.

now for the crowning oddity.  xgl crashed to gdm.  that is where i am typing this in firefox.  gdm.  i am not logged in.  nautilus and a post it note were left over from the crash.  so i opened up a terminal with a right click, fired up firefox and am here to relate this very bizarre occurence.

alpha software can be amusing.

**ONLY TRY THIS IF YOU ARE 100% PREPARED FOR A CRASH**: [SIZE=2]Press Shift+Backspace

I'm not sure but I thought that this was a resolved bug... maybe not. I'm really not sure of any other reasons why it would be crashing... I've been using it since... golly I dunna when... a little pre-dapper at least and its only gotten (for the most part) more stable as I've gone.... but maybe thats a more unique circumstance... what guide did you use?
[/SIZE]

---

### Post by cptnapalm on 2006-07-26
which guide?  All of them, I think.

that it functions at all is completely weird.  the ati driver is only supposed to be 2d if memory serves, yet it is doing 3d, although not with any guarantee of stability.

btw, i'm still in gdm... is there a command line way to take a screen shot...

---

### Post by RAOF on 2006-07-26
> **jimmygoon said:**
> **ONLY TRY THIS IF YOU ARE 100% PREPARED FOR A CRASH**: [SIZE=2]Press Shift+Backspace

I'm not sure but I thought that this was a resolved bug... 
[/SIZE]
That's been resolved on my system for at least a month.

---

### Post by jimmygoon on 2006-07-26
> **cptnapalm said:**
> which guide?  All of them, I think.

that it functions at all is completely weird.  the ati driver is only supposed to be 2d if memory serves, yet it is doing 3d, although not with any guarantee of stability.

btw, i'm still in gdm... is there a command line way to take a screen shot...

gnome-screenshot ought to do it

---

### Post by cptnapalm on 2006-07-26
[http://ubuntuforums.org/gallery/showphoto.php?photo=3126&cat=508]("http://ubuntuforums.org/gallery/showphoto.php?photo=3126&cat=508")

This is the oddity, the freak of nature!

Behold!  GDM with Panels!

(In case you wonder about the Debian login screen, I just liked the picture.)

---

### Post by jimmygoon on 2006-07-26
> **cptnapalm said:**
> [http://ubuntuforums.org/gallery/showphoto.php?photo=3126&cat=508](http://ubuntuforums.org/gallery/showphoto.php?photo=3126&cat=508)

This is the oddity, the freak of nature!

Behold!  GDM with Panels!

(In case you wonder about the Debian login screen, I just liked the picture.)
Jeez, did you mess it up so bad that even failsafe gnome won't work??

---

