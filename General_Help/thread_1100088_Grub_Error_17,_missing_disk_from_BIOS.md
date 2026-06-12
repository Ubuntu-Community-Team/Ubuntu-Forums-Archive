---
title: "Grub Error 17, missing disk from BIOS"
date: 2009-03-18
forum: General Help
---

### Post by HarryZhe on 2009-03-18
I had a look around to get help with this,
but didn't find an example with similar conditions to mine.

I have 2 HDDs, master 320gb and slave 80gb
1.Installed windows on master,
2.(physically)Installed 80gb slave
3.Both appeared in BIOS
4.Installed ubuntu on slave
5.Booted ubuntu
6.Shut down computer
7.Booted windows
8.Shut down windows
9.Booted up, Grub error 17
10.Entered BIOS, basic setup, master 320gb is listed, slave 80gb is not

I'm not really sure what I should do. Running live CD now.

---

### Post by ruel- on 2009-03-18
I usually got error 17 and 16 from my older CPU, but what I do is just turn it off a little bit, then start again.. it works for me..

---

### Post by HarryZhe on 2009-03-18
Okay, just tried this

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

but i got this

```
grub> root(hd0,0)

Error 27: Unrecognized command

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> root (hd1,1)

Error 22: No such partition

grub> 
```

In case it isn't painfully obvious, this is my first time using Ubuntu.

---

### Post by 123456789123456789123456 on 2009-03-18
if bios does not read the disk
that would explain the grub error
you see, GRUB part 1 is installed on the MBR of the master disk, primary disk
that is why you get a GRUB error.
open the computer up
see if the hard drive is connected, that it has not somehow gotten disconnected
when the computer is turned on, does the slave drive spin up?
it could be a problem that the BIOS may need to be reset.
The drive could have possible suddenly failed
If BIOS can not read the disk, it can not start.
the BIOS controls the computer boot, and finds the disks.
IF disks can not be located, then you have problems.

With all of that said, it sounds to me like either the BIOS lost the disk for reasons, of power, or IDE cable came loose somehow, Disk has gone bad, and BIOS can no longer read the disk, IDE controller has gone bad on motherboard - possible, but unlikely.  Or the BIOS needs to be reset.  If your motherboard has a jumper setting to reset BIOS, suggest you use it.  There may be an option in BIOS to reset, you could also physically remove the CMOS battery, for several seconds, and reincert it to reset BIOS.  After BIOS reset it should read the disks.  IF of course, the second disk is not spinning at all, it has completely died.

If you can provide me with more information, I could possible help more.
will be checking back later.

---

### Post by 123456789123456789123456 on 2009-03-18
sounds like a BIOS situation, the computer is not reading your second drive.  Therfore GRUB can not find it.

---

### Post by HarryZhe on 2009-03-18
IT's hard to tell if the hdd is spinning up because the damn live CD is so loud.
I'll check the connections... But it was working just fine last night and GRUB worked just this morning, 5 hours ago.

It was only after I actually ran winXP for thefirst time after installing the HD and Ubuntu that it stopped recognising the drive.

---

### Post by 123456789123456789123456 on 2009-03-18
you said that the BIOS was not reconizing the drive.  XP, or any changes to the primary hard drive would not have anything to do with that.  Even having grub install on the MBR would have caused no problems.  Try resetting BIOS.

---

### Post by HarryZhe on 2009-03-18
Ok I opened the ******* up, disconnected and reconnected the cables on the slave. Still error 17, BUT it can now see the HDD in bios. Going to commence reinstalling linux on slave.

---

### Post by 123456789123456789123456 on 2009-03-18
In advanced settings of the installer, tell GRUB to install on the drive with Ubuntu, not on MBR, that could also help.  You would however have to tell BIOS what disk to boot from, or edit ntloader of windows to include Ubuntu on the second hard disk inorder to boot then.

just a suggestion.

---

### Post by HarryZhe on 2009-03-18
I reinstalled Ubuntu and still, grub 17... What exactly should I do from here?

Also, the drives are both on auto settings in bios

Just removed the slave altogether, same error

---

### Post by HarryZhe on 2009-03-18
> **123456789123456789123456 said:**
> In advanced settings of the installer, tell GRUB to install on the drive with Ubuntu, not on MBR, that could also help.  You would however have to tell BIOS what disk to boot from, or edit ntloader of windows to include Ubuntu on the second hard disk inorder to boot then.

just a suggestion.

Should I reinstall again, and do it that way? (how do i tell it what disk to boot from)

---

### Post by louieb on 2009-03-18
The super grub disk or testdisk ( available on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") ) can restore the MBR of the 320 GB drive so that windows will boot. other way too   [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm") 

Kinda sounds like the 80GB drive might be dieing. I'd go to the manufactures site and see if theres a diagnostic utility to check it out with.

---

### Post by HarryZhe on 2009-03-18
I think I'll try installing grub onto the slave like that guy suggested first... I don't wanna put it down to a hardware failure just yet. I've had that HDD just sitting around for maybe a year or more, it worked fine when I first put it in but then just stopped.

I should also mention that when I opened it up i noticed the IDE was plugged in on a kind of angle. Replugging it in made it show up in the bios. and it's definitely spinning up.

---

### Post by fieroboom on 2009-03-18
> **HarryZhe said:**
> I think I'll try installing grub onto the slave like that guy suggested first... I don't wanna put it down to a hardware failure just yet. I've had that HDD just sitting around for maybe a year or more, it worked fine when I first put it in but then just stopped.

I should also mention that when I opened it up i noticed the IDE was plugged in on a kind of angle. Replugging it in made it show up in the bios. and it's definitely spinning up.

Instead of installing more stuff, why don't you just unplug the master drive, remove the jumper from the slave (or set it to single), and try to boot Ubuntu by itself? Seems to me that would be much faster, easier, and more reliable to rule out hardware issues...
:D
-Paul

---

### Post by 123456789123456789123456 on 2009-03-18
ok, this is what I know
the MBR(Master Boot Record) is where Grub part 1 is located, part 1 points to the drive/partition that Grub part 2, the acutall booting takes place.  If for some reason Grub part 1 can not locate the disk that Ubuntu is installed on, it can not run.  You reinstalled Ubuntu.  Grub part 1 would not have been replaced.  You must first completely remove grub and ntloader from the MBR.  Reinstall Grub onto the MBR.  List in GRUB windows.  That would allow GRUB part 1 to boot either windows or Ubuntu.  Possible problems, could be that when you reinstalled Ubuntu, it caused a boot sequence error, you may have to repair MBR

It is hard to know, not looking at the computer myself.
In order for GRUB to find the UBUNTU, the drive must be connected.  I would also manually jumber the drivers, not as cable select, but as master and slave.  When booting windows, does the system run GRUB, then go to boot windows?  if so, it is actually listing windows.  I know for instance, when I was using Vista, and Ubuntu, I had to uninstall a program used to edit windows boot loader.  but GRUB should recognize windows and boot it fine.

The only thing I can think of at the moment is that GRUB part 1 has lost connection to the UBUNTU located on the disk.  After reinstall, could be that the grub was not reinstalled with the OS.  using multiple drives can cause this problem.  You must completely remove GRUB from the MBR, use windows cd to do this.  Through the repair terminal, repair MBR.  that will erase GRUB, replacing it with ntldr.  windows boot loader.  You can use this only if you want, I can walk you through the process of using ntldr to boot Ubuntu.  If you choose to use GRUB again.  You reinstall Ubuntu on the second drive.  If you don't tell GRUB any different it will install Grub part 1 onto the MBR again, replacing ntldr.  windows should still boot with no problems, and Ubuntu should also boot now with no errors.

---

### Post by louieb on 2009-03-19
Just a note each drive has an MBR. On most computers there is either a BIOS or start up option to select which MBR is loaded at boot. 

Each partition has a boot section aka VBR (1st 63 sectors of the partition)  boot loaders such as grub or ntldr can take advantage of this to [chainload]("http://users.bigpond.net.au/hermanzone/p15.htm") other operating systems. (Grub also uses this area to store the stage 1.5 programs).

Grub uses 2 programs **stage1 **which goes in the MBR (the one in /boot/grub is just a copy) and **stage2** which loads the menu.  

If the 80GB drive is working error free then Grub should not have had a problem in the 1st place. You really should rule out hardware issues before taking the time to reinstall.

There is a script which can be found here [SourceForge.net: Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") written by a couple of forum regulars. It can be dowloaded and run from the live CD. 

[LIST]
[*] Download it to your Ubuntu desktop,
[*] then open a terminal (Applications > Accessories > Terminal) and do:
[*]```
sudo bash ~/Desktop/boot_info_script*.sh
```
[*]That will create a "RESULTS.txt" file in the same directory from where the script is run
[*]please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it.
[/LIST]

That will help us to give you the commands to fix whatever boot problems you are having.

---

### Post by HarryZhe on 2009-03-20
I solved this problem, by using my windows CD to reset the MBR, then reinstalled Ubuntu with grub on the secondary hard drive.

Now I choose to boot into ubuntu by pressing f12 on startup and selecting the second drive. Could also do it through BIOS.

---

