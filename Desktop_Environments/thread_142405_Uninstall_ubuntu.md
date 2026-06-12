---
title: "Uninstall ubuntu"
date: 2006-03-10
forum: Desktop Environments
---

### Post by FISHERWINEMAN on 2006-03-10
I`ve installed the full version and I should have installed the Live.
Can anyone help me uninstall please.
You will be saving my life at home.

---

### Post by psusi on 2006-03-10
[QUOTE=FISHERWINEMAN]I`ve installed the full version and I should have installed the Live.
Can anyone help me uninstall please.
You will be saving my life at home.[/QUOTE]

That doesn't make any sense.  You don't "install" the livecd, that's the entire point; it just runs directly from the cd.  

I assume that your question is how to uninstall ubuntu. The answer to that is reinstall another OS.

---

### Post by FISHERWINEMAN on 2006-03-10
Thanks for your reply. I installed the full version by accident and now Ubuntu is dominant and I can`t install win 98 at all, Oh accept it appears as a folder in ubuntu.

---

### Post by MerZo on 2006-03-10
If you havn't overwritten the Windows 98 partition you might be able to choose it from grub? Else, like the other poster said. Reinstall.

---

### Post by astyanax on 2006-03-10
When you go to reinstall Ubuntu, check to see what partitions are available.  If there are no ntfs or fat32 partitions, then you have deleted them and overwritten your windows installation with Ubuntu.  Otherwise, you should be able to install grub and setup a dual boot between Ubuntu and Windows.

---

### Post by FISHERWINEMAN on 2006-03-11
As anovice I don`t know how to do most things so words like "grub" and "see what partitions etc" are not understood.
If someone has the patience can they help me perform the task.

---

### Post by dermotti on 2006-03-11
Heheh this is gonna be rough :-)

---

### Post by munga_bill on 2006-03-11
Well here's how to uninstall it [http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)
But why don't you learn how to use it and keep it? If you only installed it on a relatively small amount of hard drive space it will do you a lot of good. Think of it- a spare operating system that is immune from spyware and viruses and crackers, and can do all kinds of things your other system can't do. All you need to do is learn how to boot (start up) in whichever system (Windows or Ubuntu) you choose and you'll be okay.

---

### Post by glug101 on 2006-03-11
OK, I think the posters in here are being a little bit rough.  Yes, the orignal post didn't make much sense, but the original poster didn't know any better.  My guess, he meant to download the livecd, downloaded the installcd by mistake, and (like so many windows users before him) followed the prompts.  Does that sound about correct?

The easiest solution to this issue would be to configure grub to prompt for a boot to either ubuntu or windows.  That way FisherWineman can have the Ubuntu experience he was looking for in the first place, and he can have windows installed also. (and keep his family happy;) )  Fortunately, if there is a folder for windows on your desktop, it is highly likely that all of your windows files are intact.  You just can't boot windows (yet).

Unfortunately, I'm not very knowledgable about grub (the boot manager, or the program that decides which operating system Windows/Ubuntu your computer starts when turned on).  Basically, I'm part of the old guard who started out using lilo (another boot manager) and hasn't bothered to learn grub (I really should).  Here is a how-to guide that seems to be a good description of how to configure grub.  (just remember, you don't need to install grub to use it ;) )

[http://www.tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html#AEN54](http://www.tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html#AEN54)

Hope this helps!  If you have any problems with the manual, feel free to post here.

Edit:  Forget my link, munga_bill's is much better.  It has pictures and it's much more specific to Ubuntu.  But configuring grub by the description at that link should be all that you need to get both windows and Ubuntu working.

---

### Post by Zyphrexi on 2006-03-11
so what you want to do is open up a terminal

click Applications -> Accessories -> Terminal

then type 'cat /boot/grub/menu.lst'

and if you scroll up in the terminal select everything, copy it and paste it to here, we can take a look and see where your windows drive is.

A way to edit the grub bootloader (don't do this just yet)

is to type (again in a terminal) 'gksu gedit /boot/grub/menu.lst'

when the prompt pops up, type in your root password, and you'll be able to edit it.

EDIT::

er i just realized what i wrote lol. I mean, post the output from
/etc/fstab

so 'cat /etc/fstab' would be the command

---

### Post by chettyk on 2006-03-11
Fisherwineman, the first thing you need to do is check whether in installing Ubuntu you have overwritten Windows 98. The simplest way for you to do that may be to reboot the computer. As soon as the computer finishes the initial boot-up tests and before Ubuntu begins loading, a menu will appear (as I recall, it is white letters on a black background). That is the menu of Grub, which handles the booting of multiple operating systems. The menu will list all the booting possibilties Grub is set to handle on your computer. If Ubuntu has not overwritten your Windows system, Windows will be one of the options listed in that menu. If, on the other hand, Ubuntu has overwritten your Windows system, you will see only the Ubuntu boot options in the menu. I suggest you post the Grub menu options you see.

---

