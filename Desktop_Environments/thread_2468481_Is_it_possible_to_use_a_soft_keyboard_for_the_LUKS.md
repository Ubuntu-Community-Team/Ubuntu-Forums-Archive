---
title: "Is it possible to use a soft keyboard for the LUKS unlock screen?"
date: 2021-10-31
forum: Desktop Environments
---

### Post by Paddy Landau on 2021-10-31
I installed Ubuntu 20.04 with full disk, full encryption. Therefore, each time I start the computer, I'm prompted to enter the LUKS passphrase to unlock the disk.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289407&stc=1[/IMG]

I read on a forum that when changing keyboard, there is a risk that your passphrase won't be recognised because the keyboard layout has changed. I wouldn't want that to happen to me!

Unfortunately, you can't view what you are typing to confirm that it's correct (that's a shortcoming of the lock screen) — unless you can correct me on this?

So, is there a way to use a soft keyboard to enter the passphrase?

---

### Post by grahammechanical on 2021-10-31
I do not know if this will help you but at the Ubuntu login screen in the top panel and to the right there is an icon of a human. Click on that we get a variety of accessibility options including On Screen Keyboard.

Regards

---

### Post by Paddy Landau on 2021-10-31
> **grahammechanical said:**
> … at the Ubuntu login screen in the top panel and to the right there is an icon of a human.
Thanks, but that's after the disk has been unlocked. The part that I'm talking about is beforehand, when Grub prompts for the LUKS key to unlock the disk before it can load Ubuntu.

---

### Post by grahammechanical on 2021-10-31
Oh. sorry. I have had a quick browse through my copy of the Grub manual and I cannot see anything there. A very quick internet search came up with a post on Reddit about a virtual keyboard that was activated in the BIOS/UEFI settings under Security. I think the virtual keyboard appears if the actual keyboard is not connected.

Regards

---

### Post by Paddy Landau on 2021-11-01
> **grahammechanical said:**
> … a virtual keyboard that was activated in the BIOS/UEFI settings under Security. I think the virtual keyboard appears if the actual keyboard is not connected.
Thanks. I just tried that: I turned off the computer, disconnected the keyboard and mouse, and restarted (my computer has a touchscreen). A brief BIOS warning appeared, and it proceeded to the lock screen, but alas, there was no soft keyboard. I had to plug my keyboard and mouse back in to continue!

---

