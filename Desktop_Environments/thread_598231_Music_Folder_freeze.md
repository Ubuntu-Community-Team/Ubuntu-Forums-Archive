---
title: "Music Folder freeze"
date: 2007-10-31
forum: Desktop Environments
---

### Post by impf0s on 2007-10-31
Hello!

I have a problem with my music folders!
Everytime I'm in a folder that contains music, it freezes for unknown reason, and then I have to force quit.

I made a screenshot:
[http://www.mbuchmayr.at/storage/fail.png](http://www.mbuchmayr.at/storage/fail.png)

Maybe someone can tell me how to solve this...?

---

### Post by taurus on 2007-10-31
What filesystem is disk1 and how do you mount it?

---

### Post by impf0s on 2007-10-31
It is NTFS and I mounted it with NTFS Configuration Tool, **BUT** it's also on my lin partition!

---

### Post by Jaiz on 2007-11-02
I have the same problem on every kind of partition you can think of... so I guess this is not a problem of partitions ( NTFS, FAT32, ext3, etc... )

Btw, I'm on gutsy

---

### Post by joseantmm on 2007-11-02
Same problem here with Gutsy. Any solutions by now? Thanks,

---

### Post by Mobbringer on 2007-11-02
I'm having this happen problem on Gutsy with the music folders freezing with both my ext3 internal HDD and my ext3 external HDD. 
Dunno if it's related, but since I've been using Gutsy, it won't let me copy music to my external. Rhythmnbox says there's some technical error and if I try to click and drag/copy+paste/etc, it starts.. But then stops and keeps taking longer and eventually says it'll take like 3 days to transfer 1 file.

---

### Post by TeaSwigger on 2007-11-03
Hello, 

To everyone experiencing a problem of freezing, slowness or other odd behavior when browsing audio files in Nautilus, I would suggest a first step in troubleshooting would be to determine if this is due to a problem with the "audio preview" feature. It would cause such problems.

First check in Nautilus' options if audio preview is enabled. If it is enabled, disable the feature and return to verify if the behavior is still present. If it is working perfectly now with audio preview disabled, it won't hurt anything to simply leave it off; but if you want to correct the error start by determining if you're able to play those media files properly. I'm sorry I don't know what Nautilus uses (I mostly use Kubuntu) to preview the audio files with, but at least you'll know where the trouble lies.

---

### Post by TeaSwigger on 2007-11-03
> **Mobbringer said:**
> I'm having this happen problem on Gutsy with the music folders freezing with both my ext3 internal HDD and my ext3 external HDD. 
Dunno if it's related, but since I've been using Gutsy, it won't let me copy music to my external. Rhythmnbox says there's some technical error and if I try to click and drag/copy+paste/etc, it starts.. But then stops and keeps taking longer and eventually says it'll take like 3 days to transfer 1 file.

It sounds unrelated; in your case it sounds to me as if Rhythmbox is trying to keep track of the files for its music library while you're moving them. That could cause problems on any system but possibly more pronounced with an external drive due to the amount of data transfer that could add to the more limited external connection. Perhaps specify folders for Ryhthmbox's library which are not being disturbed much, perhaps preferably on the internal drive only - you'd have to see if that solves it as I don't use Rhythmbox myself. And/or disable any of its auto features while moving the files about.

---

### Post by Jaiz on 2007-11-03
It worked ! I guess that was the problem, thx a lot. But what is that audio preview doing exactly ? when you select the song it starts playing or something like that ?

---

### Post by impf0s on 2007-11-05
It works! And i won't miss that feature ;)

---

### Post by TeaSwigger on 2007-11-05
> **Jaiz said:**
> It worked ! I guess that was the problem, thx a lot. But what is that audio preview doing exactly ? when you select the song it starts playing or something like that ?

You're welcome, glad I could help :) Yeah it's supposed to play a few seconds of it when you mouse over it. Guess when it's not working right it hangs Nautilus up.

> **impf0s said:**
> It works! And i won't miss that feature ;)

hehe :popcorn:

---

