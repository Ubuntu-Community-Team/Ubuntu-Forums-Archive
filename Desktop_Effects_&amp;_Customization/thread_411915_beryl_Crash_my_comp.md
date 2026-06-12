---
title: "beryl Crash my comp"
date: 2007-04-17
forum: Desktop Effects &amp; Customization
---

### Post by Give_Peace_A_Chance on 2007-04-17
I install beryl, wiched it from the basic windows, too beryl and then it crashed...

Now it goes to the login screen, I can log in it loads up my desktop, but then it just goes to a screen thats text (not terminal like just text) then it just goes back to the login.

Im running off of the disk i have, but i realy dont want to just reinstall everything.

I tryed sudo killall beryl and it tells me nothen killed...

 [-o< Help please, [-o<

---

### Post by Seisen on 2007-04-17
Boot into recovery mode and either do this

```
sudo -dpkg-reconfigure xserver-xorg
``` and follow the directions or do this
```
sudo vim /etc/X11/xorg.conf
``` scroll down till you see this

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"

hit Shift +I  and go down to driver and change it to vesa and to write the file and save it, hold down  the shift key and press the semicolon key. Then type in "wq" which will write the file and then quit vim. Reboot and see if it works.

---

### Post by Give_Peace_A_Chance on 2007-04-17
but look

 Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver          "ati"
        BusID           "PCI:1:5:0"

---

### Post by jvc26 on 2007-04-17
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
Will set your xorg.conf back to how it was originally, then uninstall beryl via sudo apt-get remove. The if you want you can install again.
Il

---

### Post by Seisen on 2007-04-17
Follow these directions and see if it fixes the problem if not PM me and I will help you figure it out.
 
[http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html]("http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html")

---

### Post by Give_Peace_A_Chance on 2007-04-17
Im running off the disk 

I guess ill just write down the command and when i can figure it out ill just come back on..

---

### Post by Seisen on 2007-04-17
You just have to boot in recovery mode and follow the directions. Instead of using gedit use vim.

---

### Post by Give_Peace_A_Chance on 2007-04-17
I was in recovry mode and it still crashed i just reinstaller 6.06 and ill wait to upgrade on friday.



Thanks for the help.

---

