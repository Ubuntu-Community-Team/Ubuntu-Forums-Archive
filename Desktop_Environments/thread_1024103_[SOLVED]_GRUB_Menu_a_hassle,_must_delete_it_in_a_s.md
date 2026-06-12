---
title: "[SOLVED] GRUB Menu a hassle, must delete it in a safe manner from Vista?"
date: 2008-12-28
forum: Desktop Environments
---

### Post by wrichtmyer on 2008-12-28
Hello,

As an Ubuntu user for almost 6 months, I had occured a problem. So I booted up Vista, and deleted the Ubuntu partition via Vista the "unclean" way.

Now, when I boot up, the Grub Menu loads up (even though I don't want it there) and says Error 22. I know it doesn't load, but I want to get rid of it, so that I can just get to Vista directly.

Once somehow avoiding the Grub Menu, I was able to boot up Vista using the System Restore function.

Now here I am. I have a 8.04 Ubuntu live disk, however I wish to solve most of my problems from the Vista half. If I do switch, then I'm afraid I won't be able to get back to Vista.

I've tried the Vista repair disk numerous times, and at one point I accidentally changed some System32 files, but now they're fixed due to System Restore.

How to get rid of the Grub Menu...

Help would be greatly appreciated, thanks!

---

### Post by keithld on 2008-12-28
Try here and see if this helps: [MBRfix](http://www.sysint.no/Nedlasting/MbrFix.htm)

---

### Post by wrichtmyer on 2008-12-28
To be frank, I'm completely new at this. Any commands I could use specifically?

I'm not very good at editing via CMD/Regedits, and might accidently delete something.

Plus, I don't think it will help with deleting a grub menu. GRUB menus are completely different than partition editors.

---

### Post by caljohnsmith on 2008-12-28
To restore a Windows MBR to your Vista drive so you can boot Vista again, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
And then you should be able to boot Vista again. How about giving that a shot and let me know how it goes, or if you run into problems.

---

### Post by keithld on 2008-12-28
If you have the VISTA CD you should be able to just "Boot" from that and look for Repair My Computer or something like that and then choose Vista as what you want to repair...

I found this tho I have XP so I've never tried it...

1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Bootrec.exe /FixMbr, and then press ENTER.

That's it. Now when you reboot your PC, Vista will load automatically... You can now safely boot using your Ubuntu desktop CD, to use the built in Gnome Partition Manager to remove your Ubuntu partition!

---

### Post by wrichtmyer on 2008-12-28
Caljohnsmith - I have tried your way of doing so, however the term *'lilo'* isn't recognized as a command. As it says, "Command not found".

And for you keithld - It didn't work. I tried fixing it via the Vista Repair Disk (I don't have a Vista install disk) and the attempts to fix it were futile.

Any suggestions?:confused:

---

### Post by caljohnsmith on 2008-12-28
Do you have internet access while using the Live CD? If so, how about doing:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Let me know if that works or if you run into problems.

---

### Post by wrichtmyer on 2008-12-29
Thanks for the help. I have tried the commands as listed, and they have worked, I think. I do have internet access, and this is what it has given me:

```
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.

```

I shall reboot to see if it works. If it does, I shall confirm.

If it does not, I shall reply in the morning.

Thanks very much!

---

### Post by wrichtmyer on 2008-12-29
It has worked. Thank you very much for your help! :D

You may close the topic as you wish.

---

### Post by caljohnsmith on 2008-12-29
Glad to hear that did the trick; by the way, you can mark the thread as "solved" by clicking on the "thread tools" link at the top of the thread and selecting "mark as solved" or whichever is the exact option. Cheers and have fun with Vista. :)

---

