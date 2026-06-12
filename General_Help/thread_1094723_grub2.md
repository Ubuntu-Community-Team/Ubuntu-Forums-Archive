---
title: "grub2"
date: 2009-03-12
forum: General Help
---

### Post by charlescarroll1 on 2009-03-12
I installed grub2 without realizing that it is considered unstable.  After I installed it, the grub menu loads up that looks like this:

> 
Chainload into Grub 2
___________________________________________________________
When you have verified Grub 2 works, you can use this command to complete the upgrade: upgrade-from-grub-legacy
___________________________________________________________
Debian GNU/Linux, kernel 2.6.27-11-generic
Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
Debian GNU/Linux, kernel memtest 86+
Other operating systems:
Windows XP Professional
When I seleced "Chainload into Grub 2", I got the following error message:

> Error 11: Unrecognized device string
Press any key to continue...

Damn.  It didn't work, so I tried to boot up Ubuntu regularly, and I got the same error message.  I receive the same error message when I select anything other than Windows XP Professional.  

Is there any possible way of fixing this?  I read somewhere that I could use a Live CD, and enter the following command in a terminal:

> sudo apt-get install grub

This reason why I don't think this will work in the first place is because when I boot from a Live CD, I do not get some drivers necessary for my laptop to operate, most importantly my WiFi adapter.  I assume that this command will attempt to install grub off the internet and I do not have access to a direct connection, so you see my problem.

Does anyone have any recommendations or suggestions at all?

---

### Post by Herman on 2009-03-12
It's because Ubuntu's GRUB (legacy) uses the uuid command instead of the older root command with the (hd0,1) syntax for designating the Ubuntu partition. GRUB2 doesn't support the uuid command (yet).
Switch to the root command and the (hd0,1) type syntax in your GRUB menu and you should have no more trouble.

Regards, Herman :)

---

### Post by charlescarroll1 on 2009-03-12
> **Herman said:**
> It's because Ubuntu's GRUB (legacy) uses the uuid command instead of the older root command with the (hd0,1) syntax for designating the Ubuntu partition. GRUB2 doesn't support the uuid command (yet).
Switch to the root command and the (hd0,1) type syntax in your GRUB menu and you should have no more trouble.

Regards, Herman :)

Sorry for asking Herman, but how might I do that exactly?

---

### Post by Herman on 2009-03-13
When upgrading from GNU GRUB 0.97 to GRUB2 (or currently 1.96), if your existing /boot/grub/menu.lst file has the uuid command which replaced the root command, you need to revert to the root command.

You need to open your /boot/grub/menu/lst file as 'root' (administrator), with this command, ```
gksudo gedit /boot/grub/menu.lst
```Then you need to edit the file and save the changes before closing.
For example, change this:
```
[title]("http://users.bigpond.net.au/hermanzone/p15.htm#title_")    Ubuntu, kernel 2.6.20-15-generic
[COLOR=Red]**[uuid]("http://users.bigpond.net.au/hermanzone/p15.htm#root")     fe7bf845-7ce9-4733-b6de-f70f2b62076d**[/COLOR]
[kernel]("http://users.bigpond.net.au/hermanzone/p15.htm#kernel")   /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
[initrd]("http://users.bigpond.net.au/hermanzone/p15.htm#initrd")   /boot/initrd.img-2.6.20-15-generic
quiet
[savedefault]("http://users.bigpond.net.au/hermanzone/p15.htm#savedefault")
```to this:
```
[title]("http://users.bigpond.net.au/hermanzone/p15.htm#title_")    Ubuntu, kernel 2.6.20-15-generic
**[COLOR=Blue][root]("http://users.bigpond.net.au/hermanzone/p15.htm#root")     (hd0,1) [/COLOR]**  # or alter for whatever hard disk and partition number you have
[kernel]("http://users.bigpond.net.au/hermanzone/p15.htm#kernel")   /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
[initrd]("http://users.bigpond.net.au/hermanzone/p15.htm#initrd")   /boot/initrd.img-2.6.20-15-generic
quiet
[savedefault]("http://users.bigpond.net.au/hermanzone/p15.htm#savedefault")
```Where: '(hd0,1) is the applicable hard disk and partition number in GRUB terms for your Ubuntu partition.
If you're not sure, run 'sudo fdisk -lu', or open Gnome Partition Editor from your Ubuntu Live CD and take a look.
You will see your Ubuntu partition described with a number like '/dev/sda2' or similar. 
You can convert that to GRUB terms by looking here, [A Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System").

---

### Post by charlescarroll1 on 2009-03-14
Your solution worked.  Thanks for the help, Herman! :D

---

### Post by Herman on 2009-03-14
:D Okay, cool! You're most welcome and thank you for the feedback. 

Do you think you'll keep using it the way it is now or revert to GRUB legacy, or do you want to upgrade to GRUB 1.96?

GRUB 2  (or rather, 1.96 at present), is booting my operating systems okay. 
It works well enough as a boot loader just for plain old regular everyday operating system booting.
If we need to do anything fancy at the command line interface or in the grub-emu it's not as good as GRUB legacy at this stage of development.
'Grub-emu' is short for 'Grub Emulator' and it seems to be the new replacement for the grub shell that you get with legacy GRUB when you type 'sudo grub' in a terminal. Grub-emu has a lot of commands that don't seem to be fully functional yet, at least not the last time I tried them all out. I could get some commands to work but others didn't seem to do anything. The command line mode wasn't much better. The most important functions are there though.

One thing I like about it is the way it automatically detects other operating systems and adds them to the boot menu when we run 'sudo update-grub'.

Another thing that's impressive about GRUB 1.96 is the way it's able to display nicer splashimages than GRUB 0.97 (legacy). There are some splashimages made for GRUB2 in the repositories that you can download and install, or we can easily make our own. Any .png or .tga image seems to work alright. GRUB 2 will be much prettier than GRUB legacy.

I think there is still some work for the programmers to do before GRUB2 will be functionally as useful as GRUB legacy though.

---

