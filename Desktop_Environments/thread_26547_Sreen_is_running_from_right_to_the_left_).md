---
title: "Sreen is running from right to the left :)"
date: 2005-04-13
forum: Desktop Environments
---

### Post by la-karaviro on 2005-04-13
Hi,

at the boot, after it initializes hotplug, the screen is running from right to left and its squized to the bottom, but as soon as it starts GDM "everything" is again fine

that happened after i did xorgconf  and fglrxconfig

i have a ATI Radeaon card and i installed the ATI driver 8.12.10 i386 (is there a 686?)

does anybody know how to fix that, or with what exactly the failure is connectet,
what does it starts after the hotplugs, the X server? and why he can display gdm and gnome but not properly the console and terminal before?

if you have at least one answer to the questions above, please help me, if not, its suerly allowed to say just hellou :) but taht is called spam

im still a newbie, so have mercy :) have a great day

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=la-karaviro]Hi,

at the boot, after it initializes hotplug, the screen is running from right to left and its squized to the bottom, but as soon as it starts GDM "everything" is again fine

that happened after i did xorgconf  and fglrxconfig[/QUOTE]

Being a nVidia user and not an ATI user, I'm taking a shot in the dark, but I think that the FireGL drivers you installed (especially if fglrx comes with kernel modules like nvidia's drivers do) might be interfering with the kernel's console display driver. Does your friend have a VESA framebuffer console, or is he using the old-fashioned console?

---

### Post by la-karaviro on 2005-04-13
hm i think he uses the old fashioned one,
but you brought me on a idea,
i put in the grub config the vga=791 parameter in the kernel colone, now its all pretty and dont flickers

thank you for your help and try 
till then

---

