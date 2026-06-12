---
title: "unable to mount OS exit code 1 error message"
date: 2011-05-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by taoist33 on 2011-05-27
Good afternoon, I'm running with a Dell Studio 8100 | dual booting 10.10 & win7-
   I have a nasty one, but have made some progress.  In short I had been  working on reinstalling the java cause I needed to copy text from chat  in an I-frame which was all working good til I decided to upgrade to  Natty Narwhale.  Arrrg, anyways I'm staying with 10.10 from now on but  copied all of my ubuntu user dir to windows partition.Did the reinstall,  and had a movie on in Ubuntu, running from a dir on the windows  partition, also had a kingston flash drive in the USB.
  Okay , I had an appointment , in a hurry just pulled the flash drive out without "safely removing" device.
        Shutdown computer, came back later and than tried to mount the  win7 partition OS. got the famous unable to mount OS err msg 2.  Went  through alot of changes and reinstalls of legacy grubs, installed ntfs  -config, albe to mount the recovery partition now, however, in the disk  partition ntfs is 750 gb shows no usage. Finally after reinstalling when  ubuntu comes up on the splash screen shows that unable to mount OS.  when I try to mount it get the error now "unable to mount OS" Error  mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda3 on /media/Win7
   I was able to mount it in terminal yesterday, but can't get it to  boot into the win7 from the grub it just hangs for a second and reboots.   verified the uuid and have been manually trying to get it working with  the grub & fstab etc.  I have some really important data on my win7  drive now that I don't want to lose.
  If you could help me get this win7 to boot into win7 again that would  be incredibily helpful. I'm not a noob and usually run strictly ubuntu  and win7 for legacy programs.
   I find it weirdly significant that it happen in conjunction with the  flash drive and running a movie from the win7 dir in unbuntu .....

It mounts in terminal using the Sudo command only.

   thanks a bunch !

---

### Post by taoist33 on 2011-06-01
Well since no one else wanted to take up the gauntlet I will mark this  one as closed myself.  I found out that the MBR for the windows  partition was blown out .  
fix the MBR
after creating a usb bootable for win7
boot and choose command prompt , then at the command prompt type
bootrec /Rebuild BCD
bootrec /FixMbr
bootrec /FixBoot

after doing this it re-enables the recovery partition. Now the next  wonderful ephipany.  The backup restoration disks for the Dell xps 8100  studio are not created for a 1.5 tera byte drive so it hangs at 35 %  when formatting the drive. Than it pops up with an error 
0x4001100200001005 which means that it is a media error since the  restoration disk software was not created to work on large 1.5 terrabyte  drives.   Called Dell and they are going to send me out the proper set  of Restorations discs under warranty. Be here in a couple of days.  Learned alot through this experience. Maybe it will help someone else. 

In closing here is an excellent article 
[http://essayboard.com/2010/12/19/add...o-ubuntu-10-10]("http://essayboard.com/2010/12/19/adding-new-hard-drive-onto-ubuntu-10-10")

---

