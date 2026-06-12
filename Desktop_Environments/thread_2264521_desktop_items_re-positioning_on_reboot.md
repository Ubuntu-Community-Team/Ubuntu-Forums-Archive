---
title: "desktop items re-positioning on reboot"
date: 2015-02-08
forum: Desktop Environments
---

### Post by raysa on 2015-02-08
My desktop items always used to stay where I put them, but just lately they have been re-setting themselves to top left when I re-boot the computer.  How can I go back to having them stay in the position I move them to? Xubuntu 14.4.01 and XCFE 4.

Thanks, Ray

---

### Post by ajgreeny on 2015-02-08
Place all your icons (assuming this is what you want to stay put) where you want them, then try logging out and back in again.
If they all stay where they should be, run command ```
sudo chattr +i /home/*username*/.config/xfce4/desktop/icons-screen*
```Those icons-screen files, of which you may have several, will all now be immutable and not able to be changed even by root until the immutable attribute is removed.

For a cleaner setup you could remove all those icons-screen* files first, then set your icons where you want them, and then run the **sudo chattr** command.

Now, should any icons move themselves, (mine never do now), or be moved accidentally by yourself, you can just hit F5 to refresh the desktop and as if by magic, all icons move back to where they should be.

---

### Post by raysa on 2015-02-08
Thank you, but before I do that can I ask: will I still be able to add or remove items (folder or file icons) or will the entire desktop be frozen?  I like to have my icons positioned where I want them, but also I sometimes add new ones and remove old ones, and I wouldn't want to lose being able to do that easily.

I'm puzzled that the Icons stay put if I just log out and log back on, but they get repositioned top left when I close down and re-start.  And this is new - I've had Xubuntu 14.04 since it came out and until a few days ago the icons always stayed where I had put them. I haven't installed any new software recently, although I do usually do updates when Software Updater invites me to.  

Has a recent update changed the desktop icon behaviour?  And if so, why?  Why would a developer/updater decide that I should no longer have the icons staying where I want them?

Thanks again,
Ray

---

### Post by ajgreeny on 2015-02-08
You can certainly add new icons, or files themselves, to the desktop even if the icons-screen* file or files are immutable, but if you shutdown the system may, I think, make a new file with the added items on it and the old one will no longer be used, and I am not certain that you will be able to delete the launch icons from the desktop; not sure about that so I'll try it and report back..

EDIT:
OK, I've just tried this.
[LIST=1]
[*]You can remove icons from the desktop without a problem, but then a logout and login again seems to confuse the system and the icons move all over the place, presumably because not all the items expected are  present.  F5 still puts the remainder back where they should be.
[*]Restoring the removed item from trash meant that the icons were all correctly placed after a logout and login.
[*]No new icons-screen* file was made, though I just logged out, I did not reboot; a reboot may be different.
[/LIST]

---

### Post by raysa on 2015-02-08
Thank you very much for your time on this.  If I have a play, could I later remove the immutable condition by starting the command line "sudo chattr -i "?

---

### Post by ajgreeny on 2015-02-08
Yes, you certainly can.

You can then either remove the icons-screen* file or files and allow the system to make a new one when you shift icons around or you can leave it and allow it to change automatically.
It appears to be only the **appname.desktop** files (launchers) on the desktop that are listed in the icons.screen* files, not any actual files you put on the desktop, but that needs to be tested a bit more before I'm certain of that.

---

### Post by raysa on 2015-02-08
Oh, the items I have on my desktop are not .desktop files - at the moment there are five folders, a .pdf file and a .txt file, and they are all listed in the icons.screen file.
I've now made that file immutable as you suggest, so I'll see if the icons stay put when I power down and start up again.

Well, partial success ... my items stayed put on re-boot, but then I added a new file and re-positioned it alongside the others. On re-boot the original icons stayed put but the new one jumped back to top left. Making the icons.screen file immutable after every change would be a bit tiresome.

---

### Post by ajgreeny on 2015-02-09
You could always do it with a simple script and use a keyboard shortcut to run that script, but I agree it's a bit of a workaround, not a real answer.

Interesting find of yours, however, which I didn't see on the few times that I added a file to the desktop; it only happened to me when I removed an icon listed in the icons-screen file.

---

