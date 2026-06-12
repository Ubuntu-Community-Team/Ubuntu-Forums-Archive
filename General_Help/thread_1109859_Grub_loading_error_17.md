---
title: "Grub loading error 17"
date: 2009-03-29
forum: General Help
---

### Post by coryalantaylor on 2009-03-29
I was running xp64 and then I tried to install ubuntu on a separate drive. I restart my computer and I can't boot to windows anymore. I get the "Grub error 17". But if I take the hard disk out and open it on a different computer it still has all my windows program files in it, and only one partition.

Oh, and I'm new this is my first post on the forums.

---

### Post by balaknair on 2009-03-29
Go into your BIOS, turn off quick boot - this will force your computer to reload all the hardware settings and re-read the MBR. Make sure the disk with the MBR is selected as the first startup device in BIOS boot options.

---

### Post by coryalantaylor on 2009-03-29
What is an MBR?

---

### Post by coryalantaylor on 2009-03-29
I turned off quick boot and I got error 21. :(

---

### Post by balaknair on 2009-03-29
MBR= Master Boot Record
It's basically the first bytes on your hard drive that tell the computer BIOS that the hard drive is bootable and where the OS boot files are. That's what brings up the OS boot menu when you start the computer.

In your case, I think it ought to be the drive with Windows on it.

---

### Post by coryalantaylor on 2009-03-29
Right now the only drive in there is the windows drive, but it won't boot to the windows drive, it tries to load grub. I did change it so that quick boot is disabled. And now it gives me error 21.

---

### Post by balaknair on 2009-03-29
Can you see the drives in BIOS?

---

### Post by coryalantaylor on 2009-03-29
Yes I have only one drive in right now, but I can see it in the bios.

---

### Post by balaknair on 2009-03-29
Error 21 means that it can't find the hard drive. GRUB is on the Linux disk(which you removed), so that's why you get the error.

---

### Post by coryalantaylor on 2009-03-29
Hmm... how do I make it try to boot from the Windows drive?

---

### Post by balaknair on 2009-03-29
If you have a Windows CD handy, you can boot into it--> Recovery Console--> Use the command ***fixmbr*** to create a new Windows MBR which will then be able to boot Windows.
1 Boot Windows CD
2 Choose &#8220;Repair&#8221;
3 Enter installation number(usually it'll be 1) and admin password if asked
4 At the command prompt type &#8220;fixmbr&#8221;, then confirm. Windows will overwrite the dual boot info in the MBR that Ubuntu put there.
5 Reboot

---

### Post by coryalantaylor on 2009-03-29
Ok, I'll try that now.

*Wishes Ubuntu forums had a chat feature*

---

### Post by balaknair on 2009-03-29
> **coryalantaylor said:**
> 
*wishes ubuntu forums had a chat feature*


:p

---

### Post by coryalantaylor on 2009-03-29
Thanks for your help! It worked yay! Now I can go back to rendering my animation.

*starts to explore the forum for Blender related stuff*

---

### Post by balaknair on 2009-03-29
Glad to know your problem's fixed.

Have fun.

---

