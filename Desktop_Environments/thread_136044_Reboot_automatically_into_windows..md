---
title: "Reboot automatically into windows."
date: 2006-02-25
forum: Desktop Environments
---

### Post by Pe2 on 2006-02-25
I'm currently running a dual box with ubuntu and windows xp.

I've used Suse and KDE erlier, and had this option to reboot directly into windows/Suse.(Without having to select windows/suse in the Grub menu)


Is it possible to add this function into Ubuntu with gnome aswell?

---

### Post by PrivatePickle on 2006-02-25
The following thread showed me how to change this.

[http://www.ubuntuforums.org/showthread.php?t=133031&highlight=change+grub+priority]("http://www.ubuntuforums.org/showthread.php?t=133031&highlight=change+grub+priority")

---

### Post by aysiu on 2006-02-25
If you mean that you can select which to boot into *before* rebooting/booting (i.e., telling Ubuntu "The next time I boot into this computer, boot Windows, but ordinarily I want Ubuntu"), then I don't think it can be done simply.

If you just mean you want to change what the *default* operating system you boot into is, then follow PrivatePickle's link.

---

### Post by ranf on 2006-02-25
```
grub-reboot <entry>
```

Not much info in the man page on how <entry> has to be given.

---

### Post by Pe2 on 2006-02-26
Yes aysiu. I'd like to tell ubuntu where i want to boot before i reboot. 

I tried to use grub-reboot, but can't say i figured out how to use it.

---

### Post by PrivatePickle on 2006-02-27
I found this and it worked for me,

> The way to do this is to use the grub-reboot command. grub-reboot requires the entry number you wish to set as the temporary default to us. Using the above menu.lst, we’d simply issue grub-reboot 1 to try out the 2.6.8-2-686 kernel. If the kernel fails to boot, we can simply powercycle the system and the server will boot the normal default 2.4.18-sb kernel (entry 0). If everything works just fine, then you will be able to edit the menu.lst file after the system is back online and move the 2.6.8-2-686 entry to be the first entry in the file and grub will use it by default from here on out.

After running grub-reboot you will be asked if you would like for grub to reboot your system now. If you answer yes, the system will be shutdown properly. If you answer no, you will be returned to the root command prompt and you can reboot the system any time later by running reboot or shutdown -r now as root.

This was quoted from the following web page.

[http://www.spoonix.org/blog/howtos/safely-testing-new-kernels-on-remote-systems/]("http://www.spoonix.org/blog/howtos/safely-testing-new-kernels-on-remote-systems/")

Example:  Windows xp is the 10th entry listed in /boot/grub/menu.lst so I typed

sudo grub-reboot 10

Enter password if necessary then "y" or "n" depending on if you wish to reboot now or later.

I am fairly new to linux, does anyone know if you can make a script "forgive me if I am not using the proper term" that can be executed from a menu using this command so you don't have to open the console and type it in each time?

---

### Post by Pe2 on 2006-03-01
Thank you! Works like a charm.

But yes, as you said, it would be nice to have a little desktop menu or program that would do this without using the console!

---

### Post by florizs on 2006-03-01
> Thank you! Works like a charm.

But yes, as you said, it would be nice to have a little desktop menu or program that would do this without using the console!


hmm maybe i'll give it a try, I've been wanting to do some scripting lately.

---

