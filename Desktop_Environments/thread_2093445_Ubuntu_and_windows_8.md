---
title: "Ubuntu and windows 8"
date: 2012-12-10
forum: Desktop Environments
---

### Post by harlie on 2012-12-10
Ok I bought a new desktop pc (HP) p6-2326 s I want to change OS to Ubuntu 12.04 But machine will not boot from DVD and that is what I have is a live DVD for 12.04. Can  anyone tell me how to get around this?
 
Harlie

---

### Post by d.atanasov on 2012-12-10
> **harlie said:**
> Ok I bought a new desktop pc (HP) p6-2326 s I want to change OS to Ubuntu 12.04 But machine will not boot from DVD and that is what I have is a live DVD for 12.04. Can  anyone tell me how to get around this?
 
Harlie
Hi, 

By does not boot DVD ou mean it can not or it wont ? If this property is missing on the machine then you have to get a new CD... If you have this feature to boot from DVD then I would suggest to find you boot options and play a bit with them. Most of the times you can find them in the BIOS manu just when the PC is loading you hit F2/F12 or some buttuns which should be written on the screen when the logo of the Brand is shown...

---

### Post by oldfred on 2012-12-10
If it is a new Windows 8 system you may do better with the 12.10 64 bit version. It has the newest grub2 v2.00. Although today I noticed in 12.04 grub2 1.99 had some updates to secure boot issues. Supposedly 12.04 will get grub2 2.00 with the next point release in Jan.

       Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
    
Other systems that have eventually worked.
       Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to [EasyBCD]("http://ubuntuforums.org/./EasyBCD.html"))
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)

---

### Post by harlie on 2012-12-10
> **d.atanasov said:**
> Hi, 

By does not boot DVD ou mean it can not or it wont ? If this property is missing on the machine then you have to get a new CD... If you have this feature to boot from DVD then I would suggest to find you boot options and play a bit with them. Most of the times you can find them in the BIOS manu just when the PC is loading you hit F2/F12 or some buttuns which should be written on the screen when the logo of the Brand is shown...

It is not an option in bios to make the pc boot from DVD drive I was in contact with tech support and the person I talked with on support chat didn't know how to make it boot from DVD drive. He said to hit esc while pc is booting but still no option appears there. Also same if bios is accesed from F10 during boot up.

---

### Post by Sef on 2012-12-10
Read Distrowatch's [Questions and Answers]("http://distrowatch.com/weekly.php?issue=20121126") for a solution.

---

### Post by grahammechanical on 2012-12-11
If it is impossible to boot the machine from a DVD drive, then how did the supplier put Windows on the machine? They needed to boot from a Windows install DVD to install Windows, did they not?

What messages do you see after the machine is switched on? You may see a message that says to press Del to enter Setup or something like that. You should also see a message telling you who made the BIOS program. You also should have received a motherboard guide that explains all about the BIOS settings and how to changed them.

Follow the links

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03509229&lang=en&cc=us&taskId=120&contentType=SupportFAQ&prodSeriesId=5295969&prodTypeId=12454]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03509229&lang=en&cc=us&taskId=120&contentType=SupportFAQ&prodSeriesId=5295969&prodTypeId=12454")

[http://h20000.www2.hp.com/bizsupport/TechSupport/ContactHP.jsp?lang=en&cc=us&prodSeriesId=5295969&prodTypeId=12454]("http://h20000.www2.hp.com/bizsupport/TechSupport/ContactHP.jsp?lang=en&cc=us&prodSeriesId=5295969&prodTypeId=12454")

[http://h20000.www2.hp.com/bizsupport/TechSupport/SupportTaskIndex.jsp?lang=en&cc=us&taskId=115&prodTypeId=12454&prodSeriesId=5295969]("http://h20000.www2.hp.com/bizsupport/TechSupport/SupportTaskIndex.jsp?lang=en&cc=us&taskId=115&prodTypeId=12454&prodSeriesId=5295969")

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=115&prodSeriesId=5295969&prodTypeId=12454&objectID=c03383166]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=115&prodSeriesId=5295969&prodTypeId=12454&objectID=c03383166")

> To open the Computer Setup Utility, turn on the computer and immediately press the Escape key repeatedly, about once every second, until the Startup menu opens. Then press F10 .

> **Boot Order** - Select this to change the order of the devices from which the computer boots.

> Use this screen to specify the order in which UEFI boot sources (such as an internal hard drive, USB hard drive, USB optical drive, or internal optical drive) or legacy boot sources (such as a network interface card, internal hard drive, USB optical drive, or internal optical drive) are checked for a bootable operating system image. UEFI boot sources always have precedence over legacy boot sources.
To change the boot order, use the up and down arrow keys to select the item you want to change. Then press the Enter key to drag the device to a new location. Press F10 to save the change or ESC to cancel the change and return to the previous menu.

There you are. It seems that an ordinary user like me knows more about HP machines than the HP support person who is paid to know what he is talking about.

Regards.

---

### Post by harlie on 2012-12-11
I think I have solved this issue. I have not yet installed ubuntu but I did get to run it from the disk. I didn't install it yet because I have the 32 bit disk  (I think). I will get the 64 bit version some how and then will go for the install.

Here are the steps I followed to get the pc to boot from the DVD drive:

1.  At start of boot up I hit F10 to get to HP setup screen.
2.  Then moved to right to SECURITY SCREEN. 
3.  Then down to SECURE BOOT CONFIGURATION.
4.  At the red screen F10 to accept.
5.  Then DISABLE SECURE BOOT and also DISABLE FAST BOOT.
       enable LEGACY SUPPORT.
6.  Back to left to FILE, highlight SAVE CHANGES AND EXIT. 
7.  Reboot and then the pc boots from the DVD drive.

I will post back if I get the 64 bit and get it installed.

Harlie

---

### Post by JKyleOKC on 2012-12-11
Many thanks for posting the details. It's a widespread problem!

---

### Post by harlie on 2012-12-12
I inadvertently left out one step in the instructions it is to disable the existing boot scheme with F5 before enabling legacy support.
Now have 12.10 installed and working. Hope this helps someone.

Harlie

---

