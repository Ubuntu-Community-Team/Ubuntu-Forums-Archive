---
title: "windows 7 install on usb?"
date: 2009-04-30
forum: General Help
---

### Post by blandino123 on 2009-04-30
hey guys. i want to dual boot into ubuntu and windows 7. i have the windows 7 iso but i dont have a dvd burner so i cant. i know that for this to happen i will have to install win 7 then reinstall ubuntu but i dont mind. i needto know how to do this?? how do i burn an iso in a usb and be able to boot into it? (windows)

---

### Post by Polygon on 2009-04-30
why do you need to install it to a usb key? you can just resize your ubuntu partition to  make room on your hd for windows 7.

and the ISO file is a image of the dvd, you need access to a dvd burner to actually create the cd so you can insatll it.

and you don't need to reinstall ubuntu after you install windows, you just need to restore grub. after you install windows, just boot int a ubuntu live cd again, open a terminal, and type "sudo grub-install hd0"

---

### Post by Hajo Harts on 2009-04-30
> **blandino123 said:**
> hey guys. i want to dual boot into ubuntu and windows 7. i have the windows 7 iso but i dont have a dvd burner so i cant. i know that for this to happen i will have to install win 7 then reinstall ubuntu but i dont mind. i needto know how to do this?? how do i burn an iso in a usb and be able to boot into it? (windows)
Hi. you might try this link:
[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/]("http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/")

---

### Post by obreiro on 2009-05-01
M$ Windows in Ubuntu forums??? NO please.
You should go to Microsoft's ridiculous forums [http://support.microsoft.com/search/](http://support.microsoft.com/search/)

---

### Post by eladamri on 2009-06-16
As Ubuntu users we should be supportive of people who want to dual boot.

Ubuntu is not going to attract new people if all it's users are uninviting and not understanding.

---

### Post by blueridgedog on 2009-06-16
Well, you could install ubuntu and make a smallish ntfs partition and extract the ISO to it and try and boot it with grub...if it works, then install to the unused part of your disk.  Just a wild guess.

---

### Post by Cheesemill on 2009-06-16
You could try this guide:
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

On step 4 in the guide just remember to not partition the drive into 1 large partiton as it suggests, leave yourself some space for Ubuntu.
For step 5 as you don't have an optical drive you could mount the .iso using [MagicDisc]("http://www.magiciso.com/tutorials/miso-magicdisc-overview.htm") instead.

---

