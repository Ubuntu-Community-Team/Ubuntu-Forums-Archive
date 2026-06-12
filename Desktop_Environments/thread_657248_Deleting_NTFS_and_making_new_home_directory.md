---
title: "Deleting NTFS and making new /home directory?"
date: 2008-01-03
forum: Desktop Environments
---

### Post by irv on 2008-01-03
This past week I made some changes on my laptop. I was duel booting with Ubuntu 7.10 and WinXP. I have only one program I use in Windows so I installed Vistualbox and setup WinXP. I then installed the program I use and everything works great. Now what I want to do is use gparted to delete the NTSF partition and set it up as my /home directory and move all my files from my home to it. I am not sure if I can do this or not? Does anyone know of a “how-to”, or can someone give me some help on this one?
I am afraid if I setup a new /home mount point, I won't be able to access the old mount point. I could back up all my stuff in my /home to my USB drive and then restore all the files to the new /home directory.
Any suggestions or help would be well received. I like to move with caution when it come to changing a hard drive. 
Thank Irv

---

### Post by taurus on 2008-01-03
Maybe this guide will give you a hint on how to do that.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by irv on 2008-01-03
This link is useful but I have gparted on a boot CD which does the same thing. I still have some question on this. Do I need to delete the /home I have now in order to setup a new mount point for the new /home? If anyone has tried this before, have you had success?

---

### Post by carrett on 2008-01-03
You wouldn't have to delete it. However if you're making a new /home partition, you probably want to move all the stuff currently on /home over to it anyway, right? If you do that, you'll get some extra free space on / plus a less-likely-to-be-destroyed /home.

Good luck!

---

