---
title: "Want to uninstall Ubuntu!!! (No knowledge about Linux)"
date: 2006-01-16
forum: General Help
---

### Post by Mattiaz on 2006-01-16
First of all I want to say that Ubuntu is a great initiative. But after I installed Ubuntu on my fathers computer, because he had forgotten the password and I couldn't reinstall windows without the password. I've come to the conclusion that I can't handle it. I don't understand how the terminal works or anything. Because of that, I now need help uninstalling Ubuntu and reinstalling Windows. The best thing would be "step by step" instructions.
:confused: 
If anyone could send a link to my email (Mashon02@student.umu.se) with some instructions regarding this problem or help me themself, I would really appreciate it. :smile: 

Thanx and best wishes to the whole Ubuntu Community.
/Mattias

---

### Post by aysiu on 2006-01-16
[This link](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458) may help.

---

### Post by Xorg on 2006-01-16
Well, I've uninstalled, and reinstalled (K)ubuntu many times. (yeah, I had reasons. ;))

I simply used my Knoppix CD to boot into Knoppix (what else would you do with it?) and then I formatted my Linux partition. Then I booted into the Windows Recovery Console (Really just DOS) and type fixmbr (this made a new master boot record which erased GRUB - therefore completing my uninstallation)

However, if you aren't dual booting (doesn't sound like you are) then I'd just use the Windows CD to install it as you would if Ubuntu weren't installed. Simply tell it to format the HDD, and Ubuntu will be gone.

Look [here](http://www.linuxforums.org/forum/showthread.php?p=285947) if you don't understand what I said. :p

EDIT: Beaten by a good bit. :| Well, that's what I get for typing it all. :p

---

### Post by Jaygo333 on 2006-01-16
[QUOTE=Mattiaz]First of all I want to say that Ubuntu is a great initiative. But after I installed Ubuntu on my fathers computer, because he had forgotten the password and I couldn't reinstall windows without the password. I've come to the conclusion that I can't handle it. I don't understand how the terminal works or anything. Because of that, I now need help uninstalling Ubuntu and reinstalling Windows. The best thing would be "step by step" instructions.
:confused: 
If anyone could send a link to my email (Mashon02@student.umu.se) with some instructions regarding this problem or help me themself, I would really appreciate it. :smile: 

Thanx and best wishes to the whole Ubuntu Community.
/Mattias[/QUOTE]

Frankly, What is annoying you with the terminal. I installed Ubuntu myself back in December and had the same problems you did with the terminal. I just came here to ubuntuforums and they've helped me out a lot. Just come here and ask any question, any question at all. And I guarantee you, somebody will anser you back. Its worked for me so far.
I still lost with the terminal, try:
[http://ubuntuforums.org/showthread.php?t=73885&highlight=intro+terminal](http://ubuntuforums.org/showthread.php?t=73885&highlight=intro+terminal)
It helped me to understand the terminal a-lot. Try It

:):h34r: Jaygo333 :):h34r:

---

### Post by Xorg on 2006-01-16
Well, since his dad forgot the password, here's something that may help 

When GRUB loads, scroll down and boot into recovery mode. This will give you a root shell.  Type startx at the shell. This will load your GUI. Then you can go to System Settings > Users and Groups and change his password again.

---

### Post by Sef on 2006-01-16
What don't you understand?  We'll be more than happy to help you if you just ask us here.

Here's a couple of places to start reading:

1)[http://easylinux.info/wiki/Ubuntu]("http://easylinux.info/wiki/Ubuntu")

2) [https://wiki.ubuntu.com/UserDocumentation]("https://wiki.ubuntu.com/UserDocumentation")

To Dual Boot with XP and Ubuntu:

3) [http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

There is a learning curve to Linux, but if you don't want to do it, then just reinstall Windows and it write to the whole partition.  (I hope you do take some time to learn it.

---

### Post by GreyFox503 on 2006-01-16
[quote=Xorg]Well, since his dad forgot the password, here's something that may help 

When GRUB loads, scroll down and boot into recovery mode. This will give you a root shell.  Type startx at the shell. This will load your GUI. Then you can go to System Settings > Users and Groups and change his password again.[/quote]

I think that Mattiaz meant that his father forgot his Windows password.

---

### Post by HJThis on 2006-01-16
Hello,To all

@Mattiaz

Well as you can see there are tons of help for
you here just ask

as for the Windows password no need to do a
reinstall of XP there is a way around this

Best of luck

---

### Post by gnuconvert on 2006-01-16
Mattiaz

Ubuntu helped me save the data on my Windows computer from a similar fate (forgotten Windows password). I had window 2000 with lots of data that I couldn't access because I didn't remember the password. I started to rescue the data chunk by chunk using an Ubuntu live CD. Then I actually installed Ubuntu as a dual boot, and that made life much easier. I probably ended up salvaging the data the hard way, by archiving the windows data over to the Linux side of the disk and out via memory stick or burning CDs. I saw some easier ways to do it on this forum, if you search around a bit. Bottom line is, it worked, and my old windows data is now safe and accessible. This all assumes that you set up Ubuntu for dual booting (Windows and Ubuntu) using GRUB (the default installation option).

I am not sure, though, how getting Ubuntu off your PC helps you. You're still going to have a windows machine that you can't get into because of the forgotten password. At least if you keep Ubuntu, you can rescue the data on the Windows side of your disk. Besides, with a little perseverence, you may end up liking Ubuntu. It's a little tricky at first, but after a while you start to love it. Like someone else said, if you run into a problem, post it on the forum. There are lots of power users that can help. My first post got an answer in 1 minute flat!

gnuconvert

PS. I reread your post and was thinking that if you don't care about any of your data on the computer, you should be able to just reinstall windows right over the Ubuntu installation that you have. I suspect that the problem with windows asking for a password to reinstall could be due to trying to reinstall windows from an upgrade CD rather than from the original CD. If you originally set up your computer with an earlier version of windows, and then upgraded to a later version of windows, you will probably need to go back and install the original version of windows first, and then install the upgraded version of windows. It's been a while since I went through that procedure, but I think it should work. I don't think that you will need the forgotten password to do this. You WILL need the product keys (usually about 25 - 30 letters and numbers in about 5 or 6 groups) written on the Windows CD packages, however. 

This is all major surgery though, and you may want to wait to see any other replies to your post before doing it.

Good luck.

---

### Post by goatflyer on 2006-01-16
I can vouch for the good replies from the forum to help you answer your Ubuntu questions.  It really is one of the best reasons to like this Linux distro better than the others.

Hope you decide to keep it.

---

### Post by Mattiaz on 2006-01-17
Thanks for all the answers. The primary probem I have is that I've tried to boot the computer with the WinXP SP2 cd. But everytime I try to use it, and also when I try to boot via cd-rom using the Ubuntu-cd, it just skip it and goes directly to password screen and the OS. As I understand from some of the answers, everybody haven't understood that I ONLY have Ubuntu on the computer now.  Should I maybe format the disk? And if so, how do I do that?

Thanx again
/M

---

### Post by _LOphT on 2006-01-17
i dont think you should uninstall, learn...knowledge is power :)

---

### Post by Thirsteh on 2006-01-17
[QUOTE=Mattiaz]First of all I want to say that Ubuntu is a great initiative. But after I installed Ubuntu on my fathers computer, because he had forgotten the password and I couldn't reinstall windows without the password. I've come to the conclusion that I can't handle it. I don't understand how the terminal works or anything. Because of that, I now need help uninstalling Ubuntu and reinstalling Windows. The best thing would be "step by step" instructions.
:confused: 
If anyone could send a link to my email (Mashon02@student.umu.se) with some instructions regarding this problem or help me themself, I would really appreciate it. :smile: 

Thanx and best wishes to the whole Ubuntu Community.
/Mattias[/QUOTE]

Type this to wipe your MBR (partition table):
sudo dd if=/dev/zero of=/dev/hda1 bs=512 count=1

Now that your partition table is erased, Windows won't have problems partioning and finding your disk. Reboot and install Windows.

---

### Post by peteyp666 on 2006-01-17
[QUOTE=Mattiaz]Thanks for all the answers. The primary probem I have is that I've tried to boot the computer with the WinXP SP2 cd. But everytime I try to use it, and also when I try to boot via cd-rom using the Ubuntu-cd, it just skip it and goes directly to password screen and the OS. As I understand from some of the answers, everybody haven't understood that I ONLY have Ubuntu on the computer now.  Should I maybe format the disk? And if so, how do I do that?

Thanx again
/M[/QUOTE]

It sounds like your computer is not set to boot from cd-rom.  You have to enter the setup screen after you power on the computer.  To do this you have to hit one the the f-keys or delete or something.  Once in the menu look for something like boot-sequence and make sure cd-rom is first.  Then save changes and exit.  The machine will reboot and boot from the winxp cd.

---

### Post by krypto_wizard on 2006-01-17
Please don't leave Ubuntu. 

[QUOTE=Mattiaz]Thanks for all the answers. The primary probem I have is that I've tried to boot the computer with the WinXP SP2 cd. But everytime I try to use it, and also when I try to boot via cd-rom using the Ubuntu-cd, it just skip it and goes directly to password screen and the OS. As I understand from some of the answers, everybody haven't understood that I ONLY have Ubuntu on the computer now.  Should I maybe format the disk? And if so, how do I do that?

Thanx again
/M[/QUOTE]

---

### Post by lamego on 2006-01-17
Your problem is not with the OS but with the computer itself, to be more precise you didn't understood yet that you have a boot order and that your CD is not on the list (It was when you installed Ubuntu).
Just go to the BIOS and put the CD on the boot options.

If you do give up from Ubuntu at least you have learned how your system boots :razz:

---

### Post by Ptero-4 on 2006-01-17
Mattiaz. When you refer to a password screen. You mean a screen that appears before the "Microsoft Windows XP" splash screen (The Windoze XP boot screen)? Because of that's what you see then chances are that you're in front of a password protected BIOS or grub menu (don't know exactly the terms, the last PC I owned was a PC XT with DOS 4.0, after that I had an Amiga A3000 and later my iBook G3 500 MHz and finally my current eMac G4).

---

### Post by Nightwind on 2006-01-18
[QUOTE=Mattiaz]Thanks for all the answers. The primary probem I have is that I've tried to boot the computer with the WinXP SP2 cd. But everytime I try to use it, and also when I try to boot via cd-rom using the Ubuntu-cd, it just skip it and goes directly to password screen and the OS. As I understand from some of the answers, everybody haven't understood that I ONLY have Ubuntu on the computer now.  Should I maybe format the disk? And if so, how do I do that?

Thanx again
/M[/QUOTE]

If XP was installed when you got the computer, hit F8 when it boots, select safe mode, when the log in screen comes up select  the Administrator log in, hit enter as most manufactures do not put a password for the Administrator when they install XP at the plant. You can change the password for your father at this point in the control panel, users.
As I do not know your skill level I make 2 other suggestions below if this fails. 
1. Seasoned User Method(fastest method)
You may need to go into the BIOS setup and change the order of the boot devices. Depending on the manufacturer of the computer, you would hit either F-2 or F10 or the delete key when the computer shows the manufactures logo screen (this depends on the manufacturer). There you will see a menu that will have boot devices in it, tab until the CD Drive is listed first, then floppy or removeable devices, then hard drives, etc, you will hit the arrow keys or page up/down to tab to that menu, hit enter(normally)or what ever command is at the bottom or right of the screen to enter that part of the menu, hit F-10 in most cases to save the changes you made in the Boot menu, then reboot. Most BIOS menus have slim instructions in them and if you do not understand them do not go there.
Understand going into the BIOS you can make errors and cause the machine to become unbootable. You have been warned and I take no responsibility should you make the machine unbootable.

2. Safest Method (more time involved)
So in your case, since you cannot seem to boot from the XP CD I would go to this link:
[http://support.microsoft.com/?kbid=310994](http://support.microsoft.com/?kbid=310994) 
and follow the instructions to make the floppy disk for which ever version of Windows you have. 
Be advised that there is a difference in the boot floppies for XP Home and XP Pro. One will not work with the other so be sure to get the right ones. It will take 6 floppy disks and some time. Be sure to format the floppies and check them for errors. You right click on the floppy icon, left click properties, there are tabs at the top, pick tools, and then use the tools to scan the floppies for errors.
When the floppies are made,make sure you number them as you make them, put the #1 disk in and reboot, follow the on screen instructions.Perhaps this will help, post back if it doesn't. 
Good luck!

---

