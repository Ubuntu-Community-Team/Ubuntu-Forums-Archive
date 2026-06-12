---
title: "Changing volume label on a fat32 partition."
date: 2006-02-21
forum: Desktop Environments
---

### Post by bb002 on 2006-02-21
I have a couple fat32 usb-drives that need their volume label changed. Currently the labels are blank. I just don't know how to change partition labels in linux. I've googled around and haven't come up with anything.

---

### Post by jones_jj on 2006-02-21
Do the drives show up in the Nautalis explorer, or on the desktop?  If they do, you should be able to right click on them and go to properties, and change the labels from there, just like you would in Windows.

---

### Post by bb002 on 2006-02-21
I tried that already. It is greyed out and won't let me change it.
I searched the forum and found this page [http://ubuntuforums.org/showthread.php?t=128363](http://ubuntuforums.org/showthread.php?t=128363).

For some stupid reason I posted before I searched this forum. During my google searches I found a page for a tool called "mlabel". mlabel didn't exist on my system. The above thread says it is part of the mtools package. So I'm going to install that and try mlabel again.

---

### Post by bb002 on 2006-02-21
mlabel did the trick but having to edit .mtoolsrc to create a drive letter rather than just being able to just use /dev/sda1 is annoying and useless. mlabel is just going to end up using /dev/sda1 so why bother with the overhead? To make things worse the need to edit .mtoolsrc wasn't mentions in the man pages. I got lucky in the fact that the page I linked to also linked to another page that had a set of working instructions for mlabel.

---

### Post by nekr0z on 2006-06-25
Well, and how do I do the same thing in Kubuntu? There's no Nautilus, and in Konqueror the device, not the label, is shown...

---

### Post by lee_03 on 2006-07-03
[QUOTE=bb002]mlabel did the trick but having to edit .mtoolsrc to create a drive letter rather than just being able to just use /dev/sda1 is annoying and useless. mlabel is just going to end up using /dev/sda1 so why bother with the overhead? To make things worse the need to edit .mtoolsrc wasn't mentions in the man pages. I got lucky in the fact that the page I linked to also linked to another page that had a set of working instructions for mlabel.[/QUOTE]
Where is .mtoolsrc located?

---

