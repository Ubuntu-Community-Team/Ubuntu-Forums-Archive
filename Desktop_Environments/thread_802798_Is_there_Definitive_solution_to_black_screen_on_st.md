---
title: "Is there Definitive solution to black screen on startup"
date: 2008-05-21
forum: Desktop Environments
---

### Post by John1927 on 2008-05-21
Is there a definitive solution to the black screen that appears on start-up?

I am using xubuntu 8.04, and practically every boot-up I get the black screen appearing.

I resolve by boot-up in repair mode and that allows me to at least log-on. However the problem keeps reappearing on the next boot-up.

I switch th Linux to avoid the computer crashes I was getting, but now..... seems to be a similar problem with xubuntu.

Hope a definitive solution exist.

Thanks.

---

### Post by Nythain on 2008-05-21
gksu gedit /boot/grub/menu.lst

down at the bottom there's a line that looks like
kernel (lots of space) vmlinuz=blahblahblah root=blahblahbla ro quiet splash

delete teh quiet and splash
save and reboot... basically removing usplash...

there's also a thread on here about blank or black tty's and how to fix that by enabling the correct framebuffer, following that guides advice should also fix your problem, and you should be able to re-enable usplash (hopefully)

---

### Post by John1927 on 2008-05-22
Thanks,

---

### Post by John1927 on 2008-05-22
> **Nythain said:**
> gksu gedit /boot/grub/menu.lst

down at the bottom there's a line that looks like
kernel (lots of space) vmlinuz=blahblahblah root=blahblahbla ro quiet splash

delete teh quiet and splash
save and reboot... basically removing usplash...

there's also a thread on here about blank or black tty's and how to fix that by enabling the correct framebuffer, following that guides advice should also fix your problem, and you should be able to re-enable usplash (hopefully)
Well I checked gksu gedit /boot/grub/menu.lst and reference to splash was removed.  However the problem of the black screen remains.

any other suggestions that I could try... it is getting a little difficult having to repair packages on each boot-up?

---

### Post by VMC on 2008-05-22
> **John1927 said:**
> Well I checked gksu gedit /boot/grub/menu.lst and reference to splash was removed.  However the problem of the black screen remains.

any other suggestions that I could try... it is getting a little difficult having to repair packages on each boot-up?Sounds like you have to problems. If you remove the quiet & sqlash to something like below:

kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=d8533154-cef1-4cce-a823-9f3f74aab65b ro #quiet splash

Then when you boot up, do you see at least a screen or two of data fly by?
Also mine stops shortly and I have to press Alt+F1 for data to keep going.

But at any rate this has nothing to do with repairing packages??

---

### Post by John1927 on 2008-05-22
> **VMC said:**
> Sounds like you have to problems. If you remove the quiet & sqlash to something like below:

kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=d8533154-cef1-4cce-a823-9f3f74aab65b ro #quiet splash

Then when you boot up, do you see at least a screen or two of data fly by?
Also mine stops shortly and I have to press Alt+F1 for data to keep going.

But at any rate this has nothing to do with repairing packages??
Everything looks fine as the system is booting and I see no errors from the listing on screen.

However, when the system is about to start xfce Windows, nothing happens and the screen stays black.

Below is a section taken from menu.lst

> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1c23f031-9b6b-499c-bdb9-eb7eab56c6e1 ro vga=771
initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

---

