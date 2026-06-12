---
title: "kernel 2.6.29.1 ultimate. failed to fully install. Now affecting dpkg."
date: 2009-05-06
forum: General Help
---

### Post by benon on 2009-05-06
I installed this kernel using kernelcheck hoping my system would work better. It does not show on the boot list and its modules can't be found! I have tried to remove it without any success. Now when i try to install or upgrade anything i get this  very common dpkg error,you must manually run 'dpkg --configure -a'

benon@benon-laptop:~$ sudo dpkg --configure -a
[sudo] password for benon: 
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.29.1-ultimate
Cannot find /lib/modules/2.6.29.1-ultimate
update-initramfs: failed for /boot/initrd.img-2.6.29.1-ultimate
dpkg: subprocess post-installation script returned error exit status 1


benon@benon-laptop:~$ lsb_release -d
Description:	Ubuntu 8.04.2
benon@benon-laptop:~$ uname -mr
2.6.24-19-generic i686


benon@benon-laptop:~$ sudo lshw
[sudo] password for benon: 
benon-laptop              
    description: Portable Computer
    product: Vostro A860
    vendor: Dell Inc.
    serial: D1DJ6H1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-3100-1044-804A-C4C04F364831
  *-core
       description: Motherboard
       product: 0Y487G
       vendor: Dell Inc.
       physical id: 0
       serial: .D1DJ6H1.CN486438A92675.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A00 (08/15/2008)
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Microprocessor
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 133MHz


benon@benon-laptop:~$ sudo dpkg --audit
[sudo] password for benon: 
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      tools for generating an initramfs

benon@benon-laptop:~$ sudo dpkg --configure initramfs-tools
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.29.1-ultimate
Cannot find /lib/modules/2.6.29.1-ultimate
update-initramfs: failed for /boot/initrd.img-2.6.29.1-ultimate
dpkg: subprocess post-installation script returned error exit status 1
 
Am hoping all this helps in getting me any solution. Thanx anyone in advance.

---

### Post by cmost on 2009-05-06
I experienced this issue on my Debian box running a mixed Testing / Sid.  I've never seen this on Ubuntu and I am also using a 2.6.29.2 kernel.  Nevertheless, here's how I solved the problem:

sudo gedit /etc/kernel-img.conf

edit to look like this: Note: lines prefaced by "#" are the original; the following line is the change.

#postinst_hook = /sbin/update-grub
postinst_hook = update-grub
#postrm_hook = /sbin/update-grub
postrm_hook = update-grub
do_bootloader = no
do_symlinks = Yes
relative_links = Yes
#ramdisk = /usr/sbin/mkinitramfs
ramdisk = /usr/sbin/update-initramfs

Save the file

open a Terminal and then type:

sudo dpkg --configure -a

Viola! All errors (should now be) corrected and your new kernel and modules should be installed without issue!

Let me know if this worked for you.  Good luck!

---

### Post by benon on 2009-05-06
do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
postinst_hook = /sbin/update-grub
postrm_hook   = /sbin/update-grub

Made the changes except the RAM part which didn't come up! Error remains. But thanks. U'VE GIVEN ME SOME HOPE

---

### Post by cmost on 2009-05-06
I'd go ahead and add the line:
ramdisk = /usr/sbin/update-initramfs

and see if that doesn't straighten out the problem.

---

### Post by benon on 2009-05-07
postinst_hook = update-grub
postrm_hook = update-grub
do_bootloader = no
do_symlinks = Yes
relative_links = Yes
ramdisk = /usr/sbin/update-initramfs

I.ve decide to paste the text after the editing to make sure i have not made any mistakes. The error just won.t go! 

I don.t know if this is related. Am using an earlier kernel 2.6.24-19 because i can.t access wireless from 2.6.24-23-generic i686 my 'latest kernel' However this was there before i tried to install 2.6.29.1 ultimate.
       Thanx for the help so far.

---

### Post by cmost on 2009-05-07
May I ask why you're trying to use the Ubuntu Ultimate kernel and not the more generic kernels listed here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)  I'm using the 2.6.29.2 one myself on Jaunty and it works perfectly.  Which leads me to my next question:  are you getting this error ONLY with the Ultimate kernel or with any kernel?

---

### Post by dkruidhof on 2009-05-08
I just had this problem with another kernel. Actually, that's why I found this thread.
I fixed it by going to /var/lib/initramfs-tools/ and deleting the file that was named after the kernel that I had uninstalled. That allowed me to update my initramfs-tools. 

Unfortunately, I'm not that knowledgeable. I hope it doesn't break anything...

---

### Post by colau on 2009-05-08
> **cmost said:**
> I'd go ahead and add the line:
ramdisk = /usr/sbin/update-initramfs

and see if that doesn't straighten out the problem.
Hi,
Is there any problem here?
cat /etc/kernel-img.conf
[html]
do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
postinst_hook = update-grub
postrm_hook   = update-grub
[/html]
uname -r
[html]
2.6.29-020629-generic
[/html]

---

### Post by cmost on 2009-05-08
> **colau said:**
> Hi,
Is there any problem here?
cat /etc/kernel-img.conf
[html]
do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
postinst_hook = update-grub
postrm_hook   = update-grub
[/html]
uname -r
[html]
2.6.29-020629-generic
[/html]

I don't know, are you having problems?  The ramdisk line appears in Debian but not Ubuntu.  Nevertheless, a ramdisk is automatically created when a new kernel is installed.  I'm not yet used to the way Ubuntu deviates from Debian.  I can only say if all is working as it should, leave it alone!!!!  :guitar:

---

### Post by benon on 2009-05-08
Well let me make the problem a little clearer. I installed **/boot/initrd.img-2.6.29.1-ultimate** because that is what the application called kernelcheck gave me as the recommended kernel. Maybe i was wrong to trust kernelcheck.org. My other 2 ealier kernels are working. initrd.img-2.6.29.1-ultimate does not even appear on the bootloader menu! It never got fully installed so i can't even use it. I just need to remove it but how? 
      
     Then on the part of /var/lib/initramfs-tools/ i did find _947ee56e59987e2ca92e1bfd89e2065425e03208  /boot/initrd.img-2.6.29.1-ultimate_ though i don't know how to use root privilledges to remove it. Do i use sudo and what's the command.
     I tried to remove it using apt get but still i get the dpkg error!

benon@benon-laptop:~$ sudo apt-get remove initrd.img-2.6.29.1-ultimate 
[sudo] password for benon: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Sorry guys if am asking too much. And thanks again.

---

### Post by dkruidhof on 2009-05-11
Well, I haven't found any problems yet with what I did, so running 
```
sudo rm /var/lib/initramfs-tools/2.6.29.1-ultimate
```
should take care of it for you.

However, if that kernel is still installed or half-installed or whatever, then it may be better to keep the file around in case deleting it screws things up more. So maybe try moving it to your desktop with:
```
sudo mv /var/lib/initramfs-tools/2.6.29.1-ultimate /home/[username]/Desktop/2.6.29.1-ultimate
```
Then you can move it back if things get more broken.

---

### Post by benon on 2009-05-11
This is what i got from terminal.

benon@benon-laptop:~$ sudo mv /var/lib/initramfs-tools/2.6.29.1-ultimate /home/benon/Desktop/2.6.29.1-ultimate
[sudo] password for benon: 
mv: cannot stat `/var/lib/initramfs-tools/2.6.29.1-ultimate': No such file or directory


benon@benon-laptop:~$ sudo rm /var/lib/initramfs-tools/2.6.29.1-ultimate
[sudo] password for benon: 
rm: cannot remove `/var/lib/initramfs-tools/2.6.29.1-ultimate': No such file or directory

**Yet the problem seems to have resolved! **The file is nolonger present.Now Update manager is asking me if i want to upgrade-takes about 5 hours. should i go ahead?  Am not so sure what i pulled off but thanks to you guys I can download packages again! Should i just stay with my 2 kernels because now i fear upgrading!

---

### Post by Sef on 2009-05-11
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. Open the Terminal (Applications > Accessories > Terminal), then copy and paste (or type) this code:

```
 sudo dpkg --configure -a
```

---

### Post by benon on 2009-05-14
Sorry i've taken quite a while to reply. When i run the command sudo dpkg --configure -a nothing happens. Am thinking of doing a partial upgrade but it takes forever! What do u think? Otherwise thanks for all the help.

---

### Post by afrodeity on 2010-07-23
I have something similar. 

Installed linux-image-2.6.34.1-candela using kernelcheck, but it isn't inited properly, it runs into a kernal panic and root option is just /sda1
so I tried to sudo update-initramfs -u -v -k linux-image-2.6.34.1-candela
but this error: Cannot find /lib/modules/linux-image-2.6.34.1-candela

if I update-initramfs -u -v -k all 

the kernels which were installed previously are found and reconfigured, but no new kernel.

This is my kernel-image.conf
```

do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
postinst_hook = update-grub
postrm_hook   = update-grub

```

---

