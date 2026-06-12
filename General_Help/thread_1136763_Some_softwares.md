---
title: "Some softwares?"
date: 2009-04-25
forum: General Help
---

### Post by BlindSoul on 2009-04-25
**Hello,**
**I'm new here and i just installed Ubuntu 9 on VMware and it looks great and works great.**
**I've been wondering why it doesn't suppose softwares like on Windows. I mean the setup. [ Which saved as .exe. ]**
**And i've been wondering if WebPageMaker will work?**
**And if there's drivers for my laptop: HP DV6875se.**
 
 
 
**Thank you.**

---

### Post by kpkeerthi on 2009-04-25
[https://help.ubuntu.com/9.04/index.html]("https://help.ubuntu.com/9.04/index.html") is a good place to start.

---

### Post by BlindSoul on 2009-04-25
Yeah, But i've been wondering if you can offer me of any software i can download on the internet which opens .exe files.?

---

### Post by kpkeerthi on 2009-04-25
If you want to run windows application in Linux, try [wine]("http://www.winehq.org")

---

### Post by BlindSoul on 2009-04-25
Wow it's so confusing. I've been trying to install WinRar, I downloaded it for Linux and now i don't know what to do next.
Can anyone help?

---

### Post by lisati on 2009-04-25
> **BlindSoul said:**
> Wow it's so confusing. I've been trying to install WinRar, I downloaded it for Linux and now i don't know what to do next.
Can anyone help?

Ubuntu has its own program for managing RAR files (WinRar is a Windows program that won't work unless you use [Wine]("https://help.ubuntu.com/community/Wine")). On the Applications->Add/Remove Software menu, do a search for "RAR" 

For more information about using Windows programs via Wine with Ubuntu, read this wep page: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by BlindSoul on 2009-04-25
So that's mean ubuntu is only for softwares that are on the Add/Remove thingy?

---

### Post by kostkon on 2009-04-25
Check [this guide]("http://www.psychocats.net/ubuntu/installingsoftware") on how to install software in Ubuntu, if you want.

For rar support, go to Synaptic and install the rar and unrar packages. Then you will be able to extract and create rar files.

---

### Post by 3rdalbum on 2009-04-25
You're pretty much correct. Use Add/Remove or Synaptic Package Manager - it's the easiest way to find and install software. It's possible to download software from the web and install it, but it usually requires a compiling step that is probably beyond you at this stage.

---

### Post by stwschool on 2009-04-25
Ok you know how xbox games only work on an xbox and not a ps3, and how mac software doesn't work on a PC? Same thing. Linux is a different format, so windows software works on windows and linux software works on linux.

Linux is very convenient in that with ubuntu you have a package manager, which lets you just grab them from a list, a lot like Apple's App Store, but without the credit card bill.

I've found that using Wine allows me to get most windows software working pretty smoothly, and that's a pretty remarkable thing. I don't see anyone getting ps3 games working on an xbox360 any time soon ;)

The only quibble is that you won't get the full experience running in a vm. Bung it on as a dual boot, try it out properly, install wine and use that to ease the transition, and see where it leads you.

---

### Post by Murrquan on 2009-04-25
> **3rdalbum said:**
> You're pretty much correct. Use Add/Remove or Synaptic Package Manager - it's the easiest way to find and install software. It's possible to download software from the web and install it, but it usually requires a compiling step that is probably beyond you at this stage.

Not quite! A .deb file is to Ubuntu like an .exe file is to Windows -- something you can basically double-click on and it will install. And with Wine, you can run .exe files too. ^.^ It just doesn't always work perfectly.

Remember, though, for any Windows program you're wanting to use there's probably an Ubuntu equivalent! Like how you can do a search for .rar in Add/Remove Programs instead of downloading WinRar. Think in terms of what you need to do with your computer, rather than what Windows apps you need, and then find ways to do those things. You may be pleasantly surprised by what is available -- I vastly prefer Ubuntu apps to Windows ones!

If you want to see if a particular Windows app (or game) will run on Ubuntu, however, go here: [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by albinootje on 2009-04-25
> **BlindSoul said:**
> Wow it's so confusing. 

I think it's a good idea to read this carefully before you get more confused :
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
> 
I've been trying to install WinRar, I downloaded it for Linux and now i don't know what to do next.

There's no need for software like WinRar.
Ubuntu comes with software for archives. You can add rar and zip to this by installing the packages unrar, unzip, zip in Synaptic Package Manager.

-> System -> Administration -> Synaptic Package Manager
See also :
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by BlindSoul on 2009-04-25
And i'm unable to use Web Page Maker?
And what about the drivers?

---

### Post by lisati on 2009-04-25
> **BlindSoul said:**
> And i'm unable to use Web Page Maker?
And what about the drivers?

Open Office Writer can be used for creating basic HTML files. I'm sure there are other options if you dig around enough...

---

### Post by albinootje on 2009-04-25
> **BlindSoul said:**
> And i'm unable to use Web Page Maker?

For "wysiwyg" html editors, there's mozilla seamonkey html editor to try. If you really can't do without run it inside VirtualBox.

> 
And what about the drivers?

Very often all drivers that you need are included in Linux already.
With the possible exception for drivers with Ndiswrapper in case your wireless card is not natively supported by Linux.

---

