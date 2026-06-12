---
title: "uninstalling compiz in latest hardy breaks window manager ?"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by hatchetman82 on 2008-02-07
hi.

after installing the latest hardy alpha I've started tweaking it a bit. among the changes i've made was removing compiz (which removed 3-4 other packages the names of which i dont remember).

right after this change, application windows would appear without their titl bars, window borders, or anything - applications would just render into the top left corder of the screen, over whatever was there, and i couldn't move / resize / minimize them (no title bar, no birders).

the problem went away after i re-installed compiz (which brought back a few other packages with it - like compiz core and compiz gnome and maybe another one i cant remember right now).

why would removing compiz leave gnome / X server (probably the latter) in such a state ?
should this be considered a bug or is it simply impossible to run hardy without compiz ? (the computer is weak and old, i don't want any graphical effects slowing it down).

any ideas on how i can remove compiz without the side effects ?

Thanks in advance for any assistance.

---

### Post by overdrank on 2008-02-07
> **hatchetman82 said:**
> hi.

after installing the latest hardy alpha I've started tweaking it a bit. among the changes i've made was removing compiz (which removed 3-4 other packages the names of which i dont remember).

right after this change, application windows would appear without their titl bars, window borders, or anything - applications would just render into the top left corder of the screen, over whatever was there, and i couldn't move / resize / minimize them (no title bar, no birders).

the problem went away after i re-installed compiz (which brought back a few other packages with it - like compiz core and compiz gnome and maybe another one i cant remember right now).

why would removing compiz leave gnome / X server (probably the latter) in such a state ?
should this be considered a bug or is it simply impossible to run hardy without compiz ? (the computer is weak and old, i don't want any graphical effects slowing it down).

any ideas on how i can remove compiz without the side effects ?

Thanks in advance for any assistance.
HI and I suggest just selecting none under system, preference, appearance, visual effects. This way you will have no effects and will not have to uninstall anything.

---

### Post by hatchetman82 on 2008-02-08
thank you for the reply.
however, the effects were disabled in the menu you mentioned from the get-go.
i was just thinking that if im never going to use compiz anyway, i might as well remove it, and then when i removed it things went bad.

---

### Post by overdrank on 2008-02-08
> **hatchetman82 said:**
> thank you for the reply.
however, the effects were disabled in the menu you mentioned from the get-go.
i was just thinking that if im never going to use compiz anyway, i might as well remove it, and then when i removed it things went bad.

HI and I just removed compiz core from my system and it also removed CF plugins and emerald for a total of 5. Restarted X and  It has had no effect on my system. What is the model of the graphics card?

---

### Post by hatchetman82 on 2008-02-09
intel i810 (old machine - p3 1GHz) onboard graphics controller.

---

### Post by overdrank on 2008-02-09
> **hatchetman82 said:**
> intel i810 (old machine - p3 1GHz) onboard graphics controller.

Ok are you using xfce, KDE, gnome?

---

### Post by hatchetman82 on 2008-02-11
gnome, plain vanilla, straight out of the install CD (didnt even change the desktop).
i've just recreated the problem, by marking compiz-core for complete removal and rebooting afterwards.
i've also made a video capture of what happens after i redmove compiz-core and reboot (its attached, made with recordmydesktop available through synaptic, but i couldnt play it either on ubuntu or windows. im hoping you'll have better luck).

to solve it, all i need to do is re-install compiz-core (just that, nothing else) and everything is back to normal.

since the screencap isnt up to forum file size standards (its 2 MB) here's a rapidshare link :
[http://rapidshare.com/files/90970881/out2.ogg.html](http://rapidshare.com/files/90970881/out2.ogg.html)
(as i said, it doesnt work for me, i dont know why, you might get lucky).

if you haver any more ideas about how to further diagnose the problem (or get a better working screen cap ...) ill be happy to cooperate (its a spare PC im playing with, so i dont mind abusing it)

---

