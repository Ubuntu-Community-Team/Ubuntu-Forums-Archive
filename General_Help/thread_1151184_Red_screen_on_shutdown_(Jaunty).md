---
title: "Red screen on shutdown (Jaunty)"
date: 2009-05-06
forum: General Help
---

### Post by The Judderman on 2009-05-06
Dear all,

I don't know if this is a bug that I need to report or if it is the same for everyone. When I shutdown Jaunty I don't get the usual Ubuntu and disappearing line, but a plain blank red screen.

It feels like there is an error on shutdown that I can't work out. I did have the nasty beep as well that has been noticed by a few people that was resolved by blacklisting pcspkr.

Does any body have any ideas? Should I try and sort this out?

Thanks,

The Judderman

---

### Post by BslBryan on 2009-05-06
Hello, The Judderman. :-)

Apparently this was also a minor problem some people were having on the Jaunty RC.

From what I've gathered, it comes every so often, but not terribly much, and goes away for a pretty long while.  

Also, it seems that it's not an actual problem with the stability of the OS, and so your computer is not in jeopardy.  

From looking at a few bug reports, I'd like to suggest that maybe it's xorg failing at shutdown (ending later than usual, and therefore failing).  

Anyway, hope I helped!  If there's any kind of workaround that I can think of, or find, I'll let you know.

Best to you. :-)

---

### Post by The Judderman on 2009-05-07
Thanks for the reply.  I have looked at the bug reports and can't see anyway round it, so any thoughts would be gratefully received!!! I look forward to the hearing a little more! Where should I go and look? I've googled and looked at Launchpad, but with no idea what to do!

Cheers,
The Judderman

---

### Post by The Judderman on 2009-05-12
Anybody have any ideas?!?

Thanks,

The Judderman

---

### Post by blastbar on 2009-05-31
i get exactly the same thing but it always happens, no idea what it is or how 2 stop it =[

---

### Post by The Judderman on 2009-06-03
Does anyone have any workarounds on this, or any ideas of where to look so that I can see what is going on?

I can't even work out how to get the error messages so that I can see what is going wrong, as it is part of the shutdown process. shutdown -v doesn't help at all, or piping the error log to a log file...

Help anyone?

---

### Post by The Judderman on 2009-06-25
To anyone interested, this issues was resolved automatically today by upgrading to the latest kernel. It was obviously a Kernel issue and is now solved!!!

Still not sure why the problem occurred in the first place, but hey!!!

Cheers,

The Judderman

---

### Post by del_diablo on 2009-06-25
For me it involed removing apm and getting in ATI's drivers. To fix the red screen that is.

---

### Post by wesswei on 2009-06-30
Apparently this issue is not just simply solved by updating the kernel as is my case (2.6.28-13). I was actually having trouble with wireless internet, but the 9.04 live CD worked perfectly with wireless, so I did a fresh install. Anyway in addition to wireless problems, I also had the problem of the boot/shut down screen not appearing after upgrade. This loss of boot screen happened on my last upgrade from gutsy to hardy, repaired it, then again when upgraded from hardy to jaunty.

A fresh install was in order, but now the red screen appears on shut down. It doesn't appear to affect shutdown processes as the computer does poweroff, but it certainly makes for an ugly and awkward exit. It also happened when using the LiveCD, but only once. Maybe this is a graphic card or X issue.

I don't really want ATI's drivers since Ubuntu's native work with compiz now.

I'm assuming APM is only for laptops? Going to google in the meanwhile and remove if necessary, seeing if that helps.

---

### Post by The Judderman on 2009-07-01
Just out of interest, what are the APM's to remove or not to remove?!? 

Incidentally, I've never found upgrading straight forward and so always do a clean install from now on... And it does help! (the initial red screen problem was on a clean install as you have now found!)

---

