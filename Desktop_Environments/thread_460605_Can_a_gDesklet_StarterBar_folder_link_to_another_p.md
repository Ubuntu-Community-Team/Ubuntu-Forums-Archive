---
title: "Can a gDesklet StarterBar folder link to another partition?"
date: 2007-05-31
forum: Desktop Environments
---

### Post by eeefresh on 2007-05-31
I am using the gDesklet StarterBar launcher on my desktop, and by default it creates a link to your Home folder.  However, I would rather it link to a folder on another partition.  Is there a way to do this?

---

### Post by eeefresh on 2007-06-01
Bump

---

### Post by Kevanx on 2007-06-25
Hi, I was pulling my hair out trying to find a solution to this. Google had the answer.
For some reason, the gdesklet StarterBar launcher app doesn't quite recognize how folder type launchers work, so you need to specify nautilus (or a similar file browser) to open it.

It's still a mystery to me how the default home folder that the StarterBar provides works, but whatever.

This should solve your issues.

1. Create a new launcher, but make it an APPLICATION launcher, not a FILE launcher.
2. Name it.
3. Point it to the folder by using this:
```
nautilus ../../your/directory
```
By default nautilus seeks out the user directory i.e. ./home/kevan/
That's where the ../../ comes in.
4. Choose an icon.

If you did this on the desktop, then drag it onto the StarterBar, and if you created it through the gDesklet, then it should appear and be fully functional.

Voila! I hope this works, and that you haven't given up hope!

---

### Post by eeefresh on 2007-08-14
I was just cruising through some old posts when I found this one.  Glad I look back at them once in a while.  Thanks!

---

### Post by henjenagin on 2007-11-02
Thanks Kevanx. Worked for me. My default home folder launcher stopped working. The icon just started bouncing...and bouncing...sigh...and bouncing whenever I clicked it. I couldn't understand it. It worked in the beginning. I think my problem might have came from a couple of automatic updates, but I could be wrong. I've only been bouncing around linux since June. Now I just specify the nautilus application and point it to my home folder and choose my own icon just like you said. How about making the background bar transparent? Right now I have it the same color as my desktop, so you can't tell the difference, but I change that all the time.

---

