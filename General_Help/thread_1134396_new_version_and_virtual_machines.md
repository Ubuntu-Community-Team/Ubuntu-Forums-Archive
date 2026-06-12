---
title: "new version and virtual machines"
date: 2009-04-23
forum: General Help
---

### Post by gianthobbit on 2009-04-23
New to ubuntu and forums,  quick question, I need to be able to run some windows apps like photoshop etc.  Is there a way to do this in ubuntu?  What is the best way?
[RIGHT][/RIGHT]
I am having some serious windows issues at the momment, my pc goes form bios to black screen every boot.  I have to run recovery disk chkdsk every time to get it to boot into windows.  Will this effect the install or possibly fix it?

---

### Post by mwacky on 2009-04-23
Give Wine a try, I don't know how it works with Photoshop but it works well with other Windows Apps.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by kanikilu on 2009-04-23
If you have a copy of windows, probably the easiest way to run your windows applications would be to use some sort of virtualization.

Many people swear by VMWare, but I was late to the VM party and have only ever used VirtualBox...which has worked fine for my needs.

Your other options for running windows apps on linux would be Wine (free, opensource) or the commercial software built off Wine called CrossOver. Check the respective websites first though to see if your applications are supported.

As for whether or not installing Ubuntu will "fix" your problem with windows, I can't say for sure. If you have to run chkdsk everytime you boot, to me that sounds more like a failing hard drive than a corrupted filesystem...

Rather than guessing, though, you should find out what brand the hard drive is and download the diagnostic tool from the manufacturer's website.

I think the [UBCD](http://www.ultimatebootcd.com/) has some hard drive diagnostic tools on it as well...

---

