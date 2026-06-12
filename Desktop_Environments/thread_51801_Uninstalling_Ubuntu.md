---
title: "Uninstalling Ubuntu"
date: 2005-07-25
forum: Desktop Environments
---

### Post by lostinzim on 2005-07-25
Hi,
I have been having problems getting ubuntu to do what i want it to so have decided to go back to Mister Gates and install XP.  Before I do any untold damage is there any specific way of removing ubuntu?  I would appreciate any help.

Thanks

---

### Post by majikstreet on 2005-07-25
Listen to the people below.

---

### Post by charlieg on 2005-07-25
Oh ye of 2 posts, what is it you are having trouble doing?  Perhaps if you ask we can help!  Then you won't have to go back to XP.

Plus there's nothing like a few weeks of using Linux to make you appreciate it properly. ;)

---

### Post by jeremy on 2005-07-25
charlieg is right, if at all possible just hang on in there just a bit longer, post your problems, and, if we can, we'll help you sort them out.

---

### Post by Takis on 2005-07-25
Well if you're going to do it, might as well leave on a good note. Presumably you have a single partition on your computer with Ubuntu (i.e. no XP yet). Put in the XP cd, boot up the installer and when it gets to the bit where you select where to install Windows, delete the 'unknown partition' and then create an NTFS one. You'll lose all data you had with Ubuntu.

Alternatively, if you're dual-booting, get a Windows 98 bootdisk, load that up and type```
fdisk /mbr
```When you reboot, grub will be gone. Log into Windows, right-click on My Computer and go to Manage, go down to 'Disk Management', select the 'unknown partition' and format it to NTFS. You'll have it as another logical drive.

Buuuut, like the others said, couldn't you at least let us try and help you before switching back to Windows?

---

### Post by spudley on 2005-07-25
Although I'm not the OP, one of my reasons for not making a total switch to Ubuntu is the lack(?) of an app to replace my Palm Desktop program... 

This is a heavily used program on my notebook (dedicated to XP) and not something I can go without ( I use all aspects of it - calendar, todo, memos, notepads, & voice memos) .  

What are people using as a Linux alternative? Evolution looks promising (no memos or voice memos though)  Or should I take a stab at running Wine and then the Palm Desktop program under that?

---

### Post by graigsmith on 2005-07-26
[QUOTE=spudley]Although I'm not the OP, one of my reasons for not making a total switch to Ubuntu is the lack(?) of an app to replace my Palm Desktop program... 

This is a heavily used program on my notebook (dedicated to XP) and not something I can go without ( I use all aspects of it - calendar, todo, memos, notepads, & voice memos) .  

What are people using as a Linux alternative? Evolution looks promising (no memos or voice memos though)  Or should I take a stab at running Wine and then the Palm Desktop program under that?[/QUOTE]
 i searched for palm desktop on google. and found jpilot.

[http://www.jpilot.org/](http://www.jpilot.org/)

jpilot is in the universe repositories.  if you need help enabling the universe repositories, just ask.  i would try jpilot at least before formatting and going back to windows.

---

