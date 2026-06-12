---
title: "grub loader"
date: 2009-03-26
forum: General Help
---

### Post by bcbotha on 2009-03-26
i was dual booting vista and ubuntu but i have now taken off vista. however the microsoft bootloader is still in the list. how do i get rid of it and automatically boot into ubuntu?

---

### Post by Anthon on 2009-03-26
You should edit the file /boot/grub/menu.lst

---

### Post by omrisaber on 2009-03-26
This is not a problem since your default boot entry is ubuntu.
However, if you want to get rid of seeing "windows" entry in the grub boot list, you can do it manually.

open the terminal and write :
sudo gedit /boot/grub/menu.lst

you will find at the end the entry named "windows" and few lines after like this one :

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP (Saber OMRI)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

just add the "#" symbol in the beginning of each line, or simply remove this enty ;)

Now if you don't want to see the boot list, try to find in the same file, the entre called "timeout" :

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

just change the "10" to "0" ;)

---

### Post by bcbotha on 2009-03-27
im needing help. i got rid of microsoft from grub but i think i messed up grub. i cant log on to my machine. i get 

Error 11: Unrecognized device string

Press any key to continue...

this happened after i tried to install grub 2 and had a problem installing it. so i tried to uninstall it. i moved everything from my microsoft partition to this partition and now its not booting up. i do have a live cd with me if that will be any use.

---

### Post by bcbotha on 2009-03-27
what do you mean?

---

### Post by nebileix on 2009-03-27
Try running from your live cd and re-setup the boot. Follow instruction from this link should help. [[PHP]http://linuxmint.com/wiki/index.php/How_to_repair_your_grub[/PHP]]("http://linuxmint.com/wiki/index.php/How_to_repair_your_grub")

Gd luck.

---

### Post by bcbotha on 2009-03-27
i tried it but it didn't work. is there anything else i should be doing?

---

### Post by bcbotha on 2009-03-27
im running off the live cd and my ubuntu partition is dev/sda2. if i right click on it and go to infomation the status is Not mounted?

---

### Post by bcbotha on 2009-03-27
thanks guys for all your hard thinking. i managed to get in. i booted up to the select screen chose the item i normally do, pressed 'e' selected root and pressed 'e' then deleted every thing that came after root and typed (hd0,1). and now it boots up fine.

---

