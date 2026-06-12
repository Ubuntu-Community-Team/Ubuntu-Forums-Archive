---
title: "Framebuffer console during boot"
date: 2007-06-18
forum: Desktop Effects &amp; Customization
---

### Post by beebelo on 2007-06-18
This has not worked in Ubuntu since Hoary, and I've never found a Howto or other info.  Why is it that I can select from a list of frame buffer resolutions during Ubuntu *install*, but it's gone after installation.  If I add vga=791 (or similar command) to menu.lst, it doesn't work.  Ubuntu is the only distro I can't do this with--Arch, Sidux, and others I've used--even currently--are capable of it on my system...

I always turn off the boot splash.  I want to see the text scrolling by, and I want it in a small font.  Can someone point me in a direction where I can find the answer to this problem?  Thanks.

---

### Post by RAOF on 2007-06-18
Framebuffer modes work for me.

If you edit your menu.lst manually, you want to make sure to edit the "# kopt=" line (leave it commented), or the "# defoptions" line, then run "sudo update-grub".

If you manually edit the options on the boot line of your various kernels, they'll be wiped out each time menu.lst gets updated (by having a new kernel installed, for example).

---

### Post by beebelo on 2007-06-18
Thank RAOF.  Yes, I was simply adding vga=791 to the boot line in menu.lst, as I've done in other distros.  Tonight I'll try what you said.  

Question:  Does the choice to use (or not use) framebuffer during installation make a difference in the installed system, as far as the modules that get loaded, etc.?

---

### Post by beebelo on 2007-06-19
This time vga=791 works fine.  There are two explanations I can think of:  1) something is different, and 2) I did something different.  If it's because I did something different it could mean that all my previous installations were done without adding a frame buffer option--reason being I thought the option only applied to *during* installation ... Anyway, alles gut.

---

### Post by RAOF on 2007-06-20
> **beebelo said:**
> ...
Question:  Does the choice to use (or not use) framebuffer during installation make a difference in the installed system, as far as the modules that get loaded, etc.?

I believe that if you add the vga= option when you install, it should be automatically added to your menu.lst, but that's the only difference that it will make.  It won't change anything else.

---

### Post by Qu4k3R on 2007-06-28
Framebuffer mode does not works for me :'(
After X11 session starts-up, I can no longer see what's happening to terminals (1 to 6)
I had posted one topic about that, but I cannot get it working.
I am not the only one to have this bug.

I have tried to change vga options into /boot/grub/menu.lst and also changing defoptions.
I had also tried to update-grub. It simply does nothing..


my topic is this:
[http://ubuntuforums.org/showthread.php?p=2866358](http://ubuntuforums.org/showthread.php?p=2866358)

Could anybody help me out?
Thanks in advance.

---

