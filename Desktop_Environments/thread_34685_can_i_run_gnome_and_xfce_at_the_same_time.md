---
title: "can i run gnome and xfce at the same time??"
date: 2005-05-16
forum: Desktop Environments
---

### Post by jerome bettis on 2005-05-16
i like to use xfce when i'm doing programming work, there's less distractions and i can get more done.  but i love gnome because it's sweet for using for every day stuff.  what i'm wondering is if i can have both running side by side on the same X server.

i've been doing this by running gentoo on a seperate partition, chrooting into it and starting xfce.  but gentoo has really turned me off in the past few days (portage sucks!!  :roll:  ) so i've wiped it out and am happily back to an ubuntu only machine. O:) 

i've switched to a console and typed startxfce4 and it won't go because the x server is locked.  but simply deleting the /tmp/lockfile allowed me to start it :grin: i'm able to switch back and forth between the two with ctrl alt f7 / f8 but one thing isn't right.  

if i start firefox (or any other app) in gnome, it shows up in xfce.  so how can i fix that?  or is there a right way to start them both?  what about starting two copies of gdm? ](*,)

thanks

---

### Post by 23meg on 2005-05-16
i have two suggestions, but i'm not sure either will work the way you want, but anyway: did you try Applications / System Tools / New Login? also try installing xnest and check out the manpage, it's in the repositories.

---

### Post by jerome bettis on 2005-05-16
[QUOTE=23meg]Applications / System Tools / New Login[/QUOTE]

YES

THANK YOU :grin:  :grin:  :grin:  :grin:  :grin:  :grin: 

i didn't even know that was there but it did the trick perfectly

thanks!!!!

---

### Post by poofyhairguy on 2005-05-16
Why run both and make things slow? I just make XFCE look like Gnome. Its easy, get into XFCE and run "gnome-panel." If you want the Gnome backround and the adding of CDs and USB drives to the desktop, run "nautilus" and "gnome-volume-manager" Try it.

(PS if you want to kill the XFCE panel, use this command: "killall xfce4-panel")

---

### Post by 23meg on 2005-05-16
you're welcome :)

do you feel a great performance loss when both are running?

---

### Post by bored2k on 2005-05-16
[QUOTE=jerome bettis]YES

THANK YOU :grin:  :grin:  :grin:  :grin:  :grin:  :grin: 

i didn't even know that was there but it did the trick perfectly

thanks!!!![/QUOTE]
 Question: if you do your programming on xfce because of the speed ? howcome you leave gnome open ?

---

### Post by jerome bettis on 2005-05-16
> Why run both and make things slow? I just make XFCE look like Gnome. Its easy, get into XFCE and run "gnome-panel." If you want the Gnome backround and the adding of CDs and USB drives to the desktop, run "nautilus" and "gnome-volume-manager" Try it.

(PS if you want to kill the XFCE panel, use this command: "killall xfce4-panel")

hrmm that's interesting.  but my gnome panel is full of distractions and xfce is strictly business.  i'll try it and see what happens.

[QUOTE=23meg]you're welcome :)

do you feel a great performance loss when both are running?[/QUOTE]

none what so ever.  the linux kernel really does a good job on this machine.  for a while i thought my swap wasn't being used, because free would always say my ram was almost full and my swap was empty.  i had to open about 13 copies of the gimp and about 6 open office windows and only then did the swap get used.

>  Question: if you do your programming on xfce because of the speed ? howcome you leave gnome open ?

i do it in there because it looks less distracting.  i have all kinds of eye candy in gnome and i tend to piss around like a child in there.  i leave gnome open so i can be downloading / be on instant messenger etc etc and my boss only sees emacs running in xfce :cool:

---

### Post by bored2k on 2005-05-16
[QUOTE=jerome bettis]i do it in there because it looks less distracting.  i have all kinds of eye candy in gnome and i tend to piss around like a child in there.  i leave gnome open so i can be downloading / be on instant messenger etc etc and my boss only sees emacs running in xfce :cool:[/QUOTE]

Lol you sound just like me when I have a project or something. But in my case, I just log on Windows. It's so boring I have nothing to do other than get to work :\

---

### Post by jerome bettis on 2005-05-16
yeah but i can't function in windows because i just make fun of it the whole time.  after i installed it on here it wasn't more than 3 minutes and explorer crashed for no reason.   i'm not joking either .. it was a good laugh.  and i love it when those cute little ballons pop up in the corner at random times to tell me something very important.  "lets take a tour of windows xp"  no how about lets shut the hell up and leave me alone! :click:  

plus i use the command line for programming instead of an ide now.  have you used msdos lately?  haha try it it's funny.  i had to use it once in the windows lab when i was demonstrating this java app.  i kept typing gnu commands out of habit instead.  
$ls ... "blah blah not found"  ohhh right it's dir over here  ... 20 seconds later ... $ls damnit!! ;lsafkjda;ljhfg alt+f4 alt+f4 alt+f4 alt+f4

---

