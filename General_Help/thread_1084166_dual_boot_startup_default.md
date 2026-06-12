---
title: "dual boot startup default"
date: 2009-03-01
forum: General Help
---

### Post by lindsay7 on 2009-03-01
I just set up a dual boot with Ubuntu and Vista. How do you change the default startup so that I can choose to automaticaly start vista or Ubuntu. Right now it will start Ubuntu. I want to restart windows if the computer is running windows, if I get a blue screen error.

---

### Post by Rallg on 2009-03-01
From within Ubuntu, open a Terminal. then:

sudo gedit /boot/grub/menu.lst

This is the file containing the boot order. Any line begiining with a hash (#) is a comment.

Towards the bottom, you will see the Windows boot instructions. Cut and past so that those instructions precede the boot instructions for your ubuntu. I don't mean put them at the top of the file, I mean relative to the other boot instructions.

Just keep in mind that there are several "sample" boot instructions, commented out.

Save the file, then you can reboot.

What if you made a terrible mistake, and bungled the editing? All is not lost. You can edit that file using something such as a live Linux distribution on a USB stick. Just keep in mind that you need to edit the menu.lst file on your hard drive, not the one within the live Linux distro.

---

### Post by lindsay7 on 2009-03-01
So, if I understand you, I would make the changes in the gedit list that I get when I run gedit /boot/grun/menu.lst and just save that file, close gedit, and reboot. When you say that If I make a mistake, I could use a live distribution, you mean if I were to really mess up this grub file, right. I can always do an edit as long as the systems boots to Ubuntu, correct. I imagine that I could save the contents of the gedit list to a document somewhere on my computer and use it to copy back to the gedit if I needed to.  Am I understanding this correctly. I do not want to mess with this file if I do not.

Thanks for you help.

---

### Post by Rallg on 2009-03-01
Yes. The menu.lst is a plain text file. It is human-readable, if you know how. Windows, Linux, and Mac use different codes for line endings, so that might be an "oops" if you use the wrong text editor by transfering the file to a different system. But even then, it can be fixed.

Probably, very few people damage the file. There's not much that can go wrong with cut and paste.

In fact, if you totally lose menu.lst, it can be reconstructed. I won't provide details here - you probably will never need them - but as long as you can get access to your ubuntu partition from somewhere else (such as a separate live Linux on USB), you can fix or replace menu.lst. It is even possible to create a brand new menu.lst from a blank, without knowing what was in the original menu.lst.

In fact, when you edit menu.lst, your system probably keeps a backup copy named menu.ls~ that is hidden. It can be restored, even from an external live Linux, by getting to your hard drive, showing hidden files, and changing the extension from menu.ls~ to menu.lst. (Note: Distros other than Ubuntu may work differently.)

People do this all the time. You can also change how long the boot menu is shown before it automatically boots to the first entry.

---

