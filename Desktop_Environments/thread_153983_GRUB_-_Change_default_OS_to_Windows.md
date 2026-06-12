---
title: "GRUB - Change default OS to Windows?"
date: 2006-04-02
forum: Desktop Environments
---

### Post by briansalo on 2006-04-02
Hey all,

I'm trying to find a way to alter the GRUB bootloader to have Windows XP as the default OS, since the other people who have to use this computer will have no idea of what to do unless the computer does it for them (let the timer run out and boot XP).

Thanks in advance.

---

### Post by kikkum on 2006-04-02
Open your /boot/grub/menu.lst file and find the block with "title    Windows bla". Move this block of text (I think there should be a line with root (hdx,y) and one with chainloader +1) to between the following lines:

```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```

so it'll become a little something like this:

```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title Windows
root (hdx,y)
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST
```

This way it'll be put on top of your list and it'll stay there, even if you upgrade to a new kernel. If you want this top entry to remain the default choice, also make sure you have set "default		0" in the same menu.lst file.

---

### Post by souki on 2006-04-02
- boot linux
- edit /boot/grub/menu.lst and change the default option
- reboot

you can find usefull comments in this file
if you change to  'default saved'
and put a 'savedefault' to the windows section, you will keep this default after kernel upgrade

---

### Post by briansalo on 2006-04-02
Thanks to both of you for the help, and it was so quick too :)

---

