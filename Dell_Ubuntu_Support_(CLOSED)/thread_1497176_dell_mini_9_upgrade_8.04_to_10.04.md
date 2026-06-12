---
title: "dell mini 9 upgrade 8.04 to 10.04"
date: 2010-05-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by engr_sav on 2010-05-30
good morning. I have a Dell Mini 9 that came preloaded with ubuntu 8.04 LTS. I would like to upgrade to 10.04 LTS, my first OS upgrade. the Mini 9 has 16gb solid state drive. Can I go from 8.04 to 10.04 in one step? I've downloaded the 10.04 LTS netbook version from Ubuntu as an ISO file but not sure what to do next. thanks.

---

### Post by Joe of loath on 2010-05-30
The best way to do it is over the internet. If you go into the terminal and type 'sudo update-manager -d' It will give you the option to upgrade.

---

### Post by lswartz on 2010-05-30
Or, you can make a bootable USB which worked well for me [http://www.ubuntulinux.org/desktop/get-ubuntu/download]("http://www.ubuntulinux.org/desktop/get-ubuntu/download"). This link tells you how to do it.

---

### Post by Joe of loath on 2010-05-30
> **lswartz said:**
> Or, you can make a bootable USB which worked well for me [http://www.ubuntulinux.org/desktop/get-ubuntu/download]("http://www.ubuntulinux.org/desktop/get-ubuntu/download"). This link tells you how to do it.

But unless they've changed the installer, the only disc you can upgrade from is the alternate install disc.

---

### Post by ugm6hr on 2010-05-30
Let me clarify...  I have a Mini 9 (pre-loaded Ubuntu 8.04 originally), albeit with 8GB SSD.

Issues to bear in mind:
1. The original Dell Ubuntu 8.04 was an "lpia" version, which is no longer supported on 10.04.
2. Dell Ubuntu 8.04 uses a special Dell / lpia repository, which does not have USB "Startup Disk Creator"
3. Dell Ubuntu 8.04 has proprietary Fluendo codecs for mp3 etc.

What this means to you:
1. You can't upgrade as suggested by J of loath.
2. You can't create a USB bootable image on your Mini as suggested by lswartz.
3. You may want to consider backing up your codecs to reinstall after a fresh install of 10.04: [http://ubuntuforums.org/showthread.php?p=9224709#post9224709](http://ubuntuforums.org/showthread.php?p=9224709#post9224709) (I didn't do this myself - but apparently it does work)

So - how do you actually achieve the upgrade (fresh install)?

1. Backup your files you want to keep, or just backup the entire /home directory to restore if you want to keep all application settings etc.
2. Backup fluendo codecs, if you want to (see above).
3. Create a bootable USB startup disk from your iso you downloaded using any other computer (i.e. not your Mini) as instructions linked to by lswartz.
4. Turn off Mini, and plug bootable USB in.
5. Press 0 on the first boot screen after turning Mini on and select USB as boot device.
6. Follow instructions to install...
7. Restore files or /home and/or codecs as you wish.
8. Restore wifi with: [http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

That's it.

---

### Post by lswartz on 2010-05-30
Humbled by ugm6hr's post. I wish I could write (maybe think too) as clearly. He/she is spot on to a solution for you.

---

### Post by engr_sav on 2010-05-31
> **ugm6hr said:**
> Let me clarify...  I have a Mini 9 (pre-loaded Ubuntu 8.04 originally), albeit with 8GB SSD.

Issues to bear in mind:
1. The original Dell Ubuntu 8.04 was an "lpia" version, which is no longer supported on 10.04.
2. Dell Ubuntu 8.04 uses a special Dell / lpia repository, which does not have USB "Startup Disk Creator"
3. Dell Ubuntu 8.04 has proprietary Fluendo codecs for mp3 etc.

What this means to you:
1. You can't upgrade as suggested by J of loath.
2. You can't create a USB bootable image on your Mini as suggested by lswartz.
3. You may want to consider backing up your codecs to reinstall after a fresh install of 10.04: [http://ubuntuforums.org/showthread.php?p=9224709#post9224709](http://ubuntuforums.org/showthread.php?p=9224709#post9224709) (I didn't do this myself - but apparently it does work)

So - how do you actually achieve the upgrade (fresh install)?

1. Backup your files you want to keep, or just backup the entire /home directory to restore if you want to keep all application settings etc.
2. Backup fluendo codecs, if you want to (see above).
3. Create a bootable USB startup disk from your iso you downloaded using any other computer (i.e. not your Mini) as instructions linked to by lswartz.
4. Turn off Mini, and plug bootable USB in.
5. Press 0 on the first boot screen after turning Mini on and select USB as boot device.
6. Follow instructions to install...
7. Restore files or /home and/or codecs as you wish.
8. Restore wifi with: [http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

That's it.
thank you for responding so quickly. I suspected it might not be as easy as hoped. I'll will give your suggestions a try.

---

### Post by engr_sav on 2010-06-02
just a note to say thanks for the quick response and for the suggestions. I loaded the netbook version of 10.04 and all seems to be working fine at this point. thanks again.

---

### Post by chiphazmaj on 2011-02-20
Simple fix:

Go here:  [ftp://ftp.dell.com/OS/](ftp://ftp.dell.com/OS/)  and get ubuntu-10.10-i386-dell_A00.iso  Use a windows machine to burn the image.

Get a cheap usb DVD player or borrow one and install it that way.  It installs Ubuntu and builds the recovery partition

---

### Post by clarkthehardy910mini on 2011-04-03
> **chiphazmaj said:**
> Simple fix:

Go here:  [ftp://ftp.dell.com/OS/](ftp://ftp.dell.com/OS/)  and get ubuntu-10.10-i386-dell_A00.iso  Use a windows machine to burn the image.

Get a cheap usb DVD player or borrow one and install it that way.  It installs Ubuntu and builds the recovery partition

Has anyone tried this new method of using the ftp file for 10.10 on the dell mini 910? 

I currently have the 8.0410.10 and would like to go up to 10.10, trying to decide which route is easier and sure to work.

Thanks!

---

### Post by sracusin on 2011-07-10
> **ugm6hr said:**
> Let me clarify...  I have a Mini 9 (pre-loaded Ubuntu 8.04 originally), albeit with 8GB SSD.

Issues to bear in mind:
1. The original Dell Ubuntu 8.04 was an "lpia" version, which is no longer supported on 10.04.
2. Dell Ubuntu 8.04 uses a special Dell / lpia repository, which does not have USB "Startup Disk Creator"
3. Dell Ubuntu 8.04 has proprietary Fluendo codecs for mp3 etc.

What this means to you:
1. You can't upgrade as suggested by J of loath.
2. You can't create a USB bootable image on your Mini as suggested by lswartz.
3. You may want to consider backing up your codecs to reinstall after a fresh install of 10.04: [http://ubuntuforums.org/showthread.php?p=9224709#post9224709](http://ubuntuforums.org/showthread.php?p=9224709#post9224709) (I didn't do this myself - but apparently it does work)

So - how do you actually achieve the upgrade (fresh install)?

1. Backup your files you want to keep, or just backup the entire /home directory to restore if you want to keep all application settings etc.
2. Backup fluendo codecs, if you want to (see above).
3. Create a bootable USB startup disk from your iso you downloaded using any other computer (i.e. not your Mini) as instructions linked to by lswartz.
4. Turn off Mini, and plug bootable USB in.
5. Press 0 on the first boot screen after turning Mini on and select USB as boot device.
6. Follow instructions to install...
7. Restore files or /home and/or codecs as you wish.
8. Restore wifi with: [http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

That's it.
Thanks usm6hr for your thorough help. I followed your instructions to the T for my Dell mini 8.04 (hardy) to 10.04 netbook (lucid), sucessfully backed up, found my audio codecs, created a USB using pendrive and pressing 0 at bootup or f12 will boot from this flash drive. I am getting frustrated. I thought I finally found the help I needed and I still can't get anywhere. 8.04 is so useless. I need skype and some other apps that I can't install on it.
I am beginning to believe that this device cannot be upgraded. Thanks in advance for any further help you can give me.

---

### Post by Joe of loath on 2011-07-10
EDIT: The howto is for that.

How did you create the USB stick?

---

### Post by sracusin on 2011-07-10
> **engr_sav said:**
> just a note to say thanks for the quick response and for the suggestions. I loaded the netbook version of 10.04 and all seems to be working fine at this point. thanks again.

engr_sav! I am trying to follow ugm6hr's instructions and cannot boot from the flashdrive I created using pendrive. I have hardy and want to upgrade to lucid and used the 10.4 netbook installer. The pendrive install seemed to go ok but I can't use 0 or F12 to boot from it which tells me I must have not created a boot partition on it.
Any suggestons? I might have to resort to a CD but I would rather not have to find one.
Thanks

---

### Post by Joe of loath on 2011-07-10
You said this already. Answer my question, how did you do the USB install?

---

### Post by ugm6hr on 2011-07-10
> **sracusin said:**
> The pendrive install seemed to go ok but I can't use 0 or F12 to boot from it which tells me I must have not created a boot partition on it.
Any suggestons?
Yes. The problem is the pendrive install.
You need to:
1. Check the md5sum of the iso file you downloaded.
2. Ensure you did not create the pendrive install on the Mini.

---

### Post by sracusin on 2011-07-10
> **Joe of loath said:**
> EDIT: The howto is for that.

How did you create the USB stick?

I read a lot of howto articles and ugm6hr's was the best of all posts. 

I downloaded the netbook iso (windows exe) and created the flash boot on my windows device. I am a newbie to ubuntu so have mercy. I assumed the end result would boot ubuntu but maybe I was wrong.

---

### Post by sracusin on 2011-07-10
> **Joe of loath said:**
> You said this already. Answer my question, how did you do the USB install?

ugm6hr seems to thin that my USB was not created correctly. I am not sure what I am supposed to look for on the md5sum text file but what I did was I downloaded an .exe from ubuntu, stored it on the flash drive I was ultimately using along with the pendrive bootup installer (both on the flash drive) and ran the boot creator from Windows XP. (started out empty with a total of 4gb free)
It wasn't intuitive whether I should keep the boot creator file in Windows or together with the lucid image. I hope that is what you are asking...a blow by blow of what I did.
The pendrive boot creator is Universal-USB-Installer-1.8.5.6.exe

---

### Post by ugm6hr on 2011-07-12
> **sracusin said:**
> I read a lot of howto articles and ugm6hr's was the best of all posts. 

I downloaded the netbook iso (windows exe) and created the flash boot on my windows device. I am a newbie to ubuntu so have mercy. I assumed the end result would boot ubuntu but maybe I was wrong.

What netbook iso exe? Show us where you got the link for this file. The iso is an iso - not an exe.

The instructions about how to create a Live USB on Windows are here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
(See item 2)

md5sum is explained here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

> I am beginning to believe that this device cannot be upgraded. 
Be assured this is not true. I say that from personal experience with the same (identical) device.

---

### Post by ComputerMedics on 2011-12-29
Update...

Go to [ftp://ftp.dell.com/OS/]("ftp://ftp.dell.com/OS/") and download ubuntu-10.04-dell_A00.iso for a full Dell install/restore ISO.

Use the method detailed above to create a USB install and select the unlisted (old file system) option...

---

