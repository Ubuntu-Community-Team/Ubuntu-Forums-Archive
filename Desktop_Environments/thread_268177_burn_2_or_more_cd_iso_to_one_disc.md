---
title: "burn 2 or more cd iso to one disc"
date: 2006-09-29
forum: Desktop Environments
---

### Post by m.musashi on 2006-09-29
Is there any software in ubuntu or the repositories that will let you take 2 or more ISO files and combine them into one? Essentially, I'd like to take two audio CDs and place them on one CD and have it play in a normal CD player.

Any ideas?

Thanks.

EDIT: I know I can make them into MP3 files and then burn them all but that isn't the same. Some CDs have one long song broken into tracks. When you rip MP3s you lose the continuity of the tracks and introduce pauses. I suppose you could then edit them all in audacity or something but that sounds like more work than it's worth.

---

### Post by jpkotta on 2006-09-29
You can mount the two iso files and copy the contents of each to another directory, then create a new iso from that.

To mount an iso:
```
sudo mount -o loop /path/to/image.iso /mount/directory
```

You can make .isos with mkisofs, but it's got a lot options and I can't remember how to use it.  You can easily make a music cd from a directory with Nautilus or any number of other programs.

---

### Post by artinla on 2006-09-29
With audio CD's, you don't have an ISO9660 filestructure like you do with data discs.

You will likely not be able to do what you want with them.

---

### Post by m.musashi on 2006-09-29
Thanks for the feedback. I don' want to cause an argument, but which is correct? Is the structure an issue? You can't just tack the data from one iso on to the end of another and have a new iso? Maybe I don't understand what an iso is, but I thought it was basically a data file created by copying the image off a disc.

@jpkotta - if I do as you suggest, will I end up with a single iso or will it keep the images in a directory structure?

---

### Post by jpkotta on 2006-09-30
In theory what you want to do is possible.  I don't burn music CDs so I'm not exactly sure how to do that part, but I'm pretty sure there is a program(s) that will take .wav files (or other sound files) and write them to a music CD.  Assuming you have the .wavs, it's probably just a matter of putting them all in one directory and running the program.  

abcde (and a number of others) will get you .wavs from a music CD.  I'm not sure how to get .wavs into a music CD, but it's possible.

---

### Post by jpkotta on 2006-09-30
OK, I turns out that I have to burn a music CD this weekend, so I searched for "burn music cd" in the forums and came up with this:

[http://ubuntuforums.org/showthread.php?t=257138](http://ubuntuforums.org/showthread.php?t=257138)
[http://ubuntuforums.org/showthread.php?t=260436](http://ubuntuforums.org/showthread.php?t=260436)

Also, [https://help.ubuntu.com/community/CdDvdBurning](https://help.ubuntu.com/community/CdDvdBurning)

I'm trying graveman.  I'll post back if it isn't up to it.  k3b always comes up in the list of CD buring apps, so that's probably a good bet.

---

### Post by jpkotta on 2006-09-30
I found gnomebaker to be best.  Graveman burned static, Goobox didn't seem to be able to burn (only rip), and k3b wanted to install half of KDE (it wanted to install kicker, the KDE panel; why the hell would it need that?).

---

### Post by m.musashi on 2006-09-30
Thanks for the tips. I have used k3b a few time for copying CDs. In windows I have also worked with ripping mp3 files and creating compilations. However, for this project I don't want to play with the .wav or mp3 files at all. I just want to take the disc image (what would normally be saved to the HD when doing a straight CD to CD copy with one drive) of 2 CDs and putting them on one disc. I have some CDs that are short and I want to two on one disc to save space. If I copy the two .iso files to the HD, can I stick one behind the other and have just ONE new .iso file that I can then burn back onto a single CD?

Thanks.

---

