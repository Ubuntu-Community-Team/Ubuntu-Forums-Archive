---
title: "Preferred app + defragment"
date: 2006-05-14
forum: Desktop Environments
---

### Post by mevan on 2006-05-14
Hi!

I just wanted to know how can I change the preferred application for some file types. I go under "open with" in file's properties, I see some applications with radio buttons listed there but I cannot move the dot from the initial one.
Any ideas??

Another issue is that I have a FAT32 partition, remnant from my old Win system, full of files, which I now use for copying audio and video, compressing, uncompressing, etc.. 
It is not ext3, it is FAT32. Does it get fragmented?? 
And if it does, what can I do??? (except from moving away all files and copying them back again. This is a not a solution for a modern OS - and I don't have the necessary space for doing so!!!!)

Thanx!

---

### Post by louis_nichols on 2006-05-14
[QUOTE=mevan]This is a not a solution for a modern OS 
Thanx![/QUOTE]
I'm assuming you're talking about windows here... Because Linux has no fault in whatever happens or doesn't happen with a FAT32 filesystem (completely microsoft contraption), except having devised a way to read and write to it. I agree: having to defrag one way or another is a crappy thing. Ext2 and ext3 partitions, Linux's native ones, don't need this kind of process, although it can be done.

As for defragging fat32 under Linux, I'm afraid to my knowledge there isn't a tool that does that.

---

### Post by mevan on 2006-05-17
No no no no... You don't understand me... By the term Modern OS I mean Linux... 
And of course I do not blame the system, if a FAT drive I use to swap files in and out constantly, gets fragmented.
By "no solution" I mean solutions of the type "move all files out, then move them back in".
Indeed, by doing so the drive will defragment, but as I said this in not a solution (I am stating this option because someone calling himself computer "guru" proposed that to me!!!!!)

All I want to know is whether some utility exists, to perform the FAT defrag under linux...

How about the preferred app problem??? Anybody???

---

### Post by louis_nichols on 2006-05-17
That was a little irony I was making there. :) Because you seem to blame Linux because FAT gets fragmented and can't be defragmented from under Linux, whereas all that the Linux community has done was figuring out a way to read and write to it and has nothing to do with FAT's bad quality as a file system. Indeed, the only known way to defragment fat filesystems in Linux is the one that guru suggested. There is no other way. Linux users don't need to think about fragmentation, because the native filesystem doesn't get fragmented.

Anyhow, the defragmentation tool that windows uses does pretty much the same thing: moves files around on the hard disk. LOL, it even requires that you keep like 15% of the hard disk free in order to be able to do that.

Sorry I missed your other question. Depending on the file browser you use, how it usully goes is you right click, choose properties and you'll have an "open with" tab where you can choose the default.

---

### Post by mevan on 2006-05-19
hehe.. I agree, FAT sucks, but since almost everyone in my environment uses it (for time being) I have to go with the flow...

The problem with prefered apps, is that the system would not allow me to change anything!!! I find the "open with" tab, see that it lists some apps there, but I cannot select any of them! ](*,) I am using Nautilus. 
Take a look at my attachment, it is from mp3 files. By default Totem is selected, but I cannot change it! 
Apart from the Nautilus option dialog, is there a configuration file where such changes are stored?

Thanx for the time!

---

### Post by louis_nichols on 2006-05-19
[QUOTE=mevan]hehe.. I agree, FAT sucks, but since almost everyone in my environment uses it (for time being) I have to go with the flow...

The problem with prefered apps, is that the system would not allow me to change anything!!! I find the "open with" tab, see that it lists some apps there, but I cannot select any of them! ](*,) I am using Nautilus. 
Take a look at my attachment, it is from mp3 files. By default Totem is selected, but I cannot change it! 
Apart from the Nautilus option dialog, is there a configuration file where such changes are stored?

Thanx for the time![/QUOTE]

well, the options aren't greyed out so you should be able to select them. Do you try to click specifically in the option box? Selecting the app name doesn't do it.

as for the FAT... here's a quick idea: search for livecd's that can do that. UBCD would be a good place to start. Of course, it would require a reboot, but not a dual boot system.

---

### Post by mevan on 2006-05-20
Thanx for the info!

Options are not grayed out.. 
I click the option (another program), it becomes blue (selected) but the dot remains in "totem":(  !

---

### Post by Ramses de Norre on 2006-05-20
Did you click on the button instead the line with the application, you really need to click inside the little circle to get the dot there.

---

### Post by mevan on 2006-05-23
been away for a while...

Of course I clicked in the dot!!! I clicked everywhere!!! And I 've been messing with operating systems (MS that is) for quite a while, I know where to click, trust me;)

thanx for the effort, nevertheless:)

---

