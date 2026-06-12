---
title: "Error 21 - How do I get out of this?"
date: 2009-05-18
forum: General Help
---

### Post by crispeto on 2009-05-18
I installed Jaunty onto an external HD using my Win desktop. I had it boot to the CD, installed Jaunty, and then unplugged my external drive and restarted Windows but before windows could ever start I get an error message "Grub Loading Stage 1.5" and then it says "Grub Loading...Please Wait" and finally, "Error 21" and then it just hangs there. How can I get my desktop to boot into windows again? It's my wife's machine and I hate sleeping on the couch!

---

### Post by Bindsa on 2009-05-18
Your MBR's are messed up, try this in terminal:
**Code:**
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
**Code:**
```
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then to restore a Windows MBR to your Windows drive, you can do:
**Code:**
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Then reboot, try booting the Ubuntu drive. Then unplug it and reboot, check whether windows boots.

---

### Post by sahabcse on 2009-05-18
For fixing the grub follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by crispeto on 2009-05-18
Wow, Bindsa, you're good! Worked like a charm! Thanks a bunch!

---

### Post by Bindsa on 2009-05-18
No problem mate.

---

### Post by crispeto on 2009-05-18
So now how do I boot to my external jaunty drive? Do I have to change it in the bios each time? Is there any way to choose between windows and my external jaunty during the boot up? Again, thanks.

---

### Post by Bindsa on 2009-05-18
Yes, plug in your drive, boot from it, GRUB menu will appear and you choose between Vista bootloader or Ubuntu.

---

### Post by crispeto on 2009-05-18
I'm actually running xp. So I plug in my external, set the bios to boot to it and it will ask me which drive to boot to? My desktop is a dell with WinXP and my external has Jaunty. Is there anything in the bios settings I can set to prompt me during start up as to which drive to boot to so I don't have to do it manually in the bios each time? I hope I'm making sense. Thanks.

---

### Post by Bindsa on 2009-05-19
Change your BIOS boot order and make it so that it boots from external drive first, that way you will automatically boot into Ubuntu when your external drive is connected, when you reboot and unplug it you will boot Windows, that's the easiest solution I can think of.

---

