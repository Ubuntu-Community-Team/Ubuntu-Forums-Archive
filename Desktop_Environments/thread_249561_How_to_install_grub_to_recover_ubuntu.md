---
title: "How to install grub to recover ubuntu???"
date: 2006-09-02
forum: Desktop Environments
---

### Post by DumDum on 2006-09-02
Hi!

I've installed Vista and it removed grub.:( 

Using the live cd ubuntu I've access to my ubuntu  hd instalation(hda7), therefore access to /boot/grub and menu.lst(the old startup menu of grub).

How can I reinstall Grub to use the old menu? my boot devive is hda (or hda1).

Thanks!

---

### Post by Crooksey on 2006-09-02
Jump onto a liveCD

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

---

### Post by motin on 2006-09-02
Boot with Live-CD
Open terminal
Run "sudo grub"
type in "root ("
press tab, choose your ubuntu-holding hard-drive and type that in, ie "hd0"
type in "," and press tab
type in the partition with /boot/grub and remember which number contains your Vista installation (unknown filesystem 0x7 or similar)
end the paranthesis and press enter
type in "setup (hd0)" + enter
then add Vista chainloader menu item in menu.lst (google it :) )

partition 0,1,2,3 are your primary partitions, from 4 and on begins the logical partitions.

---

### Post by jISh on 2006-09-02
And remember GRUB counts from 0, so even if your hard drive is hda1, you need to put in hd0.

---

### Post by DumDum on 2006-09-02
Thanks to all! its working again :)

---

