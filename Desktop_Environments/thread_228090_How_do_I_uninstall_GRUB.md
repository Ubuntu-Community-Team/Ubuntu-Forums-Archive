---
title: "How do I uninstall GRUB?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by bobleny on 2006-08-02
I had my system set up with two HDD; one with Ubuntu Linux (Primary Slave) And the other Windows XP Home (Primary Master). Unfortunately I had to uninstall Linux from the Slave, but now, when I turn on the computer, I get a GRUB error. Error 17 to be exact... If I take the slave drive out, I and turn the computer on, I get GRUB error 21.

Not knowing this until I installed Windows 98 SE on the slave  drive, I'm afraid reinstalling Ubuntu is a LAST resort. How can I uninstall GRUB? Is there a way to access windows XP by bypassing GRUB?

---

### Post by louis_nichols on 2006-08-02
grub is not really "uninstalled". it's rather simply overwritten or just deleted. to recover your XP boot, the easiest way I think is to boot from the XP install CD. when the option screen comes up, choose rescue and login to your win installation. then, issue these commands:

fixboot
fixmbr

no particular order. then it should just boot your XP.

---

### Post by bobleny on 2006-08-02
Yeah, Thanks! I'll try it with a boot disk first though. I don't know where the software is for it, Or even If the dumb thing came with a software disk. It's an HP...

Thanks.

---

### Post by bobleny on 2006-08-02
I get an I/O error with boot disk so I found the windows disk for this PC and poped that in.

fixboot worked fine. Didnt fix the problem (I know you said to use both).

When I use the fixmbr command, It says it may damage my partitions leaveing my HDD a pile of, well, you know the rest...

So, Should I do it anyways, or is there another way? I know windows is full of, well... and that they will give errors or warnings for no reason...

So, is there a better way?

---

### Post by louis_nichols on 2006-08-03
there isn't a better way. whatever you do, you must erase and rewrite the MBR (actually, rewriting it might not be necessary, but if you're there, you might as well do it) which will always involve risks. of course, as with everything at this hardware level, there are risks... every tool that will let you do such a thing will give you such a warning, which is only normal.

the win xp disk has never filed me, but I can't guarantee anything, so you will be doing this on your own risk. anyways, should, by exception, something go wrong, there are tools to recover from this.

---

### Post by mlind on 2006-08-03
You can "uninstall" grub using **dd**
[http://www.ubuntuforums.org/showpost.php?p=1275618&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1275618&postcount=4)

---

### Post by msandersen on 2006-08-03
There's a small Windows utility you can fit on a floppy called [Bootpart]("http://www.winimage.com/bootpart.htm") that can restore your MBR and more, specifically adding partitions to your boot menu.

---

