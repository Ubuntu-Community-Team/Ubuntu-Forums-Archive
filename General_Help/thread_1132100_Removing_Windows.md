---
title: "Removing Windows"
date: 2009-04-21
forum: General Help
---

### Post by matthewboh on 2009-04-21
Okay - have a dual boot system and NEVER use Windows anymore, so I want to get rid of it - but I'm having problems.  I saw that people suggest that I download gparted - but it hangs on scanning the disk.  I'm having problems reading the partition if I type in sudo ls -lh /dev/sda1

Any pointers?  I can find lots of posts getting rid of Ubuntu - but I want to get rid of Windows

---

### Post by sir_nasty on 2009-04-21
my suggestion would be to just format the windows partition then try gparted to recover the space, or keep it as a "seperate" drive.  Don't forget to update grub.

---

### Post by hyperdude111 on 2009-04-21
1. Download the ubuntu .iso and start the live cd
(You need this to be able to unmount the main partition)

2. Unplug all usb devices or other external media
(Some usb devices cause gparted to hang)

3. Start gparted from inside the live cd, delete the windows partition.
(Removes Windows)

4. Stretch the ubuntu partition to cover the empty space the last stage made.

5. Apply these changes (This takes a while) Then re-boot to you hard drive.

6. Back in your normal desktop go to terminal and ```
sudo gedit /boot/grub/menu.lst
``` and remove the option for windows at the bottom.
(Removes the windows option from grub)

7. Your done but remember to back up your data in case something goes wrong.

---

### Post by matthewboh on 2009-04-22
Thanks for the quick responses!

---

