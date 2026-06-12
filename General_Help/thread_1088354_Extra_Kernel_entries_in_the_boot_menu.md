---
title: "Extra Kernel entries in the boot menu"
date: 2009-03-05
forum: General Help
---

### Post by Beaslah on 2009-03-05
How many kernel up dates does grub keep in memory?  So far I got 4 and it seems a little excessive.  Is the best way to eliminate a old kernel boot option to go edit the /boot/grub/menu.lst file and take out the older

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=591d6e1d-0617-46da-a1a2-c4d6453cb238 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=591d6e1d-0617-46da-a1a2-c4d6453cb238 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

entries?  Or maybe I can change the howmany=7 term in this file to howmany=3 or something?

---

### Post by Nano_ext3 on 2009-03-05
In my experience it is best to keep at least* 2 kernels available at bootup.  This is to ensure if you mess up one kernel, you should still be able to get into the other kernel, if not the 2nd kernel in recovery mode.  

One method of only keeping two entries, if you wish, is to edit your /boot/grub/menu.lst file.  BEFORE you do this, make a copy by doing a "sudo cp menu.lst menu.lst.backup.  You can comment out any entries that you do not want (in your case the last, bottom 2 kernels), by putting a # sign in front of the line you want to "comment" out.  This ensures if you wish to get those entries back, all you need to do is uncomment them.  Edit this file by issuing the command: "sudo nano /boot/grub/menu.lst"

The second, easier method is to install "startup manager" for gnome.  You can find this is Add/Remove programs (make sure third party software in your Software Sources is enabled, and the applications drop down at the top of Add/Remove is selected to all available applications.)  You may also install by issuing the terminal command "sudo apt-get install startupmanager"

Using startup manager is quite easy.  The last tab limits how many kernels you want to keep in menu.lst.  The main screen lets you select the resolution or any custom options, such as a custom splash screen and the like.  Your main concern is the tab that controls the number of kernels.  Check the box to limit the number of kernels, and choose how many you want to show, I DEFINITELY suggest keeping at least 2.

Hope this helps!

Cheers!

-Nano

---

### Post by lykwydchykyn on 2009-03-05
If you have old entries, more than likely you have old kernels still installed.  Open Synaptic and search for "linux-image".  Remove the oldest two kernels, and it should automatically fix your grub config.

---

### Post by dcstar on 2009-03-05
> **Beaslah said:**
> How many kernel up dates does grub keep in memory?  So far I got 4 and it seems a little excessive.  Is the best way to eliminate a old kernel boot option to go edit the /boot/grub/menu.lst file and take out the older
.......
entries?  **Or maybe I can change the howmany=7 term in this file to howmany=3** or something?

Exactly.

3 is a good number as you will still have your old kernel if a new one arrives, and if the new one has problems and an even newer one is released to fix it, you will still have your "good" kernel at the bottom of the list!

---

### Post by ramjet_1953 on 2009-03-05
Another way to control the number of kernels and also do many other things, like displaying text while booting is to install the [COLOR="Blue"]startupmanager[/COLOR] package, by using synaptic, or by typing in:

```
sudo apt-get install startupmanager
```

Regards,
Roger :D

---

### Post by Beaslah on 2009-03-06
Thanks for the help guys. I'm to lazy to install stuff so I'll probably just go with dcstar's suggestion.

---

