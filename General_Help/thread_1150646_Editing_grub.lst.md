---
title: "Editing grub.lst"
date: 2009-05-06
forum: General Help
---

### Post by emmettpower on 2009-05-06
I'm having problems with sound since I updated to Ubuntu 8.04.2, kernel 2.6.24-24-generic.

Am I going to run into problems if I attempt to roll back to Ubuntu 8.04.2, kernel 2.6.24-23-generic by commenting out the kernel 2.6.24-24-generic entries on my grub.lst file so that it reads, in part like this?

```

#title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=f0e98b50-2788-435b-81db-7c8f3aa3dd31 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-24-generic
quiet

#title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=f0e98b50-2788-435b-81db-7c8f3aa3dd31 ro single
#initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f0e98b50-2788-435b-81db-7c8f3aa3dd31 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic

```

---

### Post by danwood76 on 2009-05-06
You should also comment out the quiet line.

What problems are you having?

---

### Post by kryptikos on 2009-05-06
That won't hurt anything, but at the same time you don't need to comment out anything either. You can just tell Grub which kernel you want her to boot....

In the **menu.lst** you'll see a section named **default**. 

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default         0**


You can change the number 0 to a number (in your case) 2 and it will boot the 24-23 kernel instead (assuming it is installed). When counting the entries, Grub starts with the number 0. For instance, you have three kernel entries in your post, starting from 0 the third entry is looked at by Grub as the being in the number two slot. 

So in the default section you would have something now that said:   **default       2**

Hope that made a little sense. :)

---

### Post by emmettpower on 2009-05-06
Good point about the 'quiet' bit. 

All sound is gone with the exception of the odd system bleep and a message of 'No volume control GStreamer plugins and/or devices found' when I try to open the volume control. I have tried various solutions which haven't worked so I figured that rolling back to the last good configuration might be better.

The machine's a Dell Inspiron 1525 laptop.

---

### Post by emmettpower on 2009-05-06
Thanks kryptikos. Sound back, that was easy.

---

### Post by kryptikos on 2009-05-06
Glad it worked for you....Happy to help :)

---

