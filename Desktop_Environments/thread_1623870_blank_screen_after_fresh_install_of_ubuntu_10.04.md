---
title: "blank screen after fresh install of ubuntu 10.04"
date: 2010-11-17
forum: Desktop Environments
---

### Post by surfer on 2010-11-17
i have a new machine with an nvidia (Quadro Plex s4 / Tesla S870 / Tesla S1070 (rev a3)) graphics card.

i made a fresh install of ubuntu 10.04.1, rebooted and saw... nothing. there seems to be no signal for the monitor.

after some googling i learned that i should set 'nomodeset' for every kernel line in boot. so far so good. i see the terminal (and probably also X; haven't tried yet).

but what's still missing is that i see the boot prompt of grub. is there a way to fix that?

---

### Post by surfer on 2010-11-17
on top of that: when booting with a splash screen, the display of the screen is huge and the important messages are so far at the bootom of the screen that i can't read them all.

yes, nosplash would fix that, but the splash is so nice...

---

### Post by sikander3786 on 2010-11-17
You need to press and hold down Shift key from Bios screen until you see Grub menu.

Highlighting the first entry, press 'e' to edit it and remove "quiet & splash" and type "nomodeset" in their place. Then press Ctrl + X to continue boot.

After you boot successfully, go to System > Administration > Hardware Drivers and if drivers for your card are available, activate them. The problem will go away then and you won't lose the splash screen.

---

### Post by surfer on 2010-11-17
thanks for the 'hold down shift'-trick. but... it does not work. all i see is a blinking cursor.

---

### Post by sikander3786 on 2010-11-17
Are you sure your computer is booting from the HDD that contains Ubuntu? Do you see anything related that tells that Ubuntu is trying to boot? The blinking cursor might just be post-Bios...

See in Bios menu if Ubuntu HDD is set as the first boot device.

How many HDDs are there? More than one?

---

### Post by surfer on 2010-11-17
> **sikander3786 said:**
> Are you sure your computer is booting from the HDD that contains Ubuntu? Do you see anything related that tells that Ubuntu is trying to boot? The blinking cursor might just be post-Bios...

How many HDDs are there? More than one?

yes. grub (grub2 in that case) is booting.

i made a fresh install, deleted all other partitions; /boot is the only unencrypted partition, and (with the nomodeset option) ubuntu boots. it's working more or less, just that i do not see anything of grub.

there are 2 HDs, but the second one is encrypted as well and there is nothing in the MBR.

---

### Post by sikander3786 on 2010-11-17
> it's working more or less, just that i do not see anything of grub.

Sorry I couldn't get whole of it. Do you mean that you can boot to the Ubuntu desktop? The only problem is that you don't see the Grub menu :confused: Or what?

---

### Post by surfer on 2010-11-17
> **sikander3786 said:**
> Sorry I couldn't get whole of it. Do you mean that you can boot to the Ubuntu desktop? The only problem is that you don't see the Grub menu :confused: Or what?

yes.

...and that the resolution for the splash screen is unusable (but yes, i can boot without splash).

---

### Post by drs305 on 2010-11-17
On a single OS system, to display the Grub2 menu, edit this line in /etc/default/grub. Add the # symbol, save the file, and update grub:

```
gksu gedit /etc/default/grub
```
> **#** GRUB_HIDDEN_TIMEOUT=0
Make sure GRUB_TIMEOUT is a positive integer.

---

### Post by sikander3786 on 2010-11-17
For tweaking the Grub menu, see this.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

However that Ubuntu purple logo screen sometimes seems ugly on some systems. It is a plymouth problem and I don't know if it can be fixed easily.

Startupmanager has some resolution options.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by drs305 on 2010-11-17
If it's the Ubuntu logo that looks large and ugly on boot, here is a link for 10.04. I've tried it and it did work, but I went back to 'stock' afterward.
[Fix Big and Ugly Plymouth in Ubuntu 10.04 {Lucid Lynx}]("http://linuxhub.net/2010/06/fix-big-and-ugly-plymouth-in-ubuntu-10-04-lucid-lynx/")

There is now apparently a script for 10.10, but I haven't used it:
[Fix ugly plymouth screen on Ubuntu 10.10 using a simple script]("http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/")

---

### Post by surfer on 2010-11-17
ok, so in /etc/default/grub i commented all the GRUB_HIDDEN_* entries and set GRUB_TIMEOUT=10 .

the i ran
```
$sudo update-grub
```
and voilà!

thanks a lot everyone!!

for the plymouth thing i will have a look at the link. thanks again!

---

### Post by surfer on 2010-11-17
yep, also the framebuffer hack worked.

...was there a special reason why you went back to stock?

thanks everyone!

---

### Post by drs305 on 2010-11-17
> **surfer said:**
> yep, also the framebuffer hack worked.

...was there a special reason why you went back to stock?

thanks everyone!

:-)

I try to keep my Ubuntu system as close to the original as possible for troubleshooting the problems of other forum members. 

If I riddle my system with hacks/improvements I'll forget whether the behavior is due to my tweaks or not. 

That's not to say that I don't have modifications. Some are important enough for me that I leave them in, in which case I troubleshoot with a clean VM installation.

So it wasn't that the splash fix was detrimental to my system in any way. Enjoy the visuals the way you have them set up.

Happy Ubuntu-ing !

---

