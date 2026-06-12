---
title: "Enabling DMA"
date: 2005-10-20
forum: Desktop Environments
---

### Post by MeijUbuntu on 2005-10-20
Hello,

How can i enable DMA and make it default ?

Now i have set the following every time i boot my system:
sudo hdparm -d1 /dev/hda

Any thoughts ?

Thnx in advance

---

### Post by aysiu on 2005-10-20
[http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)

---

### Post by denzilla on 2005-10-20
Thats an annoying bug. Had the same problem in Hoary and it carried over to Breezy.

---

### Post by SickTwist on 2005-10-20
Actually in Hoary, /etc/modules had to be modified sometimes to make it work. I don't think this second step is required in Breezy.

---

### Post by raublekick on 2005-10-20
quick question: when you add the three or so lines to hdparm.conf, do you need a '#' preceding each line?

---

### Post by flyingbrass on 2005-10-21
[QUOTE=raublekick]quick question: when you add the three or so lines to hdparm.conf, do you need a '#' preceding each line?[/QUOTE]
No. Lines with # in front are ignored.  Use # for comments or to disable a line in a config file without deleting the line (so you can reenable it later if desired).  If your CD drive is on /dev/hdc, you'd add something like this:

# This enables dma on my CD drive
/dev/hdc {
       dma = on
}

---

