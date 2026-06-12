---
title: "Beryl/XGL Problem"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by SYNeR on 2007-05-22
Hi all,

First time poster (and new Ubuntu user - after being annoyed at the maintenance required for Gentoo ;) ) here.
I've got Xgl and Beryl working.  However, my problem is that I can't run beryl-manager & emerald --replace from a terminal (or add it in Sessions under Gnome as a startup program).  If I do either, then I get a black screen with a cursor.

However, I am able to get beryl-manager & emerald working by running them as root (sudo/su).  Now I'm taking a guess that this is a permissions problem - can anyone provide any insight as to what it might be?

My second problem is that upon booting up (or restarting X with Ctrl+Alt+BackSpace), when I first attempt to login to Gnome with XGL through GDM, I get an error saying that the session crashed due to an error.  I am then returned to the GDM screen, where I seem to be able to login fine on second & subsequent attempts.  I'm not even sure if this is some sort of bug/problem, or maybe if I'm trying to log in to Gnome/Xgl before it's fully/properly loaded?

Other than these small problems, Beryl (and Ubuntu in general) seem to run great (the only thing that didn't work out of the box was sound - which I've still yet to work on).

Cheers

---

### Post by Brackish_zygote on 2007-05-22
I can't help you with your beryl problem, but I some advice for your sound problem. Try going to the terminal and type "alsamixer" and unmute (hit "M") everything but the farthest right option IEC598. 

I, too, am new to Ubuntu (about a week), but that is how I solved my sound problem. I am pretty sure Ubuntu's default sound is digital out which is what causes alot of problems. So, if you have analogue sound this will hopefully fix that.

---

