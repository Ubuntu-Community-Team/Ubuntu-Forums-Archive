---
title: "can't log in --  suggestions"
date: 2006-02-27
forum: Desktop Environments
---

### Post by newUBuser on 2006-02-27
I spent a  few hours installing ubuntu on my vmware and the user I created doesn't successfully log in....

I am guessing there is no default root password.....  so what can I do??

I tried to reboot and type init 1...  bu t there doen't seem be a way to force a boot to single user mode.   Or is there???

:confused:

---

### Post by RAOF on 2006-02-27
The "recovery mode" option at the grub bootscreen is single-user mode.

---

### Post by mcduck on 2006-02-27
[QUOTE=newUBuser]I spent a  few hours installing ubuntu on my vmware and the user I created doesn't successfully log in....

I am guessing there is no default root password.....  so what can I do??

I tried to reboot and type init 1...  bu t there doen't seem be a way to force a boot to single user mode.   Or is there???

:confused:[/QUOTE]
Have you tried logging in in command line? When in login screen, press ctrl-alt-f1 to get into CLI login, and ctrl-alt-f7 to get back to GUI.

Also, there should be option for safe mode (single user mode) in grub menu when you're booting Ubuntu. If the grub menu is hidden it should anyway show you timer and tell what button to press to show the menu..

There is no root password, and you shouldn't need one. You can use 'sudo' with any command to run it as root. (like 'sudo gedit' to open text editor as root). When you get into GUI, all administration tools will ask for _your_ password. Logging in as root is disabled (other than the single-user mode available in Grub). Here's more info about Ubuntu & root: [https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29]("https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29")

---

### Post by newUBuser on 2006-02-27
Sorry guys....

I need a bit more info to get to grub and start up in single user mode....

Part of the problem seems to be that the user name and password I thought I installed isn't working....   or variations of it....

so how I do I get into single user mode??

---

### Post by newUBuser on 2006-02-27
also....

This sequence doesn't work on my HP laptop.....

"press ctrl-alt-f1 to get into CLI login, and ctrl-alt-f7 to get back to GUI."

Does nothing for    me.

---

### Post by RAOF on 2006-02-27
Do you see the grub bootscreen?  It'll give you a list of all the kernels you've got installed, and some other stuff (like the "recovery mode").  If you **don't** see it, it should say "press esc to enter bootmenu" at some point during boot.  If this is in the virtual machine, I'm not sure how that would change it... but I think that they do a normal boot of the virtual machine.

---

### Post by newUBuser on 2006-02-27
I didn't see any prompt about  boot mode, grub or pressing esc.....

The boot is slow in vmware so I've only tried watching it twice.


So is the suggestion to press "esc"  repeatedly during the reboot??

:confused:

---

### Post by RAOF on 2006-02-27
[QUOTE=newUBuser]I didn't see any prompt about  boot mode, grub or pressing esc.....

The boot is slow in vmware so I've only tried watching it twice.


So is the suggestion to press "esc"  repeatedly during the reboot??

:confused:[/QUOTE]
Pretty much, yeah :)

---

### Post by newUBuser on 2006-02-27
OK....  rebooting again.

Thanks for the reply.....

---

### Post by newUBuser on 2006-02-27
Oh...  saw the early place in boot up where ESC brought up the list.

Since our last exchanges were about GRUB, I pressed 'c' for GRUB command line.

>>>  Apparently I should have selected just recovery mode!!

Well, is there a grub command to force single user mode??  or what do I do to exit from grub and go back to the menu list of kernels with the recovery option?

---

### Post by newUBuser on 2006-02-27
GRUB doesn't seem to support much in the way of commands.

If I say 'boot' will it do afull boot or will it return to the menu where I can select recovery mode??

I wonder if reboot is the best option.....

---

### Post by RAOF on 2006-02-27
[QUOTE=newUBuser]GRUB doesn't seem to support much in the way of commands.

If I say 'boot' will it do afull boot or will it return to the menu where I can select recovery mode??

I wonder if reboot is the best option.....[/QUOTE]
A reboot may be the best option.  Or, you could try entering the following:
```
root            *(hd0,0)*
kernel          /vmlinuz root=*/dev/mapper/storage-dapper--root* single
initrd          /initrd.img
boot

```
Replacing the italicized stuff with your actual values.

---

### Post by newUBuser on 2006-02-27
Ah.... just another "esc" get one back to the GRUB menu....

booting in recovery mode now....


lots later ....  Oh, didn't send this.   I've been working.


I succeeded at installing subversion.   But the site I need to get to doesn't seem to recognize my keys.....

Thanks to all in getting me over the startup problems.

H.

---

