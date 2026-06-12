---
title: "How I boot to a liveCD in a XP PC?"
date: 2009-04-21
forum: General Help
---

### Post by Arenamar on 2009-04-21
I want to to try Ubuntu in my PC but I cannot boot into the liveCD.  Windows always appears.

---

### Post by fballem on 2009-04-21
This may be an obvious question, but is the CD in the drive when the computer first boots? If it is, you may be given a prompt that says, "To boot from CD, press any key ...". Press a key and the Live CD should boot.

If this isn't the problem, then it may be that your machine is not set to boot from a CD. If you restart your machine, the first thing that appears is a screen for the bios. The instant this screen appears, press the key to enter bios settings. It is often the delete key, although I have also seen F12 used.

This should open up the bios settings. Once there, go through the menus until you see something like 'boot order'. The instructions for most bios are pretty clear. Usually you use an arrow key to find the item on the menu, then press enter to review or change the settings.

When you find the boot order setting, enter and make sure that the CD drive is listed before the hard disk. When you have this, follow the instructions to save the settings. The system will then reboot, and assuming that the CD is in the drive, you should be able to boot from the CD.

Hope this helps,

---

### Post by zwygart on 2009-04-21
Personnaly I always use temporary boot option, since I don't have access to the BIOS of all the computers. 

This is made by pressing the correct key during boot of the BIOS. But this change from one machine to the other. One key is for the BIOS settings if you want to permanently start on CD/USB, if it is inserted, the other is a temporary boot device.

So the possible keys I have seen is : ESC, ENTER, F1, F8, F9, F12. It may also be another key. Normally it is written on the BIOS screen on boot up, but this pass fast.

Good Luck

---

### Post by Arenamar on 2009-04-21
Thanks. It was the boot order. Now I know that Ubuntu don t work on mi PC. I use the liveCD , I can heard the Ubuntu music, then a blank screen with a cursor.

---

### Post by Promethalus on 2009-05-07
you might wanna give Xubuntu a shot, bit sleaker

---

