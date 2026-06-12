---
title: "[SOLVED] Windows doesn't boot"
date: 2008-12-21
forum: General Help
---

### Post by caio on 2008-12-21
Hello guys
my problem is this: I have windows installed in my pc and installed ubuntu under wubi. After that, I changed the boot loader of windows to directly boot ubuntu.
Now what happens is that: the bootloader of windows starts ubuntu and what appears is the grub menu. In grub menu, if I choose ubuntu, it works fine. BUT if I try to boot windows, it doesn't work!
I've tried supergrub to fix windows' bootloader, but didn't work.
My menu.lst for windows:
title Windows
root (hd0,0)
makeactive
savedefault
chainloader +1

the error I get is: 
Filesystem type is ntfs, partition type 0x7
error occurred while savedefault

My problem is that I don't know how to edit BOOT.ini of windows, before booting.

---

### Post by pytheas22 on 2008-12-21
I'm not positive, but it's my understanding that if you installed Ubuntu via wubi, it's the *Windows* boot loader that decides which operating system to boot to, not grub.  You can only use grub to boot to Windows if Windows and Ubuntu are installed on different partitions--but under wubi, they share the same partition.

When you get to the Windows boot menu--the first one that you see after BIOS--don't you have an option there to choose between either Windows or Ubuntu?  If you choose Windows there, it should boot directly to Windows.  if you choose Ubuntu, it should bring you to grub, then boot Ubuntu.  Is this not how things are for you?

If you have no option to boot Windows from the Windows boot menu, or that option doesn't work, you'll probably need to edit your boot.ini file from within Ubuntu.  To do that, boot to Ubuntu, open a file browser and navigate to '/host'.  This is equivalent to C:\ in Windows.  From there, you'll have to find the boot.ini file--I think this is at C:\Windows\boot.ini under XP, but I'm not sure.

Be sure to back up the current boot.ini file first just so that you don't make things worse than they already are.

I don't know much about what you should actually change inside boot.ini--if you post the contents of that file here, maybe someone can make a suggestion--but there's plenty of information available on Microsoft's site and through Google.

---

### Post by caio on 2008-12-22
Thanks for replying pytheas22...

The windows boot menu doesn't show up because I changed the time delay that it appears to zero and changed the default OS to boot. The windows boot manager directly boot ubuntu and then grub shows up. At least, changing the delay would help me (I think)... I'll try to change like you said :)

---

### Post by caio on 2008-12-22
Solved!

I turned on my pc and pressed F8, the windows safe-mode selection screen appeared, and the last option of the list was something like "return to the menu with the OS options"... I chose this option and the list with OS showed up. Now I'm able to change boot.ini inside windows!

---

### Post by thiagoms on 2008-12-23
Hello. I'm kind of having the same problem here. I changed the default system to Ubuntu and deactivated the time delay. Because of this, I see the Windows boot menu for a split second and then it boots Ubuntu. I tried to press F8, but it didn't work - the boot screen doesn't appear long enough to receive a command. To make things worse, I'm using Vista, and I couldn't find the boot.ini (I've even heard that Vista DOESN'T have a boot.ini ...).

Also, sorry for any English mistakes - I'm not from a English-speaking country and my English is a bit rusty :).

---

### Post by caljohnsmith on 2008-12-23
> **thiagoms said:**
> Hello. I'm kind of having the same problem here. I changed the default system to Ubuntu and deactivated the time delay. Because of this, I see the Windows boot menu for a split second and then it boots Ubuntu. I tried to press F8, but it didn't work - the boot screen doesn't appear long enough to receive a command. To make things worse, I'm using Vista, and I couldn't find the boot.ini (I've even heard that Vista DOESN'T have a boot.ini ...).

Also, sorry for any English mistakes - I'm not from a English-speaking country and my English is a bit rusty :).
Do you have your Windows Vista Install CD? If so, how about booting that, and simply do a "Vista Repair". Depending on your setup, that will probably be enough to fix the boot menu problem, but if not, let me know and we can try to manually fix it with some commands. Also, if you don't have a Vista Install CD, you can instead download and use a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how that goes. :)

---

### Post by thiagoms on 2008-12-28
Hi, sorry for the delay ...

Finally fixed it. I used a Vista Install CD. First I tried to run the startup repair, but it said everything was ok. I had to open a command-line window and write

[FONT="Courier New"]bcdedit.exe /timeout=10[/FONT]

"bcdedit.exe" is the 'substitute' of boot.ini in Windows Vista, and it was set up with "[FONT="Courier New"]timeout=0[/FONT]", which is the line that caused all the problem :(. Anyway, thanks!

---

