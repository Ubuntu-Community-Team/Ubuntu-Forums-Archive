---
title: "GRUB 1.99 Fedora help"
date: 2015-06-23
forum: Fedora/RedHat and derivatives
---

### Post by gaklein2007 on 2015-06-23
I am new to LINUX and have never used it before at all. Currently, I am using a computer (and need to use this computer) that someone else used some years ago. When this person was using it, he partitioned the hard drive and the computer currently has Windows 7 and Fedora as the operating systems where Fedora is the default. What I need to do is now change the default back to Windows 7 but the problem is that I cannot get into Fedora since it is password protected and since the person that made it hasn't been here for a few years, no one knows the password. So, I need to change the default OS back to Windows 7 from Fedora without actually getting into Fedora. I believe there should be a way through either the BIOS screen or through the GRUB 1.99 menu, but I do not know the commands to change the default back to Windows 7. Does anyone know how I can use the GRUB 1.99 menu to do this? All the research I have done is using a downloaded program but through the Linux OS which I do not have access too.

---

### Post by slickymaster on 2015-06-23
*Moved to the ***Fedora/RedHat and derivatives*** sub-forum*

---

### Post by VMC on 2015-06-23
Is the Fedora partition encrypted ? If not, you might try changing Fedora's partition: "/etc/default/grub", section  GRUB_DEFAULT=? to the windows partition. If that doesn't work you need to change "grub.cfg" directly.

---

### Post by gaklein2007 on 2015-06-23
Where would I type in those commands? In the GRUB menu there are two command options, would that be under the Minimal BASH-like command?

---

### Post by ajgreeny on 2015-06-23
Do you have a Windows install disk or failing that, the recovery disks that you are recommended to make when Windows is first booted?
If you have either of those you can probably use either of them to restore a windows bootloader, thus ignoring grub completely.  The suggestions of VMC will possibly not work, unfortunately, as to make those edits he is suggesting take effect you have to run commands in the Linux OS where those files are situated, and that will be difficult.

If it were Ubuntu you could boot into recovery mode from the grub menu, and that may also be possible in Fedora, from where you could either make the changes suggested or restore a password that you want and can remember, but unfortunately I do not know Fedora at all, so I'm not at all sure about that as a course of action.

I believe you can still also restore a simple bootloader system that works for Windows 7 (and maybe Windows 8?) by booting to a Ubuntu live OS, DVD or USB, and in that run ```
sudo apt-get install lilo
```
Ignore the warning that will probably appear, and then 
```
sudo lilo -M  /dev/sda mbr
```assuming the machine boots to sda normally.

Then you should be able to boot directly into Windows again if all goes well, and from there you can deal with the useless Fedora partitions.

Can you still boot into windows from the grub menu?  If so there may be ways to restore the Windows bootloader files from the running OS, but I do not have Windows any more and I do not know if that is possible.

---

### Post by gaklein2007 on 2015-06-23
I have no problem getting into Windows, but it is the fact that I can't seem to do anything from that side. In Windows, I've played around with the bcdedit function in command window but it tells me "accessed denied" even though I am an admin on the Windows side. I also do not have a windows install disk or recovery disk. Basically, I'm trying to find a way to make Windows the default but the only way it seems at this point is to basically do a clean install making sure Windows is the default

---

### Post by QDR06VV9 on 2015-07-14
> **gaklein2007 said:**
> I am new to LINUX and have never used it before at all. Currently, I am using a computer (and need to use this computer) that someone else used some years ago. When this person was using it, he partitioned the hard drive and the computer currently has Windows 7 and Fedora as the operating systems where Fedora is the default. What I need to do is now change the default back to Windows 7 but the problem is that I cannot get into Fedora since it is password protected and since the person that made it hasn't been here for a few years, no one knows the password. So, I need to change the default OS back to Windows 7 from Fedora without actually getting into Fedora. I believe there should be a way through either the BIOS screen or through the GRUB 1.99 menu, but I do not know the commands to change the default back to Windows 7. Does anyone know how I can use the GRUB 1.99 menu to do this? All the research I have done is using a downloaded program but through the Linux OS which I do not have access too.
This should help, you will have to read to understand. [https://support.microsoft.com/en-us/kb/927392](https://support.microsoft.com/en-us/kb/927392)
I'm not really sure if boot-repair would change those options in grub?
Regards
Crap I did not notice this thread is 3 weeks old!

---

