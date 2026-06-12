---
title: "Problem in booting windows after uninstalling ubuntu"
date: 2012-01-22
forum: Desktop Environments
---

### Post by psathiya1987 on 2012-01-22
Hi Guys,

I had installed ubuntu(not using wubi)alongside my windows.  I created a separate partition in my harddisk and installed ubuntu there. 

Now I have bought a new laptop and have installed ubuntu in it. I want to remove the ubuntu in my older machine. How can I remove ubuntu without losing my windows 7. 

Earlier before, When I wanted to uninstall ArchLinux, This was the step that I followed.
1) Log into windows
2) Format the partition using windows computer management tool

But after restarting my machine, I couldnot boot into windows. 
So I had to reinstall windows in my machine. I don't want to face a similar situation now when I am uninstalling ubuntu.

Please help me here and let me know the correct steps

I believe I pasted it in the wrong section. Forgive me if that's the case

---

### Post by abhijeet.1308 on 2012-01-22
i suggest you not directly format the partition were you install ubuntu 

i suggest you you follow following steps:

1) you login into ubuntu usig root account
2) and update grub

---

### Post by nipunshakya on 2012-01-22
Hi. I would suggest you to look at [here]("http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/")
 to solve your issue.

Goodluck.
Regards,WInuxUser

---

### Post by oldfred on 2012-01-22
WinuxUser link looks good.

You do not have to reinstall Windows, just the Windows boot loader to the MBR of the boot drive. You can do that before removing the Linux partiitons. Grub in the MBR loads additional grub files from the Linux partition and then you cannot boot as it cannot find the rest of its files.

If you do reinstall the Windows boot loader first while still booting Windows you may not need a repairCD, but it is good to have. Also getting to the repair screen in Windows with f8 can be difficult as the timing from grub2 menu entry to Windows loading is quick. You have to press f8 just as you press the Windows entry in grub. Some have to try many times.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

