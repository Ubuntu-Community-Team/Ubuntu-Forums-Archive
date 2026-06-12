---
title: "multi displays"
date: 2006-07-26
forum: Desktop Environments
---

### Post by silwerspawn on 2006-07-26
Hey everyone.

I'm in some trouble here. I have just installed Ubuntu on my laptop.
but I need to use multiple screens for presentation. 
my laptop is a HP ze4630us, and the shared grapic is a ATI Radeon Mobility U1 IGP320.

hope someone is able to help me...

---

### Post by Ziox on 2006-07-26
by having multipl screens do you mean that you need the two images on the screens to be the same?

or do you want to drag windows across monitors.

as for the first solution, i think cards that support mutliple outputs should "just work" if that doesn't and you want the second part (drag window...) then check out the link in my signature: HowTo, Dual Monitors

---

### Post by silwerspawn on 2006-07-26
i have tryed what you said.. it started eating 100% CPU for some reson, but when i return everything nothings wrong.
another thing, if i install kubuntu-desktop i can use the other screen.
but then i just need the my TV-out do you know anything about this?

---

### Post by Ziox on 2006-07-26
no, sorry. Unfortunately, i'm not sure how to get TV-out working. My card doesn't work either :(

---

### Post by silwerspawn on 2006-07-26
hmmm and i can't find anything about it...

---

### Post by Ziox on 2006-07-26
> **silwerspawn said:**
> hmmm and i can't find anything about it...

here i found one howto for nVidia: [http://www.ubuntuforums.org/showthread.php?t=98456&highlight=TV+output](http://www.ubuntuforums.org/showthread.php?t=98456&highlight=TV+output)

and one howto for Legacy ATI: [http://www.ubuntuforums.org/showthread.php?t=215763&highlight=TV+output](http://www.ubuntuforums.org/showthread.php?t=215763&highlight=TV+output)

I'm going to tryout the Legacy ATI one, and i'll post my result back :)

---

### Post by chalex on 2006-07-26
I had an Inspiron with an ATI Radeon Mobility 9000, and I spent days trying to get it to span the desktop to an external monitor.  

I tried both the Xorg Free ATI driver ("ati") and the proprietary ATI driver ("fglrx").  Both only allowed me to clone the notebook's display to the VGA output, neither allowed me to do anything else (like change resolutions independently or span the desktop or use the TV-out).  Good luck.

---

### Post by Ziox on 2006-07-26
> **chalex said:**
> I had an Inspiron with an ATI Radeon Mobility 9000, and I spent days trying to get it to span the desktop to an external monitor.  

I tried both the Xorg Free ATI driver ("ati") and the proprietary ATI driver ("fglrx").  Both only allowed me to clone the notebook's display to the VGA output, neither allowed me to do anything else (like change resolutions independently or span the desktop or use the TV-out).  Good luck.

have you tried MergeFB? its something in the ATI drivers that allow the desktop to span across two screens. If that doesn't work, have you check out my guide on dual monitors? (In signature)

---

