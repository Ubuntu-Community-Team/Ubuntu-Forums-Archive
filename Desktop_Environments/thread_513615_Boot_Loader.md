---
title: "Boot Loader"
date: 2007-07-30
forum: Desktop Environments
---

### Post by bubba2120 on 2007-07-30
Hi,
First off I would like to say that I am not new to Ubuntu, I'm pretty familiar with it. But one that bothers me is the GRUB bootloader, I just dont like it. I was wondering if there was a way to remove GRUB and use the default bootloader but still have an option in the bootloader for ubuntu.

If it helps i have windows xp media center edidtion and ubuntu 7.04 (feisty fawn)

---

### Post by raja on 2007-07-30
If you mean the bootloader in windows, it does not recognise the linux partitions and cannot boot them. What is it that you dont like about grub - it is an immensely customizable program. There are alternatives, but I would stick to grub unless there is a real necessity to change.

---

### Post by flatwombat on 2007-07-30
You should be able to use the Windows bootloader as is described here: [http://amardeepsidhu.blogspot.com/2007/05/using-ntldr-to-boot-linux.html](http://amardeepsidhu.blogspot.com/2007/05/using-ntldr-to-boot-linux.html)  Google holds many more tutorials on it, by the way.  It's not particularly 'user-friendly' but if you follow closely, you should be okay.

---

### Post by bubba2120 on 2007-07-30
thanks for your help. its not really that theres anything wrong with it, its just i like the old one and plus i dont use all those extra kernals on there so it looks kindda messy.

---

### Post by nimajiman on 2007-07-31
You could also edit grub to only display the kernels you want, and even have different names come up on the grub menu. Just edit the menu.lst file (sudo gedit /boot/grub/menu.lst) and comment out the kernels you don't want to display. In mine its the section between 

## ## End Default Options ##

and

### END DEBIAN AUTOMAGIC KERNELS LIST

I commented out the old kernels that i don't really need to run (comment out each line of that kernels section) and changed the 'title' field of my current kernel to just "Launch Ubuntu" as it's a bit prettier than "Ubuntu, kernel 2.6.20-16-generic" etc... You would obviously back up the original menu.lst file first as well in case anything goes wrong, but i have had no troubles using this method. 

Not sure what will happen though when the kernel is upgraded, as I think they are automatically added to this file, but i guess the worst that would happen is that you would have to go through the process again with the new kernel.

If you add a grub splashscreen as well it ends up not looking so bad!

---

### Post by mcduck on 2007-07-31
> **nimajiman said:**
> You could also edit grub to only display the kernels you want, and even have different names come up on the grub menu. Just edit the menu.lst file (sudo gedit /boot/grub/menu.lst) and comment out the kernels you don't want to display. In mine its the section between 

## ## End Default Options ##

and

### END DEBIAN AUTOMAGIC KERNELS LIST

I commented out the old kernels that i don't really need to run (comment out each line of that kernels section) and changed the 'title' field of my current kernel to just "Launch Ubuntu" as it's a bit prettier than "Ubuntu, kernel 2.6.20-16-generic" etc... You would obviously back up the original menu.lst file first as well in case anything goes wrong, but i have had no troubles using this method. 

Not sure what will happen though when the kernel is upgraded, as I think they are automatically added to this file, but i guess the worst that would happen is that you would have to go through the process again with the new kernel.

If you add a grub splashscreen as well it ends up not looking so bad!
Why not just uninstall the old kernels with Synaptic? If you don't use them, they are just wasting your disk space. Alo there's option in the menu.lst file to set maximum number of kernels displayed in the menu..

For the OP, it's possible to use the windows boot loader, but every time you get a kernel update you'll need to edit the configuration by hand to use the new kernel.. It's just not worth the trouble..

---

### Post by flatwombat on 2007-07-31
Agree on commenting out the extra kernels rather than deleting them ('cause you never know when a bork's in your future!) and perhaps using the 'hiddenmenu' option and modifying the 'timeout' if you almost always boot to the same distro or OS.  I also use the 'pretty colors' option to make it a bit more appealing.

---

### Post by raja on 2007-07-31
Exactly ! This is what I meant by grub being configurable. 
I think setting an upper limit on number of kernels to display, hidden menu and pretty colors is the way to go. 
Just read through the /boot/grub/menu.lst and you will see the options.

---

### Post by mcduck on 2007-07-31
> **flatwombat said:**
> Agree on commenting out the extra kernels rather than deleting them ('cause you never know when a bork's in your future!) and perhaps using the 'hiddenmenu' option and modifying the 'timeout' if you almost always boot to the same distro or OS.  I also use the 'pretty colors' option to make it a bit more appealing.

Even in the worst case you would only ever need one older kernel version so keeping all of them is rather useless. Even more so when kernel image, modules, restricted modules and other related files for couple of older kernel versions easily eat gigabytes worth of disk space.

Of course if you have plenty of extra disk space and no better use for it you can save all the old kernels you want.

I always test the new kernel for week or so after update and then remove the old one.

---

### Post by bubba2120 on 2007-07-31
yeah i guess i'll just stick with grub and clean it up some and make it have pretty colors

---

