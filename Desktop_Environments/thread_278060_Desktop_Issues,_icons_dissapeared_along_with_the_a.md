---
title: "Desktop Issues, icons dissapeared along with the ability to right click on desktop"
date: 2006-10-15
forum: Desktop Environments
---

### Post by Justin Holt on 2006-10-15
I have the problem where my desktop has disapeared as stated in the title, i do not see my icons anymore, nor can i right click to create folders and such.  The only thing i have done really to affect this is to use the little force quit button on my desktop, my stupidity led me to believe that it might allow me to stop my cd drive from being busy and allow me to eject.  
Anyone know how to reverse it? :confused:

---

### Post by Dr. Nick on 2006-10-15
do you have beryl installed? That causes this sometimes, If you are not sure the answer is probably "no".

try pushing alt+f2 and then running **nautilus**, or maybe just using ctrl+alt+backspace to log off and then log back on; If that fails a restart should fix it

---

### Post by Justin Holt on 2006-10-15
yeah...im not a complete n00b to linux...i have beryl and all that good flash stuff (i <3 my pre-used GeForce 6600 GT :-D) but yeah, just restarting by doing the alt+ctrl+bksp fixed it...thanks

---

### Post by Dr. Nick on 2006-10-16
> **Justin Holt said:**
> yeah...im not a complete n00b to linux...i have beryl and all that good flash stuff (i <3 my pre-used GeForce 6600 GT :-D) but yeah, just restarting by doing the alt+ctrl+bksp fixed it...thanks

OK, It may have been beryl then, I know thier were some instances where I booted with beryl and lost my desktop and/or all my panels. After installing some of the updates that problem has seemed to go away.

---

### Post by Steve S. on 2006-11-19
> **Dr. Nick said:**
> OK, It may have been beryl then, I know thier were some instances where I booted with beryl and lost my desktop and/or all my panels. After installing some of the updates that problem has seemed to go away.

This is probably a dead thread, but I just wanted to add: I am not running Beryl, did the force quit thing, didn't know it was related, but had EXACTLY the same problem.  I rebooted, all's well.

It has to be due to the force quit, from what I can see.  Just FYI.

Oh, and thanks for starting this thread...can't believe you had EXACTLY that same issue.  Good post.

---

### Post by Dr. Nick on 2006-11-19
It may have been that the force quit killed nautilus which is used to draw your desktop, not sure how it affects panels though. Glad a restart fixed it all, I dont think the force quit can really ever do permanent damage.

---

### Post by Steve S. on 2006-11-20
> **Dr. Nick said:**
> It may have been that the force quit killed nautilus which is used to draw your desktop, not sure how it affects panels though. Glad a restart fixed it all, I dont think the force quit can really ever do permanent damage.

...that makes sense since when I rebooted, Nautilus opened up a file browser as well, one I hadn't left open, along with the icons.

I'm glad too.:D

---

### Post by jhenager on 2006-11-24
I am having the same problem. A reboot and restart didn't help. Tried running nautilus and still can't create new desktop icons.
I am running Beryl too. This happened before, and it seems to be associated with plugging in USB devices.

---

### Post by cmlewin on 2007-09-10
i'm not on beryl and this problem just starting for me. please help!!!

---

### Post by dondad on 2007-09-15
Same problem here. I got a notification that there was a nautilus error, then no desktop icons and no right click. I am running compiz, but changing to metacity and gtk didn't help, nor did restarting x or rebooting. If I look at places>desktop, all of the icons are there and work. Fiesty on a Dell xps410n.

I played around for awhile and got nowhere, so I reinstalled nautilus through synaptic and that fixed it.

---

### Post by NoVista on 2007-09-30
I ran into this on two seperate upgrades to Gutsy.
And it is what both times made me give up because re-installing Nautilis and various other "things i would try", could never get my desktop or my right click menu back.

Good thing I always keep image files of all my partitions.

---

### Post by LashSilence83 on 2008-05-05
Did anyone ever find a fix for this problem? I've looked all over and nobody seems to have any answer... :(

---

### Post by ehblack on 2008-05-11
[SOLVED] I was having the problem for the last two hours, reboot didn't help, neither any other advice in this thread. But, I found the culprit: it was hanged nautilus. I killed the process and then CTRL+ALT+Backspace. [SOLVED]

---

