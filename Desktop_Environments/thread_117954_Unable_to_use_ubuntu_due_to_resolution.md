---
title: "Unable to use ubuntu due to resolution"
date: 2006-01-15
forum: Desktop Environments
---

### Post by Invictre on 2006-01-15
i have installed (and re-installed twice after formatting the drive) ubuntu onto a virtual machine and i am trying to use it but after the installation process, i boot ubuntu and it comes up on a huge resolution (absoloutely huge) that my monitor cannot support. it is completely unreadable. could someone help me please.

screenshots attached in PNG format

---

### Post by dcstar on 2006-01-15
[QUOTE=Invictre]i have installed (and re-installed twice after formatting the drive) ubuntu onto a virtual machine and i am trying to use it but after the installation process, i boot ubuntu and it comes up on a huge resolution (absoloutely huge) that my monitor cannot support. it is completely unreadable. could someone help me please.

screenshots attached in PNG format[/QUOTE]
Edit /etc/X11/xorg.conf

---

### Post by Invictre on 2006-01-15
i am reasonably new to ubuntu. i managed to find the command prompt and entered "configfile /etc/X11/xorg.conf" (without "") but the screen just went back to the initial screen when you first open the command prompt... no editor screen or anything. was i missing comething in the command??

---

### Post by dcstar on 2006-01-15
[QUOTE=Invictre]i am reasonably new to ubuntu. i managed to find the command prompt and entered "configfile /etc/X11/xorg.conf" (without "") but the screen just went back to the initial screen when you first open the command prompt... no editor screen or anything. was i missing comething in the command??[/QUOTE]
I have no idea what "configfile" is, use either vi or nano to edit it (probably nano would be better).

An alternative is:

sudo dpkg-reconfigure xserver-xorg

and manually set the maximum resolutions.

---

### Post by Invictre on 2006-01-16
sorry, "configfile" is something to do with GRUB...

---

### Post by alaskancaveman on 2006-01-16
[QUOTE=Invictre]i have installed (and re-installed twice after formatting the drive) ubuntu onto a virtual machine and i am trying to use it but after the installation process, i boot ubuntu and it comes up on a huge resolution (absoloutely huge) that my monitor cannot support. it is completely unreadable. could someone help me please.

screenshots attached in PNG format[/QUOTE]


try editing virtual pc setting or login if possible click system then preferences the screen resolution.  That doesn't make any sense though ive seen it work fine before with no problems.  You could check your graphics drivers in windows.  If that doesn't work you could also try vmware which works well plus its not owned by ms.  Its best to just do a full install from scratch without another os.  Try running the live cd to get use to using ubuntu, it might help

---

### Post by Invictre on 2006-01-16
David:
how am i ment to get into nano since when the shell is booted it goes to an unreadable resolution??? am i ment to press "escape" and go into grub to the command line or am i ment to edit the boot sequence stuff...?

alaskancaveman:
Virtual pc isn't having any implication on the display settings of the virtual computer, i mentioned in the original post that i can login... past that i can't read a thing. i've included another screenshot

---

### Post by Invictre on 2006-01-16
on the advice of alascancaveman, i downloaded a copy of VMWare and ran the preinstalled version of ubuntu 5.11 (which saves a heck of a lot of time - and have a descent download speed when you use torrenting.) using that i got the copy of ubuntu on MS Virtual PC to run.

here's the bad news. in MS Virtual PC, it thinks it's running in 640*480 mode and it's only ledgible in black and white (as opposed to VMware which i think i'll use for ubuntu from now on. the only downside is that i don't know the root account password, so i can't change many of the settings.) 

screenshots from MS Virtual PC enclosed

---

### Post by dcstar on 2006-01-16
[QUOTE=Invictre]
.......
here's the bad news. in MS Virtual PC, it thinks it's running in 640*480 mode and it's only ledgible in black and white (as opposed to VMware which i think i'll use for ubuntu from now on. the only downside is that i don't know the root account password, so i can't change many of the settings.) 
.......[/QUOTE]
The Ubuntu "root" account password should initially be the same as the user password you use for "sudo".

But the root account is disabled by default, do a forum search for the (many) articles on how to enable it (if you like).

---

### Post by winaje on 2006-01-16
Greetings all, I'm a noob to Ubunut and Linux.  I'd like to thank the support community, as I've been able to sort out a couple of things with the forums, especially screen resolution.

Thanks heaps for your help...

---

