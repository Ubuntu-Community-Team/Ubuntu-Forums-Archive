---
title: "Dell 131L Brightness Adjuster Problem"
date: 2008-02-17
forum: Dell  Ubuntu Support
---

### Post by digitaladapt on 2008-02-17
I have a Dell 131L, everything works fine, except the Fn +Up/Down to adjust the screen brightness. Using either one will forcibly set the screen brightness to it's maximum. The only way I can change the brightness is before ubuntu boots (at the grub menu) with the Fn + Up/Down. 

I have the priority ati drivers properly installed. 

I've already messed around in gconf-editor > apps > gnome-power-manager, non of the changes ever made an effect. 

I been searching various forums for almost a month with no success, so I figure I would see if anyone else has any ideas.

Thanks in advance for any help you can give.

---

### Post by Qray on 2008-02-17
I have an Inspiron 6400 and after the upgrade to gutsy the Fn +Up/Down stopped working too. So maybe this is not the right solution for you.
For me this [https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/151444](https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/151444) helped (the part with adding the dcop commands in /etc/acpi/video_brightness**.sh; pretty close to the end) ... 
At least partially: I have to execute "sudo /etc/init.d/acpid restart" once every time I reboot (since I mostly go into hibernate, this is not too bad for me... only a little annoying).

Hope this helps you too.

---

