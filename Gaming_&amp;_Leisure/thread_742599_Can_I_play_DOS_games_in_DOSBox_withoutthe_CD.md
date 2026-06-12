---
title: "Can I play DOS games in DOSBox withoutthe CD?"
date: 2008-04-01
forum: Gaming &amp; Leisure
---

### Post by eeefresh on 2008-04-01
I am sure this is a really easy problem to fix, but I have to say I am stumped.

I have installed DOSBox and have it set up to automount my game directory.  I downloaded some abandonware games that supposedly run great with DOSBox. However, when I try to run the exe file, it prompts me to enter the game CD, whcih I obviously don't have.  What can I do to play these games?

---

### Post by pieisgood4589 on 2008-04-01
> **eeefresh said:**
> I am sure this is a really easy problem to fix, but I have to say I am stumped.

I have installed DOSBox and have it set up to automount my game directory.  I downloaded some abandonware games that supposedly run great with DOSBox. However, when I try to run the exe file, it prompts me to enter the game CD, whcih I obviously don't have.  What can I do to play these games?

Hmmmm, I don't know, but usually (I'm not sure you can do this in DOS but) you could get an iso mounter, download the games ISO file, mount it, and play it...

---

### Post by FranMichaels on 2008-04-01
The answer is yes.
DOSBox has built in iso support, so if you back up your own CD with gnome cd/dvd or whatever, DOSBox can use it.

As for a rip, meaning you have the data on from the cd-rom, you can have dosbox mount that folder as a CD drive and treat it as such.

In dosbox type 

```
intro mount
```

and
```
intro cdrom
```

For syntax and examples.

Good luck, but it's worth mentioning you won't get as much help if you don't have the original game media. The one you downloaded could be a bad rip.

---

### Post by eeefresh on 2008-04-01
Well, I downloaded three games, but all were rar files, not iso files. I just unzipped them.  I know they work in Windows (all you have to do is drag the exe file onto the dosbox.exe file to get them to run in XP)

So in Ubuntu, do I need to first turn them into iso files before playing?

---

### Post by FranMichaels on 2008-04-02
If it works in DOSBox in windows, should be the same in Ubuntu.

Instead, right click the exe (that you dragged dropped in windows) and choose open with -> dosbox (you may have to choose custom command once, type dosbox)

That should do it!

P.S. You may have to remove the mount c  thing you added in your .dosboxrc or dosbox.conf. It will mount the folder automatically when you do the right click open with thing.

---

### Post by eeefresh on 2008-04-02
That worked, thanks!

---

