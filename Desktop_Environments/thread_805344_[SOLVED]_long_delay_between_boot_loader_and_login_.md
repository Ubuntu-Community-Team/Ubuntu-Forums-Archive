---
title: "[SOLVED] long delay between boot loader and login screen"
date: 2008-05-23
forum: Desktop Environments
---

### Post by spyd3r on 2008-05-23
i have an extremely long delay between the graphical boot loader and the actual login prompt. normally i wouldn't mind, but this is taking several minutes.  after boot everything is snappy and running fine, it's just the delay between the boot to login screen that is taking forever. please help!
runnunig hardy

---

### Post by Steve413z on 2008-05-23
do you see the ubuntu logo with the loading bar underneath? 

sounds to me like the spash boot screen isn't being displayed

---

### Post by spyd3r on 2008-05-24
yes, there is a long delay after that and before the login

---

### Post by NikoC on 2008-05-24
I had the same problem and this did the trick for me:
as soon as the grub boot menu appears, press 'e' to edit the commands before booting, select your kernel and press 'e' again.
Add 'clocksource=hpet' (without the ') to the kernel bootline, press enter and 'b' to boot. If this fixes your problem you might want to make this more definite by going into a terminal and typing:
sudo gedit /boot/grub/menu.lst and adding 'clocksourse=hpet' to your kernel line and saving.

---

### Post by spyd3r on 2008-05-25
that did not work, however changing the GDM theme did. Must've been a buggy one! Thanks for your help!

---

### Post by Optximus on 2011-05-11
**I'm a great ubuntu fan and stopped using my win7 when I fell in love with ubuntu when I first used the wubi installation...Now that I have done the livecd installation and have upgraded to the Natty Narwhal, my*[COLOR=Red] linux kernel 2.6.38-9[/COLOR]* can no longer boot and it always comes back with the information that my disk has errors and needs to be checked...; I therefore hit the 'f' to fix everything but the result always comes back with the same error thing and I tried running the fsck stuff and the result comes with this warning:**

[I][SIZE=3][COLOR=Blue]update-initramfs: Generating /boot/initrd.img-2.6.38-9-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda6
cryptsetup: WARNING: could not determine root device from /etc/fstab
cryptsetup: WARNING: failed to detect canonical device of /dev/sda7

.....[/COLOR][/SIZE][/I][SIZE=3][COLOR=Blue][B][COLOR=Black]the funny thing being that when I try running the previous kernel 2.6.38-8, the boot process runs smooth and no errors detected and no word or warning about disk having any errors....Can some one tell me what is wrong with my ubuntu or should I just remove the latest kernel since it is somehow useless in regards to how it is right now?
Thanks and all help appreciated. [/COLOR][/B]
[/COLOR][/SIZE]

---

