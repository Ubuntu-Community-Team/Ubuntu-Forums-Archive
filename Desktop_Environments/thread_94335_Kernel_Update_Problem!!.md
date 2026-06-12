---
title: "Kernel Update Problem!!"
date: 2005-11-23
forum: Desktop Environments
---

### Post by tomwell on 2005-11-23
Hi, 

I performed the kernel upgrade from 2.6.12.9 to 2.6.12.10 today, since then, not only have i had extra options with regards to booting using the "GRUB" (i get to choose between 2.6.12.9 and 2.6.12.10 kernels..+ my usual XP partition...

But My boot up process is extremely slow!!! 

Everything goes normally except that when the computer finsihes loading it goes to the flash screen (i think its called that) and stays there on a brown screen... with Metacity file something icon in the middle of the screen...! The only wasy for the rest of GNOME to load up is if i do "Ctrl + Alt + Del" and then it still takes a while to load the rest of the GNOME interface...

What do you guys think is wrong??
there is another similar thread with regards to the GRUB prob but no one seems to be experiencing the slow boot up prob...

[http://www.ubuntuforums.org/showthread.php?t=94075](http://www.ubuntuforums.org/showthread.php?t=94075)

All help really apreciated!!!!!

Peace 

Tom

---

### Post by Xian on 2005-11-23
[QUOTE=tomwell]Everything goes normally except that when the computer finsihes loading it goes to the flash screen (i think its called that) and stays there on a brown screen... with Metacity file something icon in the middle of the screen...! The only wasy for the rest of GNOME to load up is if i do "Ctrl + Alt + Del" and then it still takes a while to load the rest of the GNOME interface...[/QUOTE]
Just to clarify...are you saying that if you go back and boot into the previous kernel that this trouble loading Gnome does not take place?

---

### Post by tomwell on 2005-11-23
Well yes when i go back into booting with the previous kernel i dont get any probs....

But i cant still load up the computer by booting with the new kernel, it just takes forever and i need to use Ctrl + Alt +Del...

Peace 

Tom

---

### Post by dcstar on 2005-11-23
[QUOTE=tomwell]Well yes when i go back into booting with the previous kernel i dont get any probs....

But i cant still load up the computer by booting with the new kernel, it just takes forever and i need to use Ctrl + Alt +Del...

Peace

Tom[/QUOTE]
The new kernel obviously does not like your setup, you may be able to see something in the log files to shed some light on the problem, otherwise just use the previous kernel.

---

### Post by tomwell on 2005-11-23
Hey Dc star,

Thanks for replying, How would i go about looking at the log?

And should i remove the new kernel from my system? is that possible?? Is this a common thing that ones machine does not accept a kernel update??

Thanks 

Peace 

Tom

---

### Post by dcstar on 2005-11-23
[QUOTE=tomwell]Hey Dc star,

Thanks for replying, How would i go about looking at the log?

And should i remove the new kernel from my system? is that possible?? Is this a common thing that ones machine does not accept a kernel update??
.......[/QUOTE]
1/ Applications-System Tools-System Log and then Open "syslog" and "messages"

2/ Easiest thing to do is just comment out the new kernel in /boot/grub/menu.lst, you can remove it via Synaptic - but you will get nagged to update it again!

When another kernel update (eventually) appears, install it and see if it is any better than this one.

---

### Post by fimbulvetr on 2005-11-23
you can view most of your kernel logs with the command with:

dmesg

Paste that here.

Also, paste /var/log/Xorg.0.log here just for good measure,

---

### Post by tomwell on 2005-11-23
I have commented the old kernel out and it has solved the problem...

GOD knows why...!!!

Thank you all for your help...!!!!

Peace and goodnight...!! (4:11am)<--- LMAO ;o)

Tom

---

