---
title: "GDM error message"
date: 2006-03-28
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-03-28
When trying to log in to my computer I get the follwoing error message:

"GDM could not open your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, is not possible to log in. Please contact your system administrator".

Now, I think it really might be the disc space, and reading the forum I found out I should type ```
sudo apt-get clean
``` in a terminal.

But obviously I can't open a terminal. Or can I?

HELP!!!

G

---

### Post by taurus on 2006-03-28
You can either <Ctrl><Alt>F2 to a console and see if you can log in from there.  Otherwise, boot into single user mode, recover mode, from GRUB and clean your harddrive to make some space.

---

### Post by GabrielWolff on 2006-03-28
[QUOTE=taurus]Otherwise, boot into single user mode, recover mode, from GRUB and clean your harddrive to make some space.[/QUOTE]

Could you translate that to English (or any other language...)? ;-)
How do I log in from GRUB?
And would "clean up your harddrive" be: sudo apt-get clean?

---

### Post by art on 2006-03-28
When booting, choose the recovery mode, that will bring you up to root console.

---

### Post by GabrielWolff on 2006-03-28
[QUOTE=art]When booting, choose the recovery mode, that will bring you up to root console.[/QUOTE]

Just to make sure before I leave this machine, and go back home to mine: I do that by pressing esc when the computer is booting, right?
G

---

### Post by art on 2006-03-28
yes, when it prompts you to choose, or alternativel you can unhide the menu in 
/boot/grub/menu.lst commenting the line 
#hiddenmenu
and the menu will appear without ESC

---

