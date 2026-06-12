---
title: "Ubuntu day 1"
date: 2005-10-17
forum: Desktop Environments
---

### Post by jasonwvu on 2005-10-17
This is the first day I have used Ubuntu, and I can't figure out how to install programs. I keep reading about using the command line, but I can't find this  in any of the menus.

---

### Post by daschl on 2005-10-17
[QUOTE=jasonwvu]This is the first day I have used Ubuntu, and I can't figure out how to install programs. I keep reading about using the command line, but I can't find this  in any of the menus.[/QUOTE]


just feel free to use System -> Administration -> Synaptic Package Manager :)

---

### Post by jasonwvu on 2005-10-17
I should have been more specific, I want to install real player 10. I downloaded the program to my desktop, but am unsure how to use the package manager or anything else to install this.

---

### Post by kingsidy on 2005-10-17
first you need to open the command prompt by clicking on programs > accessories> terminal. After the terminal is open, type in "sudo su" it will then ask for a password, input the root password you set up during the install. 
you will then see "root@ubuntu: /home/" or something like that. type in "cd /home/yourusername/Desktop" and hit enter. Then type in "dpkg -i realplayer" and that's it. it will install realplayer on your computer.

i hope this helps

---

### Post by cytoplasm on 2005-10-17
jasonwvu,

First, please clarify what you downloaded.  Did you download a .deb RealPlayer package or did you download the .bin installer from [https://player.helixcommunity.org/](https://player.helixcommunity.org/) ?

The last post menionted that you use su to root.  Most likely you do not have root enable so simple use "[FONT="Courier New"]sudo dpkg -i <package name>[/FONT]".

If you downloaded the .bin installer then things will be slightly different on how you go about installed RealPlayer.

Shawn

---

### Post by WolfJay_83 on 2005-10-17
I think you may find help sites much more helpfull:

Ubuntu User documentation - look under restricted formats and multimedia- has most everything you need:

[https://wiki.ubuntu.com/UserDocumentation]("https://wiki.ubuntu.com/UserDocumentation")

You will learn alot from skimming through that manual, but specificaly realplayer instructions are at 

[https://wiki.ubuntu.com/RestrictedFormats#head-59a79c66f6fef0a9350390de31797a457ed85cd8]("https://wiki.ubuntu.com/RestrictedFormats#head-59a79c66f6fef0a9350390de31797a457ed85cd8")

hope this helps

---

