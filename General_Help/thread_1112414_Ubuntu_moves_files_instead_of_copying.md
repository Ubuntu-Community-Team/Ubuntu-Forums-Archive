---
title: "Ubuntu moves files instead of copying"
date: 2009-03-31
forum: General Help
---

### Post by tomstealthports on 2009-03-31
Hello.  

My problem is not really that big a deal, but I have four partitions- windows xp, ubuntu, an ntfs data partition and a swap partition.  When I navigate to /media/data and then drag a file onto the desktop or whatever, it copies fine as you'd expect.

However, I have created a shortcut to /media/data/photos on the desktop which, when opened, tells me its path is ~/desktop/photos.  Hmm.

When I open this shorcut (to /media/data/photos) from the desktop and drag and drop the file to, say, ubuntu's desktop, it moves it instead of copying.

I expect this is a peculiarity of the way linux handles files, or something I've screwed up, or maybe both.

So my question is, how do I get it to do what I expect i.e. copy files when I drag them onto another partition, and move them when I drag and drop on the same partition?

---

### Post by coffeecat on 2009-03-31
Well, this is very interesting. I've got a NTFS data partition which is mounted via fstab and an icon appears on my desktop. I've just created a folder in the data partition called "Test". I've created a link on my desktop and when I open that up it says, as with your system, that the path is /home/myusername/Desktop/Link to Test. So far so much the same. And that is what I would expect. The link is in ~/Desktop after all.

However, when I drag and drop a file into the link it gets copied, not moved.

Hmmm :?

How did you create the link? I did it the simple way. After creating 'Test' in the Data partition, I right-clicked on Test and chose 'Make Link' which gave me a link 'Link to Test' in the data partition. I then simply dragged and dropped that onto my desktop. (Which, incidentally, copied it, not moved it. :))

**Edit:** I've just renamed the desktop link from 'Link to Test' to just 'Test'. It didn't make any difference, not that I thought it would. I still get a copy, not a move.

---

### Post by tomstealthports on 2009-03-31
Hmm.  I just did what you did, make link, put it on the desktop.  This computer is using ntfs-config to mount the disks though.  Perhaps if I just do it manually with fstab, it won't behave in this peculiar way?

Oh,  when I drag and drop ONTO the link, it gets copied.  The other way round, though, where i open the link, see the files and drag one onto desktop, it gets moved.  Does this happen to you?

The link got copied, I think, because you didn't open it from desktop, possibly.

Unless it is because of ntfs-config.

---

### Post by coffeecat on 2009-03-31
> **tomstealthports said:**
> Unless it is because of ntfs-config.

I wonder. I don't know; I have no experience of ntfs-config, seeing as NTFS 'just works' in Ubuntu. :)

If it's any help, here is my fstab line:

```
/dev/sdb1    /media/Data    ntfs-3g        defaults    0 0
```Really straightforward. In fact that's the sort of line that the Hardy/Intrepid installer sets up if you create a mountpoint for an NTFS partition in the installer - that's if you select 'Manual' at the partitioning stage.

---

### Post by tomstealthports on 2009-03-31
Yeah, I can use fstab.  I used ntfs-config because this computer is for someone who is useless with computers and I thought ntfs-config would make it easier for him.  I shall try it without ntfs-config later on.

Oh, did you get the same thing happen when opening the link from desktop and dragging a file to your desktop?  Does it copy or move?

Cheers for the help, anyway.

---

### Post by coffeecat on 2009-03-31
> **tomstealthports said:**
> Oh, did you get the same thing happen when opening the link from desktop and dragging a file to your desktop?  Does it copy or move?

Curiouser and curiouser. Desktop > Desktop link folder = copy. Desktop link folder > Desktop = move. :-k

I think I'll go to bed now. :(

:wink:

---

### Post by tomstealthports on 2009-03-31
You get the same as me?  WOO-HOO!

I am also going to bed.  See you tommorrow, perhaps?

---

### Post by coffeecat on 2009-04-01
> **tomstealthports said:**
> You get the same as me?  WOO-HOO!

:lol:

This is all very interesting. My Desktop 1 and laptop are set up as Windows/Linux multiboots, although I rarely boot into Windows and never use it for anything productive. On both those machines I have separate NTFS data partitions and keep all my personal files on the data partition in 'Documents', 'Photos', etc folders - usual sort of thing. Then in Linux, I set up symlinks in my home folder, not on the desktop, so that I have link folders called 'Documents' and so on. All quite straightforward, and I prefer this to a shared /home partition. I must admit though that I haven't noticed this sometimes-I'll-copy-sometimes-I'll-move behaviour, perhaps because I've never had to copy/move a file from ~/Documents (say) to home before. I'll keep a closer eye on this in future.

Anyway, I have a second desktop with an all-Linux multiboot (unsullied by Windows :p), with a similar setup except that the shared data partition is Ext3. I'll try some experiments in that and see if I get the same weird behaviour. It may be a day or two before I have chance to do so, but I'll post back.

---

### Post by tomstealthports on 2009-04-01
Good luck coffeecat, maybe you'll find a solution.

Maybe some more fancy links are in order, instead of the standard ones? Just an idea.

"unsullied by Windows"...Hey, windows ALWAYS copies and pastes when it's meant to!  Sure, there are a few other "minor" faults with windows, like when it needs to reboot every 5 minutes, the bluescreens three times a day, the fact that a removable drive is always "in use", even when it bloody well isn't, and you need to use 75% of your RAM just to try and keep the system free from viruses and trojans.  

All Os's have their faults...

---

### Post by tomstealthports on 2009-04-13
No progress, then?  

Shameless bump.

Alright, does anyone know how to have an option to copy, move etc. in ubuntu like in kde?  Without installing kde?

Is the answer, drag and drop using middle click?  How can I make it always do this with a normal drag and drop?

---

