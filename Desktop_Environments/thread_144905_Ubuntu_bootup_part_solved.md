---
title: "Ubuntu bootup part solved"
date: 2006-03-15
forum: Desktop Environments
---

### Post by Alij on 2006-03-15
Hi, I am still having bootup problems on my IBM Thinkpad 600x. 
Thanks to those who helped help.

Adding [acpi=off] to the Kernel line at bootup definitely solves the problem of hanging at the desktop screen, but I can’t seem to save it in the bootup routine. If I shut down and bootup again I would have to re-enter this into the kernel line again. How would I save this to make it permanent?

My bootup menu screen is as below:

Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)
Ubuntu, memtest86+

Pressing [e] to edited first line opens the following screen:

root  (hd0,0)
kernel /boot/vmlinuz-2.612-9-386 root=/dev/hda1 ro quiet splash
initrd  /boot/initrd.img-2.6.12-9-386
savedefault
boot

I added [acpi=off] to the kernel line above also [ide=nodma noapic]
Entering [b] for boot works fin and I am able to access all programmes (I think).
But this doesn’t make it permanent, when I reboot I have to go through the whole process again.

I’ve just noticed that Ramases had a [vga=792] at the end of his kernel line i.e. after splash. Would this make a difference to making it permanent?

Please help!!!!

---

### Post by Ramses de Norre on 2006-03-15
When logged in with the options do sudo gedit /boot/grub/menu.lst and apply the changes there, they will be permanent then.
The vga option is for the resolution of the grub menu, splash screen, shell only environment etc.

---

### Post by Alij on 2006-03-16
Hi 
Thanks for your help, Ramases, but as I’m still extremely new to Linux, and Ubuntu, I am a bit lost on how to make this permanent. 
I worked out the [gedit] bit by opening the editor (I guess this is for Gnome Editor?) and then opening system?/boot /grub/menu.lst 
then paged down and found the same Kernel line (as at bootup) and tried to edit this as suggested (I was quite excited at this stage as I thought I had cracked it). This is where I came unstuck (if not before) because the file was read only and I could not find, on the dropdown menus, how I could change this to edit it. 
Would you please spell it out to me? Was I at the right place to edit the Kernel line to make it permanent, and what is [sudo gedit]?? 
I think I’m missing something important here! 

It looks like its going to be more difficult than I thought to setup Ubuntu with all the software and drivers that I’ll need so I’ll probably be back quite often asking advice and guidance, so thanks to all for your help, in advance.

---

### Post by Alij on 2006-03-17
Hi All
I’ve finally found out how to *sudo gedit  /boot/grub/menu.lst*. As mentioned in my previous message I found the right file but was only able to open it as ‘read only’. Searching on the wiki for sudo and then rootsudo gave the following, amongst other results;
•		To run a program using sudo that normally is run as the user, such 	as gedit, go to Applications --> Accessories --> Terminal and 	enter gksudo gedit. 
I could then open the file edit and save to make the command permanent, this worked.

My original message was:
Hi, I am still having bootup problems on my IBM Thinkpad 600x. Thanks to Ramases and others for their help. 
Adding [acpi=off] to the Kernel line at bootup definitely solves the problem of hanging at the desktop screen, but I can’t seem to save it in the bootup routine. If I shut down and bootup again I would have to re-enter this into the kernel line again. How would I save this to make it permanent?

My bootup menu screen is as below:

Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)
Ubuntu, memtest86+

Pressing [e] to edited first line opens the following screen:

root  (hd0,0)
kernel /boot/vmlinuz-2.612-9-386 root=/dev/hda1 ro quiet splash
initrd  /boot/initrd.img-2.6.12-9-386
savedefault
boot

I added [acpi=off] to the kernel line above also [ide=nodma noapic]
Entering [b] for boot works fine and I am able to access all programmes (I think).
But this doesn’t make it permanent, when I reboot I have to go through the whole process again.

The method mentioned above makes it permanent (as mentioned by Ramases)

---

