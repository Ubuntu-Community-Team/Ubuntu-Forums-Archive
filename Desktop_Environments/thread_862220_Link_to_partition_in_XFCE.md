---
title: "Link to partition in XFCE?"
date: 2008-07-17
forum: Desktop Environments
---

### Post by squashpup on 2008-07-17
I have a partition on my hard drive that's not recognized by Thunar.  Not a big deal, as I've added it to fstab and it works perfectly. Thing is, I'd like to be able to open it from the desktop without opening thunar, clicking on file system, and drilling down through /media/storage.  I just can't figure out how to do it.  

Anyone know how I can put a link either on my desktop or on a toolbar where I can click and Thunar will open it in a window?  Thanks.

---

### Post by mirchichamu on 2008-07-17
> **squashpup said:**
> I have a partition on my hard drive that's not recognized by Thunar.  Not a big deal, as I've added it to fstab and it works perfectly. Thing is, I'd like to be able to open it from the desktop without opening thunar, clicking on file system, and drilling down through /media/storage.  I just can't figure out how to do it.  

Anyone know how I can put a link either on my desktop or on a toolbar where I can click and Thunar will open it in a window?  Thanks.

Please refer to this thread.
[http://ubuntuforums.org/showthread.php?t=860391](http://ubuntuforums.org/showthread.php?t=860391)

---

### Post by mali2297 on 2008-07-17
There are at least two ways to accomplish this:

1. Create a launcher which executes the command *thunar /media/storage*. You can find a menu to create launchers by right-clicking on an existing desktop icon.

2. Place a symbolic link in the desktop directory. From the terminal:
```

ln -s /media/storage ~/Desktop/Storage

```

You might need to restart Xfce to see the changes.

---

### Post by squashpup on 2008-07-18
Mirch - I've already done everything in that thread except reboot the computer.  I'm copying a disc now and will try that in a second.  If it's that obvious, I will shoot either the computer or myself.

Martin - 

I tried both of those and neither worked.  Making the symbolic link put an icon on my desktop that did nothing when clicked.  Making the launcher "thunar /media/desktop" did nothing, either.  Surprising, because I was sure that would work.  I double checked and made sure that /media/storage was mounted, and it was.

I tried the obvious, too...opening /media and simply dragging the folder onto the desktop.  That seemed to work, until I found that dropping things into that folder did NOT also deposit them on my storage partition.  It had simply made a copy of the folder and put it on my desktop.

Anyway, more suggestions are always welcome.  To clarify, /media/storage is already in fstab and mounting perfectly upon boot.  I'll be rebooting in a second to see if it will show up and will post back here.

---

### Post by sisco311 on 2008-07-18
linux is case sensitive: desktop != Desktop

create a new folder on the ~/Desktop/Storage and add
this line to the fstab:
> /media/storage /home/YOURUSERNAME/Desktop/Storage bind defaults,bind 0 0

---

### Post by squashpup on 2008-07-21
OK...got this one.

Made a shell script called storage.sh (I have a folder in my home directory where I keep scripts, so I put it there).  It says simply:

thunar /media/storage

Made it executable (chmod a+x)

Put a new launcher on my taskbar: /home/username/scripts/storage.sh

Now, when I click it, Thunar opens my storage partition pretty as you please.

Thanks for the help guys.

---

### Post by j1mc on 2008-07-21
If I'm understanding you correctly, you can also just navigate to the folder that you want to use from thunar, and then click and drag the folder icon into the left pane underneath the "file system" icon in thunar.  That will create a shortcut to that folder/partition.

I hope this helps!

---

