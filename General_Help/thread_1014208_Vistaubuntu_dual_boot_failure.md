---
title: "Vista/ubuntu dual boot failure"
date: 2008-12-17
forum: General Help
---

### Post by zakad on 2008-12-17
nvidia-glx-new -> VISTA/UBUNTU DUAL BOOT FAILURE

SYSTEM: 
        Inspiron 530 Core 2 Duo (1 year) 
        Windows Vista Home Premium with Recovery Partition.   
              (NO INSTALLATION DISK)     
        PSU:  ACBel 300W 
INSTALLED:  
        Nvidia 8600 GTS graphics card (10 months) 
        Ubuntu 8.04--installed with WUBI (7 months) 
        PSU:  PC Power and Cooling Silencer 500W Dell (Nov 9, 2008) 
TECHNICAL EXPERTISE:
        Below average

                    HOW THE PROBLEM AROSE

I have been using dual boot of Vista and Ubuntu without problem.  Meanwhile, the Nvidia card was never detected in Ubuntu. On Nov 11, 2008, after attaching the 6 pin connector from the new power supply to the graphics card, I decided to install "nvidia-glx-new" from the Synaptic Package Manager (on top of the nvidia-website "NVIDIA-Linux-x86-177.80-pkg1.run" which I was unable to uninstall). The Synaptic confirmed that nvidia-glx-new was successfully installed. 
On restart, I was unable to boot, neither to Ubuntu nor to Windows Vista.   
       
On restarting, the "Windows Boot Manager"  window would duly appear.    

                   IF I SELECTED UBUNTU: 

I'd get (promptly, no time to press Insert): 

          Try (hd0,0): FAT16: No WUBILDR 
          Try (hd0,1): NTFS5: No wubildr 
          Try (hd0,2): NTFS5: No wubildr 
          Error: Cannot find GRLDR in all devices. 
          Press Ctrl+Alt+Del to restart 

Please note:
1.hd0.0; hd0,1 & hd0,2 are the 3 partitions on my hard disk,   respectively:  DELL (FAT16), RECOVERY (NTFS) & &#8220;main&#8221; (NTFS).
2.As I was able to confirm later, there was a &#8220;wubildr&#8221; file in the hd0,2 partition 
 
                      If I SELECTED WINDOWS:
 
I'd get: 

         Windows Error Recovery 
         Windows failed to start 
         Launch Startup Repair (Recommended)
         ..... 

In the Startup Repair process, a window entitled "System Recovery Options"  appeared.  The "Operating System" column  was left blank with the message "If you do not see your operating system listed, click Load Divers to load divers for your hard disk."  I had to skip this step since I had no installation medium. 

The Repair Process reported:

        Four tests were completed successfully, Error Code = 0x0.  
        One Root cause was found:   system volume on disk is corrupt.
        Repair Action:  File system repair (chkdsk).  Result:    
                      Completed successfully, Error Code = 0x0.

However, after this &#8220;repair,&#8221; boot up failed, and the Windows Boot Manager cycle was repeated without change.  Several such &#8220;repairs&#8221; had no effect.

Expert help, in English please, will be very much appreciated. 
Thank you in advance

zakad

---

### Post by zakad on 2008-12-17
UBUNTU PART SOLVED
I am delighted to report that my problem has been solved as far as Ubuntu is concerned.  All I did was to boot up from the Ubuntu live disk and then copy the file “wubildr” from /OS (which is /host in installed Ubuntu and  C:\   in Windows)  to RECOVERY.  I am now able to boot up  Ubuntu from the hard disk.

I have not been successful with the Windows boot up problem. I copied the files “BCD” and “winload.exe” from /host/Windows/System32/Boot  to RECOVERY.  No luck! 
 I also tried Startup Repair after loading from the “Vista Recovery Disk” (120MB) downloaded from PC World.  Again, repair was ineffective.
 After some of my attempts, selecting Ubuntu for boot up failed and instead led to a black page with:

           initramfs

from which I was able to exit only by pressing Ctrl+Alt+Del in order to restart.  Fortunately,  I was always able to undo the damage by again booting up from the Ubuntu live disk and/or launching Windows Startup Repair.

I am afraid that one of my nonexpert “repairs” may again mess up the Ubuntu boot up process.  I can do without Windows Vista but not Ubuntu!

Expert help is badly needed.
Thanks again,

zakad

---

### Post by TeXtonyx on 2008-12-17
I'm not an expert in this area, but I think I have a good idea.

Ubuntu 8.10 made changes to xorg.conf and I'm more familiar with
8.04. Anyway I think the problem is due to the driver that you
installed. So my idea is to boot from the Ubuntu live cd and
navigate (nautilus) to /etc/X11 which is where your xorg.conf
is stored. When you installed the new driver the system made a
new xorg.conf. So look for an older xorg.conf.bak or xorg.conf~

Just to look at the xorg.conf file I think  
cat xorg.conf 
will work to show what driver you are using now. You want to go
back to the xorg.conf that was working before you installed the
new driver. 

Once you find the old copy of xorg.conf restore it this way,
from within the /etc/X11 directory,  
sudo cp xorg.conf xorg.conf.NEW
sudo rm xorg.conf
sudo cp xorg.conf.OldWorkingCopy xorg.conf

OldWorkingCopy means use the filename that was used to describe
the old xorg.conf.Bak (the one that used to work before)
I don't know what the old backup file will be named so you will
have to find the correct old one yourself and note the filename.

I think this will load the non-harmful driver. There are a lot
of problems getting nVidia drivers to work. So do a Search, at
the upper right hand corner of the Ubuntu forum webpage.
Put in the name of your video card.
Very likely there will be a thread or two that describes what
somebody did to solve their driver problem with your video card.

Often this process involves removing the previous failed drivers 
and starting with a clean slate. This isn't going to work if 
there aren't any backups of xorg.conf, but my system always had
a few of them. Try to find something dated just before Nov 11 '08

---

### Post by zakad on 2008-12-19
Thank you TeXtonyx.
I must add that after the mishap with "nvidia-glx-new", I marked this driver for “complete removal” in Synaptic and applied the change.  I then downloaded and installed “NVIDIA-Linux-x86-177.82-pkg1.run” from the nvidia website.  This solved my longstanding graphics card problem.  At present, ubuntu 8.04 starts up and runs “normally”; the nvidia card is detected and the improvement in the video display is quite noticeable.
I am, therefore, hesitant to replace the current “xorg.conf” with an earlier file from a time when Vista  was accessible but the nvidia card was not detectable.  I could edit “xorg.conf” manually if I knew the “Section” to be edited.  If you are interested, I can provide the current “xorg.conf” as well as another “Modified:  Thu 06 Nov  2008” so that you may be able to guide me through  the changes to be implemented.
However, as far as I understand,  “xorg.conf” essentially applies to input/output.   I must confess that I do not see its relevance to the startup problem.
Could the problem be traced to another file  that was altered when I installed “nvidia-glx-new”?

---

