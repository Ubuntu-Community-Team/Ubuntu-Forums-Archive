---
title: "update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic"
date: 2009-05-05
forum: Desktop Environments
---

### Post by SILLAT on 2009-05-05
I got some Updates this morning (May-5-2009) for Ubuntu Jaunty 9.04 while i was installing the updates i think the Clamav Daemond Update froze my Desktop Pc so i had to hit the reset button to Restart my computer. After i Restart it and run sudo apt-get update it i got  'dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem' so i did what it said, after i did that it install all the updates except one for 'initramfs-tools'
I cant seem to get that update through an everytime i run sudo apt-get update i get dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
And when i run sudo dpkg --configure -a
i get this error :
 dpkg --configure -a 
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./etc/modprobe.d/motorola_ve.options: Cannot stat: No such file or directory
cpio: blank line ignored
cpio: ./etc/modprobe.d/motorola_ve.options: Cannot stat: No such file or directory
cpio: ~: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: subprocess post-installation script returned error exit status 1

How can i Correct this Problem . .? :confused:

---

### Post by omniwired on 2009-05-05
This is a workaround not real fix I believe, but at least it takes that things out of the way.

I ran sudo gedit /etc/initramfs-tools/update-initramfs.conf

where is said "update_initramfs=yes" I putted update_initramfs=no. Saved the file and ran "sudo dpkg --configure -a" once again.

That thing  "fixed" the problem. Then I change the file to "yes" again, just in case.

---

### Post by SILLAT on 2009-05-05
> **omniwired said:**
> This is a workaround not real fix I believe, but at least it takes that things out of the way.

I ran sudo gedit /etc/initramfs-tools/update-initramfs.conf

where is said "update_initramfs=yes" I putted update_initramfs=no. Saved the file and ran "sudo dpkg --configure -a" once again.

That thing  "fixed" the problem. Then I change the file to "yes" again, just in case.


Thanks omniwired .. it worked like a Charm
I Guess i Hav to use this lil trick until someone Gives me a complete fix for this problem.
I'll watch it and see how it works out

Thanks Again :P:P

---

### Post by OzzyFrank on 2010-05-24
Hi. I'm interested to know if you changed that value back to "yes", and if everything was still fine after that. Cheers

---

### Post by SILLAT on 2010-05-27
> **OzzyFrank said:**
> Hi. I'm interested to know if you changed that value back to "yes", and if everything was still fine after that. Cheers

SORRRY for the late answer but Everything Worked Fine after i change it back to "yes" 
At the time of this problem i had to keep the value at NO and always NO when i have a Kernel Update/Upgrade or else it wouldn't work (the update will not go through unless its NO)
You have to keep it at "NO" when you have kernel updates then change it back to "YES" after your Kernel Updates


Hope this Helps !

---

