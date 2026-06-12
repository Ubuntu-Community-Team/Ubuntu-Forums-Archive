---
title: "Mouse and keyboard stop working randomly"
date: 2008-12-05
forum: General Help
---

### Post by Wrathchild9 on 2008-12-05
I thought my PC freezes randomly and I searched for it on the forum, I found this: [http://ubuntuforums.org/showthread.php?t=832383&highlight=crash&page=20](http://ubuntuforums.org/showthread.php?t=832383&highlight=crash&page=20)

But I was suspicious, because I didn't have the same symptoms as they have, I don't have Dell stuff and wireless card either, I have PC, not laptop, the caps lock LED wasn't blinking when the Ubuntu was frozen so it didn't make sense.

I tried to log in via SSH from my another computer and it worked. I restarted the gdm, but the system still doesn't react to the mouse and the keyboard. If I push the caps lock/num lock/scroll lock button, the LED doesn't lit. 

I have Ubuntu 8.10, the kernel is 2.6.27-9-generic. Everything's up to date, the Ubuntu was installed yesterday.

The mouse and the keyboard have PS/2 connectors and they worked fine with the previous system (Ubuntu 6.06 LTS).

---

### Post by lukjad on 2008-12-05
Have your tried using another set of keyboard and mouse and seeing if the problem repeats itself?

---

### Post by Wrathchild9 on 2008-12-05
I've tried it with another mouse but the problem is the same. I think it's not a hardware issue.

//edit: they freeze always together!

---

### Post by lukjad on 2008-12-05
When they freeze, can you tell me what happens when you press Ctrl+Alt+F1?

Also, are you using a specific program when this happens?

---

### Post by Wrathchild9 on 2008-12-05
> **lukjad007 said:**
> When they freeze, can you tell me what happens when you press Ctrl+Alt+F1?

Also, are you using a specific program when this happens?

When I try to switch to tty1, absolutely nothing happens. There's no specific program, it can freeze also in the log on screen.

---

### Post by lukjad on 2008-12-05
Hmmm... is this a new or old PC? Also, are you hearing any loud or grinding sounds from the PC?

---

### Post by Wrathchild9 on 2008-12-05
> **lukjad007 said:**
> Hmmm... is this a new or old PC? Also, are you hearing any loud or grinding sounds from the PC?

It's an old PC and I don't hear nothing weird from it.

```
AsRock K7VT2 mainboard
AMD Athlon XP 2000+
GeForce MX440 64 MB
256 MB DDRAM
```
if it matters... I don't think it's a hardware issue, because it's started only after the installation of the Interpid.

---

### Post by lukjad on 2008-12-05
Well, two question. Does it stall in the live CD too?
And would you be willing to go back to Hardy?

---

### Post by Wrathchild9 on 2008-12-05
> **lukjad007 said:**
> Well, two question. Does it stall in the live CD too?
And would you be willing to go back to Hardy?

I never used Hardy and I used the Live CD just while I was installing the system. But no, it didn't freeze in the Live CD.

---

### Post by lukjad on 2008-12-05
You may wish to use Hardy Heron as it is the LTS (Long Term Stable) release. It has a few problems, but most are fixed.

---

### Post by Wrathchild9 on 2008-12-05
> **lukjad007 said:**
> You may wish to use Hardy Heron as it is the LTS (Long Term Stable) release. It has a few problems, but most are fixed.

Ok, thanks, I'm gonna try it.

---

### Post by lukjad on 2008-12-05
All right! Hope it works out well for you. :D

---

### Post by Wrathchild9 on 2008-12-05
Thanks. I hope so too :D

---

