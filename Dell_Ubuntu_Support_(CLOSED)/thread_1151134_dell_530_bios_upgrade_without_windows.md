---
title: "dell 530 bios upgrade without windows"
date: 2009-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aessen on 2009-05-06
i finally managed to upgrade my version 1.0.0 bios in my dell inspiron 530s without using windows.  i don't have windows on it or available to install and none of the recommended linux upgrade methods worked.  i tried many.

the firmware_tools route listed  in [https://wiki.ubuntu.com/DellBIOS ]("https://wiki.ubuntu.com/DellBIOS")looked easy enough.  but it does not work for a few systems, 530 included.  darn.

the biosdisk route didn't look too bad either.  this is described in the above link and also at [http://ubuntuforums.org/showthread.php?t=648824](http://ubuntuforums.org/showthread.php?t=648824).  the biosdisk routine got pretty far and actually ran the bios .exe for the first time.  but then it failed with a very helpful "error udosexe = -5".  given the .exe is 700k and installed on a 1.4m floppy image, this probably means disk full.

so now i decided to try the bootable usb flash route.  this worked pretty well with one important catch:  *** the usb drive must have at least 2 partitions including 1 vfat ***

the dell bios apparently assumes a usb flash with 1 vfat partition is a usb-zip, not usb-hdd.  this means that new bootable usb with the bios on it won't boot so no upgrade.  the install steps require usb-hdd and won't work with usb-zip so this caused a bit of grief.  is this normal bios behavior??

so... here's what to do:

short form:
make a freedos bootable usb, copy the bios .exe files on it, use freedos to run the bios updater.

details:
1. go to [http://support.dell.com/](http://support.dell.com/) under "drivers & downloads" and get the appropriate bios .exe file.

2. go to [http://www.freedos.org/freedos/files/](http://www.freedos.org/freedos/files/) and download fdbasecd.iso (freedos base install).  burn it to a cd.  i usually just boot the .iso in kvm and install to usb that way -- less likely to nuke the main hard drive.  but freedos didn't work in kvm for me, perhaps too much real-mode x86??  so i needed a real cd.

3. grab a usb flash (64 mbytes is plenty) and partition it with a tiny (e.g., 4 mbyte) ext2 partition plus the rest with a fat partition.  mark the fat active.  mkfs.ext2 & mkfs.vfat on the appropriate partitions.

4. stick in the usb flash & boot the freedos cd.  click through everything and install freedos on the usb.  make sure it installs on the proper partition!  don't kill your regular boot drive.  if there is only 1 fat partition amongst all your drives, the freedos install seems to find the right spot and do the right thing.

5. reboot linux and copy over the bios .exe files onto the usb flash.

6. reboot again from the usb flash (probably need to go to boot menu and/or bios settings)

7. run the bios .exe file and hope for the best.

8. reboot and check the boot messages for the new bios version!

this recipe is probably useful for all sorts of dos based bios updaters.

---

### Post by floborg on 2009-05-06
I had trouble booting a Cruzer Micro on my 530n, but got it to work with a single FAT32 partition.  It was booting fine on an HP dc office tower just by setting the boot flag, but the 530n only recognized a USB ZIP, and wouldn't boot from it.

So, I ran the USB startup disk creator from the Jaunty beta and it added the **LBA** flag to the partition.  That was it.  The BIOS recognized it as USB HDD, and it booted.

My BIOS is now and has always been 1.0.15.

---

### Post by aessen on 2009-05-07
i set the partition to lba and it still showed up as usb-zip for me.  i tried a few variants and it always came up as usb-zip.  i must be missing something else.  but as long as i can force usb-hdd with a 2nd ext2 partition i'm happy.

i'm also running bios 1.0.15 right now.  i'm not sure if you can downgrade the bios so i picked the oldest one that looked stable.  1.0.18 has quite a few complainers.  i got my 530s when it was hot off the press back in summer 2007.  maybe too hot, given the 1.0.0 bios and e1000 ethernet driver annoyances back then.

---

### Post by gbrainin on 2009-05-07
Is there someplace I can get information on the different BIOS versions?  I've got an old (1.0.0) version, and have been following the old adage of "don't mess with the BIOS unless there's a specific problem you have."  But perhaps there are changes that would be beneficial, and I just don't know they're there.

---

### Post by aessen on 2009-05-08
i don't know if there is a list of bios versions and fixes.  a kind of tedious solution is to go to the download site for the latest bios.  from there under "fixes and enhancements" you can see what that bios provides.  then you can go to "other versions" and repeat the process.

try starting here: [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R212148&SystemID=INSP_DSKTP_D530S&servicetag=&os=WLH&osl=en&deviceid=14181&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=299050](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R212148&SystemID=INSP_DSKTP_D530S&servicetag=&os=WLH&osl=en&deviceid=14181&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=299050)
or at the top here:  [http://support.dell.com/](http://support.dell.com/)

i jumped from 1.0.0 to 1.0.15.  2 fixes i know it includes are (a) no longer crashing horribly and requiring the power to be unplugged if i try to boot off usb with a corrupted mbr and (b) correctly handling  up to 8 gbytes of dram.  ok, the corrupt mbr was my fault but not resetting properly after power cycling was pretty bad.  as far as i can tell, the bios menu for 1.0.15 & 1.0.0 is exactly the same.  no new features, just bug fixes.

---

### Post by gbrainin on 2009-05-08
Thanks!

---

