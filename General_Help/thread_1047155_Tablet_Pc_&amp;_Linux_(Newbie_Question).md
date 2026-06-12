---
title: "Tablet Pc &amp; Linux (Newbie Question)"
date: 2009-01-22
forum: General Help
---

### Post by odalanizi on 2009-01-22
Hey all, new here!

First and foremost, I'm a Linux newbie. I've only ever 'seen it in action' once. In light of Obama's presidency, I've decided to migrate and be apart of the 'free world'

I'd appreciate if you'd read below and help me out :)

I recently received a laptop as a present. This laptop is essentially a Tablet PC, yet it was loaded with Windows XP Home.
> (The Laptop in Question is Flybook A33i)
> (Detailed Specs/Review: [http://www.notebookcheck.net/Review-Dialogue-Flybook-A33i.1354.0.html](http://www.notebookcheck.net/Review-Dialogue-Flybook-A33i.1354.0.html))

So I have 2 questions 
#1) Is Linux suitable for a Tablet pc? does it have Tablet-friendly software and such? I mainly use the Tablet for taking notes in class, and annotating PDF files -- is there a software in Linux that does this?

#2) If you didn't check out the specs in the link above, basically it's got: 
RAM: 512 MB DDR
Processor: 1 Ghz (Transmeta Crusoe TM-5800)
Graphics: ATI Mobility Radeon: Dedicated DX 7 (no Aero support) graphic card without Hardware T&L, based upon the desktop R100 chip with up to 16 MB memory.

I think due to this not-so-hot set up, it runs slowly, Exhaustively so! Would Linux improve the speed? and would Linux be compatible with it? 


AND MOST IMPORTANTLY: This laptop has no Cd-drive. Is there a way to install Linux by mounting the iso? with daemon tools? 


THANKS ALL

---

### Post by thegreenblob on 2009-01-22
I've never actually used a tablet pc so I can't answer the initial questions. But, I believe I can answer the last two :)

> I think due to this not-so-hot set up, it runs slowly, Exhaustively so! Would Linux improve the speed? and would Linux be compatible with it?

I've ran linux on PCs with less specs than that and it's ran fine. So I'd say yes. :)

> AND MOST IMPORTANTLY: This laptop has no Cd-drive. Is there a way to install Linux by mounting the iso? with daemon tools? 

I don't think you could run the normal installer like that. But I believe you could mount the iso and run the wubi installer. Which would set up a windows/ubuntu dual boot. Or I believe you can also do a normal install via USB flash drive instead of a disc.

Hope I've helped. :)

---

### Post by onero on 2009-01-22
You can install the latest Ubuntu using a USB drive, but I think you need to download the Live CD and then convert the .iso to a USB install. I haven't tried it, but you can [check out this guide]("https://help.ubuntu.com/community/Installation/FromUSBStick").

Regarding tablet apps, sadly there aren't really equivalents for many of the apps in Windows, but if you just want it for simple notetaking, [Xournal]("http://xournal.sourceforge.net/") is OK. It can also "annotate" PDFs by using the PDF file as the background to the Xournal file.

I'm not too sure about the Hardware, but the best way is to just check it out by booting off the USB stick (this acts the same as booting off a Live CD, and you can test how well your hardware works this way). You might need to install restricted drivers and the like for the ATI card, but I'm not sure.

---

### Post by Favux on 2009-01-22
Hi odalanizi,

If you can get Ubuntu installed:

I second onero's suggestion of Xournal.  Also Cell Writer (letter recognition) is recommended.

I'm also not sure about the hardware.  But evtouch is usually used for touchscreens.  It's in Synaptic.

---

### Post by golusweet on 2009-01-22
You can install ubuntu via USB Flash drive.

Check out this link how to make USB bootable
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I have got Tablet pc too,and it's a pain to get it working.I would recommend to have dual-boot,and give it a go.:p

---

