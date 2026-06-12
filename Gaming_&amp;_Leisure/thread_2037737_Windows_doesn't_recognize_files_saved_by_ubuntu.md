---
title: "Windows doesn't recognize files saved by ubuntu"
date: 2012-08-05
forum: Gaming &amp; Leisure
---

### Post by itsmeemikee on 2012-08-05
My windows installation doesn't see any files I saved from ubuntu, why is that? it often overwrites the files too! D:

For example, I have this second drive which I use just to store music, videos, games, etc.
and I ripped the music off a CD onto the drive, then I booted into windows so I could sync it onto my iPhone but the files didn't appear, then I just forgot about that and downloaded a program blah blah blah then returned to ubuntu and looked at the directory where I saved the music, and the music file became an .exe with the icon of the program I downloaded but preserving it's song name.:confused:

Please help me with this, i'd be ever so grateful:)

---

### Post by OM55 on 2012-08-05
Hello itsmeemikee,

Two possible reasons come to mind right away:

1. Notice that Linux in general allows additional characters in its folder and file names, which Windows does not. For example some of the punctuation marks like ':'. 
So if you (or the Ubuntu program you used on the file) accidentally change a file name, or any of the folder names in its path, to include one of those characters, it might either be visible by inaccessible to Windows, or completely invisible to Windows.

2. When you reboot to change between Windows and Ubuntu, if you leave the previous system in Hibernate mode (supposedly to save time on the next boot), it may mess up the common files that will be changed while working in the other operating system. The reason would be that while hibernating is saving the current memory state to be retrieved later on. The main assumption is that the disk is NOT shared with anyone else and will not change until the next time the system is brought out of hibernation.
If you boot into Ubuntu while Windows is hibernating, make changes and reboot to Windows - you may loos some of those changes in Windows.

Check those two things and try to recreate the same problem again. If the same problem still happens while no hibernation or non-Windows file names are involved, please describe step by step what you are doing + the result, and we'll try to help!

---

### Post by itsmeemikee on 2012-08-05
Well... that was simple :D. I mean, after I rebooted to windows(after I shut it down "properly") it ran chkdsk; which I have been trying to avoid, and moved the files into "found.xxx"

---

### Post by OM55 on 2012-08-05
If the problem is solved, please mark this thread as 'Solved'...

---

