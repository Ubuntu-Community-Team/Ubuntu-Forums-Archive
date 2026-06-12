---
title: "Ubuntu Dead - Several Questions"
date: 2009-02-22
forum: General Help
---

### Post by den160593 on 2009-02-22
Hi,

I tried to change my screen resolution on Ubuntu, but afterwards it just died (on Ubuntu start up I get multi-coloured screen of death). So I have two questions.

Firstly, how can I return Ubuntu to it's defaults without graphically entering Ubuntu (or from my second OS with Windows XP if possible).

Secondly, can I make Windows XP my default load for now until I can fix ubuntu? Again, Ubuntu doesn't work. So how can I get it to work?

-Den

---

### Post by ghd on 2009-02-22
If you see the grub boot menu you should be able to escape (esc key) the default boot and choose windows. To make it the default for now you could 
a) boot into single user mode (add -s to the kernel boot line)
b) boot from the ubuntu boot cd and then edit the grub config file
/boot/grub/menu.lst and change the "default" line to match the number of the windows boot option.

---

### Post by den160593 on 2009-02-22
Ah ok, I'll try that. Also is there a way to restore Ubuntu to it's defaults?

---

### Post by paydaydaddy on 2009-02-22
reboot and pay close attention to the screens as the boot process begins. I forget exactly what it says, but it is something like "loading linux kernal" and a 3 second count down. Hit escape within the 3 seconds and you will get a menu from which you can choose recovery mode. Highlight your choice using the up/down arrows on your keyboard and hit enter. A bunch of text will scroll by and then another menu will load. Choose xfix. This should allow you to reboot into a usable state. Tweek settings as needed.

---

### Post by den160593 on 2009-02-22
Hi, that didn't work. Nothing changed after I hit x-fix :( Any other suggestions?

---

### Post by geirha on 2009-02-22
When you boot normally, does the login screen look right? and then when you log in, you the screen gets scrambled?

---

### Post by den160593 on 2009-02-22
No, i can't get to the login in screen. I get to the GRUB loader, soo as I select it goes haywire.

Windows XP works fine though

---

### Post by geirha on 2009-02-22
Try booting without the splash screen. 

1. Select the first ubuntu entry in the grub menu and hit **e** to edit it. 
2. Select the line starting with "kernel" and hit **e** to edit it.
3. At the end of the line you should see the two words quiet and splash. Remove them, and hit enter.
4. Hit **b** to boot with this modification.

Does that have any effect?

---

### Post by den160593 on 2009-02-23
Hi I tried your advice geirha but it still doesn't work. For some reason it looks like a stuffed up, multicoloured (predominently Blue, but all streched and un-responsive) Windows XP theme - despite the fact that I'm launching Ubuntu.

Any other ideas? Please, I really want to try get this to work.

---

### Post by den160593 on 2009-02-24
Anyone?

---

### Post by Stephen50191 on 2009-05-01
Hey, I'm having the same problem with jackalope.  It goes into the grub boot loader then as it tries to start ubuntu it'll show a messed up, multicolored version of my desktop picture.  Then it will show multiple slides of the loading screen and its still that messed up,multicolored screen.  I can run XP just fine.  If anyone knows anyway to remedy this problem or has an idea please help.

:confused:

---

