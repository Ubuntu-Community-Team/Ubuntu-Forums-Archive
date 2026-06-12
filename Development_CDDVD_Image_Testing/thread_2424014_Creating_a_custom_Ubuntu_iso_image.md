---
title: "Creating a custom Ubuntu iso image"
date: 2019-08-01
forum: Development CD/DVD Image Testing
---

### Post by orion20k on 2019-08-01
i was wondering if i got a clean install of Ubuntu up and running customized with the apps and wallpapers and theams i use and other tweeks,  is there an app or a method of making a live iso image from the installation and if so is there a way it could have an installer so i could install it to a hdd if i wanted to?

---

### Post by oldfred on 2019-08-01
But you really are discussing backup and there are many ways. 
The image backup is obsolete a few minutes after you create it, but some like to do that.
 
       Full image backups
[URL="http://clonezilla.org/"]http://clonezilla.org/
      [/URL]
 fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) 
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart) 

       Includes UEFI
[http://askubuntu.com/questions/457528/how-do-i-create-an-efi-bootable-iso-of-a-customized-version-of-ubuntu](http://askubuntu.com/questions/457528/how-do-i-create-an-efi-bootable-iso-of-a-customized-version-of-ubuntu)
[http://askubuntu.com/questions/122505/how-do-i-create-a-completely-unattended-install-of-ubuntu](http://askubuntu.com/questions/122505/how-do-i-create-a-completely-unattended-install-of-ubuntu) 
    
But you cannot restore an image onto the same system, but another drive. Duplicate UUIDs are not allowed.

 I prefer to not waste space on copying Ubuntu, and plan on just reinstalling it, restoring list of installed apps, some settings from /etc & /home & data.Your /home has all the user settings you have made. If you change any system setting those would be in /etc. I only change a couple in /etc & copy to my /home so I do not directly backup /etc.
      
 scripts instead of custom ISO
[https://ubuntuforums.org/showthread.php?t=2394463](https://ubuntuforums.org/showthread.php?t=2394463)

---

### Post by orion20k on 2019-08-01
its not for backup its literally going to be used to scan my mums laptop for viruses and malware would be nice to have my favourite apps handy and i might use it as a base installer for my own systems

---

### Post by mastablasta on 2019-08-02
create a live USB with persistance.

there are also rescue disks and troubleshooting/booting disks. 

so an option is to create a multiboot USB with useful live distros on with and add some persistence to them if needed. for example add bitdefender rescue antivirus disk, ultimate boot CD (for troubleshooting), some ligth full distro (e.g. xubuntu) with your favourite apps on it.

---

### Post by slickymaster on 2019-08-02
Moving this thread moved to **Development CD/DVD Image Testing** for a better fit

---

