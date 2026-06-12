---
title: "Black screen with mouse pointer after switching users"
date: 2010-05-11
forum: Desktop Environments
---

### Post by mfearby on 2010-05-11
This problem has happened even before Lucid, but now I've come to realise that when logging off to then log on as a different user, and when you just get nothing but a black screen and a mouse pointer (seems to happen 50% of the time), widgets are really there but you can't see them.

Just now I decided to type my username/password assuming it was asking for either and then I noticed (judging by the different mouse points I'd get at various screen locations) that I was actually back to my desktop, but X couldn't display any of it since switching users and back again. I had a gnome-terminal open (evidenced by the I-beam cursor, so I typed "echo 11111 > ~/1.txt" and pressed enter. Then Ctrl-Alt-F1 to a terminal, and sure enough, the file is there.

Why does X do this when switching users, and is there some keystroke to force it to show things or to fix the problem? With Karmic, when this happened, X seemed to totally lock my computer, but with Lucid, I can actually Ctrl-Alt-F1 out of it and issue a safe shutdown, so that's an improvement. I'm using the normal level of visual effects and have an Ati Radeon HD 4670 with the proprietary driver offered.

---

### Post by De Baimbo on 2010-05-11
I am having exactly the same problem. 
Which is also my only problem, after that is solved, I think I'll keep 10.04 for two years.

---

### Post by De Baimbo on 2010-05-12
Solved!

It's a known bug: [https://bugs.launchpad.net/ubuntu/lucid/+source/xorg-server/+bug/546578](https://bugs.launchpad.net/ubuntu/lucid/+source/xorg-server/+bug/546578)


For the moment, the quick solution is to remove the package named **gnome-screensaver** (I tried and it actually works for me) but I'm sure they will fix it in short time and I'll be able to have my screensaver back.

---

### Post by mfearby on 2010-05-13
Thanks for finding that out. I should still be able to have monitor power management kick in, though? I'll try tonight, regardless.

---

### Post by Multi_User on 2010-05-13
Thanks very much for the info, I was wondering about this.

---

