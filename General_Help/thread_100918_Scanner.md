---
title: "Scanner"
date: 2005-12-08
forum: General Help
---

### Post by Christopher999999 on 2005-12-08
I would like to use my Vissoneer scanner, but Xsane can't find it. What should I do!

---

### Post by BathroomNinja on 2005-12-08
What is the model of the scanner?  Look on the scanner and give us any of the numbers and stuff you see on it.  Also, is the scanner connected with USB or parallel cable (the reall fat ended one)?

---

### Post by Christopher999999 on 2005-12-08
It is connected with USB. It is a Visioneer OneTouch 8100 Scanner.
;)

---

### Post by BathroomNinja on 2005-12-09
[QUOTE=Christopher999999]It is connected with USB. It is a Visioneer OneTouch 8100 Scanner.
;)[/QUOTE]


Short answer: It wont' work.

Long answer:
[Linux Questions.org 's reply]("http://www.linuxquestions.org/hcl/showproduct.php?product=76&sort=8&cat=all&page=1")
[Not enough info on scanner to support it]("http://www.qbik.ch/usb/devices/showdev.php?id=1072")

Basically, no devs have access to this scanner in order to create support for the E5 chipset.  Without that support, the kernel can't use the scanner, like almost any HP among many others.


UPDATE
Apparently, there IS a patch to suppor the scanner.  However, this will require re-compiling your Kernel.
[Patch]("http://www.kernel.org/pub/linux/kernel/people/gregkh/usb/2.4/usb-scanner-3-2.4.21-pre3.patch")

The process is a bit too long for me to write out here, I'll try to find a good HOWTO.  In the mean time, you might want to find your local [Linux User Group]("http://www.linux.org/groups/") and see if anyone local can help you with the recompile to add support.

- OR -

You could get a better supported scanner

---

### Post by Christopher999999 on 2005-12-09
Thanks! \\:D/

---

### Post by Christopher999999 on 2005-12-09
I am wondering if you you know what to do with the file that you linked you.

---

### Post by BathroomNinja on 2005-12-12
OK, first step.  Assuming that this scanner works fine in Windows, (if it doesn't work, you are wasting your time); first try this:

[http://www.ubuntuforums.org/showthread.php?t=84174](http://www.ubuntuforums.org/showthread.php?t=84174)

At the point where he says to tweak the kernel configuration to your needs; you will probably feel overwhelmed.  It's really not that bad.  Snoop around for USB, and look for imaging devices or scanners, and then look for your model and put an M on it to load it as a module.  Then continue with the guide.

If this doesn't work, or if you get totally lost or whatever, they the following:



Ok, if I remember correctly (I'm nowhere near my computer), here is what you need to do.  My memory is a bit off, so you will have to use your brain to help me out.


go to /usr/src
type: ls

you should see a directory with 2.6. something
 type: cd (name of directory)


Remember where this folder is.


Right click, SAVE AS that .patch file I linked you to.  Save it to the above folder.

go back into your terminal.

type: sudo patch -p1 < usb-scanner-3-2.4.21-pre3.patch

That should work if the first step doesnt.  This patch is VERY old, so I highly recomend trying the first step first.  Ask in that hread for any compile issues as they know more than me.  If you pull this off (and I know you can), you will know a LOT more about your computer than you ever dreamed and will have a lot more confidence.  That's a good thing.



EDIT -

If none of this works, another option is to buy a $40 HP scanner.  But it's fun trying to get things to work.

---

### Post by BathroomNinja on 2005-12-12
You know, I forgot to even check if your computer is seeing the scanner in Ubuntu.  What happens if you boot up the computer with the scanner UNPLUGGED, then after you are logged in, you plug it in, then try scanning?

---

### Post by NotJustANewbie on 2005-12-12
My CrapardBell-end (PackardBell) scanner hasn't worked with me on any of my Linux adventures (Mandrake, Suse, Debian and now Ubuntu) :(

---

### Post by BathroomNinja on 2005-12-12
Best way to check and see if anyone has created a driver for it is to find your make and model number, then google it with the word 'linux'.  It takes a while, but that's the only thing I do.  A lot of models of scanners, printers, etc.. just do not lend themselves to easy compatability with any OS.  Some makers try a bit harder.  HP usually works out of the box.  Old PackardBell stuff from the mid 90's...  good luck.  Post the model and name and I will see if I can help.

---

### Post by mherring on 2005-12-12
Have you checked Vuescan?

They support a lot of scanners and they have a free trial version

---

