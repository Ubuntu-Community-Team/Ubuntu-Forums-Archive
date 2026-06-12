---
title: "GRUB Doesn't count down"
date: 2009-02-07
forum: General Help
---

### Post by epswinde on 2009-02-07
Ok, so this is a rather odd issue I've been having for about a week now.

This is what happened:  I had the computer on in the morning checking email before I went to work, and (by accident) i chose reboot instead of shutdown.  No big deal, i though, i could just "catch" the system before it rebooted by pressing the power button, no waiting for the system to reboot.  So i did, and nothing bad seemed to happen.

Later that same day, when I got home from work, I went to boot my machine.  So, i turned it on and walked away (to get myself a beer or whatever) expecting to come back and find that it was at the login screen waiting for me.

Here's the odd bit:  GRUB hung at the countdown.  I have it set to 3 seconds before boot, and it was just sitting there with no counting at all.  Just stuck on 3.  I push enter to boot that kernel, and it worked fine.

So I tried changing the countdown time -- no change.  I used KDE's "restore grub" utility in the systemsettings -- no change.  I'm completely out of ideas short of a complete reinstall.

Anyone have any ideas why this might be happening?  and (aside from my current workaround of waiting) any ideas on how to fix it?

thanks in advance.

---

### Post by Hooya on 2009-02-07
can you post the contents of /boot/grub/menu.lst (it's a text file) in [code] tags?

---

### Post by epswinde on 2009-02-08
```

default 0                             
timeout 3                             
color white/blue                      

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options     
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.  
## e.g. kopt=root=/dev/hda1 ro                                    
##      kopt_2_6_8=root=/dev/hdc1 ro                              
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro                        
# kopt=root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro          

## default grub root device
## e.g. groot=(hd0,0)      
# groot=f1292149-6171-4f6f-ac4e-678a97c6a5a4

## should update-grub create alternative automagic boot options
## e.g. alternative=true                                       
##      alternative=false                                      
# alternative=true                                             

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true                                 
##      lockalternative=false                                
# lockalternative=false                                      

## additional options to use with the default boot option, but not with the
## alternatives                                                            
## e.g. defoptions=vga=791 resume=/dev/hda5                                
# defoptions=quiet splash                                                  

## should update-grub lock old automagic boot options
## e.g. lockold=false                                
##      lockold=true                                 
# lockold=false                                      

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=                                                       

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0                                             

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single                     
# altoptions=(recovery mode) single                      

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the     
## alternative kernel options                               
## e.g. howmany=all                                         
##      howmany=7                                           
# howmany=all                                               

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

But like i said:  grub still works as a bootloader, its just that the timer doesn't work.

---

### Post by caljohnsmith on 2009-02-08
It sounds like it could possibly be an issue with Grub's stage2 file somehow being slightly corrupted. How about trying:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo cp /usr/lib/grub/*pc/stage2 /boot/grub
```
Then reboot, and let me know if that makes any difference.

---

### Post by epswinde on 2009-02-08
I followed your suggested steps, but unfortunately no change in behavior.

Thanks for trying though.

---

### Post by caljohnsmith on 2009-02-08
OK, how about trying this:
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo update-grub
```
And when it asks if you want to create a new menu.lst, say "y". Then open up the new menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
Change the "timeout" line to whatever you want, and also I would recommend commenting out the "hiddenmenu" line:
```
#hiddenmenu
```
But please don't make any other changes so we can see if your previous backed-up menu.lst is the issue. Reboot, and let me know if anything changes.

---

### Post by epswinde on 2009-02-08
Tried the update-grub, which generated a new menu.lst .  Initial examination yields very little differences between the new and the old, merely commenting differences.  And no difference on reboot.

anyway, just for comparison:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),       
#            grub-md5-crypt, /usr/share/doc/grub    
#            and /usr/share/doc/grub-doc/.          

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.              
#                                                                            
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.                          
# WARNING: If you are using dmraid do not use 'savedefault' or your           
# array will desync and will not let you boot your system.                    
default         0                                                             

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).                                          
timeout         3                                                              

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu                                             

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the  
# command 'lock'                                                              
# e.g. password topsecret                                                     
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/                        
# password topsecret                                                          

#
# examples
#         
# title         Windows 95/98/NT/2000
# root          (hd0,0)                                                                             
# makeactive                                                                                        
# chainloader   +1                                                                                  
#                                                                                                   
# title         Linux                                                                               
# root          (hd0,1)                                                                             
# kernel        /vmlinuz root=/dev/hda2 ro                                                          
#                                                                                                   

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options     
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.  
## e.g. kopt=root=/dev/hda1 ro                                    
##      kopt_2_6_8=root=/dev/hdc1 ro                              
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro                        
# kopt=root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro          

## default grub root device
## e.g. groot=(hd0,0)      
# groot=f1292149-6171-4f6f-ac4e-678a97c6a5a4

## should update-grub create alternative automagic boot options
## e.g. alternative=true                                       
##      alternative=false                                      
# alternative=true                                             

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true                                 
##      lockalternative=false                                
# lockalternative=false                                      

## additional options to use with the default boot option, but not with the
## alternatives                                                            
## e.g. defoptions=vga=791 resume=/dev/hda5                                
# defoptions=quiet splash                                                  

## should update-grub lock old automagic boot options
## e.g. lockold=false                                
##      lockold=true                                 
# lockold=false                                      

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=                                                       

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0                                             

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single                     
# altoptions=(recovery mode) single                      

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the     
## alternative kernel options                               
## e.g. howmany=all                                         
##      howmany=7                                           
# howmany=all                                               

## should update-grub create memtest86 boot option
## e.g. memtest86=true                            
##      memtest86=false                           
# memtest86=true                                  

## should update-grub adjust the value of the default booted system
## can be true or false                                            
# updatedefaultentry=false                                         

## should update-grub add savedefault to the default options
## can be true or false                                     
# savedefault=false                                         

## ## End Default Options ##

title           Ubuntu 8.10, kernel 2.6.27-11-generic
uuid            f1292149-6171-4f6f-ac4e-678a97c6a5a4
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro quiet splash
initrd          /boot/initrd.img-2.6.27-11-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid            f1292149-6171-4f6f-ac4e-678a97c6a5a4
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro  single
initrd          /boot/initrd.img-2.6.27-11-generic

title           Ubuntu 8.10, kernel 2.6.27-9-generic
uuid            f1292149-6171-4f6f-ac4e-678a97c6a5a4
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro quiet splash
initrd          /boot/initrd.img-2.6.27-9-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid            f1292149-6171-4f6f-ac4e-678a97c6a5a4
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro  single
initrd          /boot/initrd.img-2.6.27-9-generic

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            f1292149-6171-4f6f-ac4e-678a97c6a5a4
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            f1292149-6171-4f6f-ac4e-678a97c6a5a4
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=f1292149-6171-4f6f-ac4e-678a97c6a5a4 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            f1292149-6171-4f6f-ac4e-678a97c6a5a4
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I haven't changed anything in this menu.lst.  In addition, i tried copying the /usr/lib/grub/i386-pc/stage1 file to /boot/grub/stage1, in case that was corrupted, as well as the e2fs_stage1_5 file in the same manner.  Neither helped the situation.  I don't have any of the other filesystems, only ext3 so that should be the only one in use.

Anyone have any ideas on how to repair the MBR and replace grub?  I'm not really looking to do a complete reintstall, I'd rather wait until Jaunty comes out to do that. :)

thanks again

---

### Post by caljohnsmith on 2009-02-08
Since you went ahead and put a new copy of Grub's stage1 and stage1.5 file in your /boot/grub directory, you can reinstall those files to the MBR with:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
But I don't think that reinstalling stage1 and stage1.5 will make any difference, because those files are merely used as steps to load stage2; it is stage2 that actually reads and interprets your menu.lst. But I guess it's worth a try because maybe I'm entirely wrong. I tend to think you might have an issue with your BIOS/computer clock, and that's what is giving you problems. Have you noticed any other problems with your computer not keeping track of time? Does your motherboard have an on-board battery for the BIOS password and clock or something of that sort you could replace?

---

### Post by epswinde on 2009-02-08
Hey, well done on the battery!  I replaced it and now everything works great!

many thanks!

edit: no solved under the thread tools tab.  but my issue has been solved!

---

### Post by caljohnsmith on 2009-02-08
Glad to hear that replacing the motherboard battery did the trick; cheers and enjoy your Ubuntu install. :)

---

