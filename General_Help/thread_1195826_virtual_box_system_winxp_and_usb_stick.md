---
title: "virtual box system winxp and usb stick"
date: 2009-06-24
forum: General Help
---

### Post by unix1adm on 2009-06-24
I have a WinXp virtual box. How can I get it to see my usb stick? 
Also how can  i transfer data from Ubuntu to the WinXp image? 

also is there a way to get my phone to hot sync over the usb to the virtual box winxp iamge?

I tried looking for a mount point on the linux system or a directory etc. but cannot find a way to get the data over to it.

---

### Post by jdeppel on 2009-06-24
Are you using VirtualBox OSE (The version available in Ubuntu repositories) or did you download the .deb from VirtualBox's site? 

If you're using the OSE version, it has no USB support. The closed-source edition does.

---

### Post by unix1adm on 2009-06-24
yes i am usng the Ubuntu installed code.

---

### Post by jdeppel on 2009-06-24
In that case, head to [www.virtualbox.org](www.virtualbox.org) and get yourself the deb for the closed-source edition. Install that, and you should be good to go.

---

### Post by unix1adm on 2009-06-25
thank you I will try that and report back.

Do I have to uninstall and lose my VB system? 
Can I just overlay the new code?

I am guessing you are talking about this?

I am running the Ubuntu 9.x now. I dont see that or do I want this?
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Ubuntu 9.04 ("Jaunty Jackalope") i386 | AMD64

I guess 9.x is called Jaunty Jackalope from what I have been reading... Confusing these code names ;)

---

### Post by jdeppel on 2009-06-25
Yep. That's the file you want to download...either i386 or x64, depending on your system. 

You will need to uninstall your current VirtualBox (not sure if it's required, but the two conflicted when I had both installed). However, when you once you get VirtualBox back up and running, you can mount the previous .vdi file from your existing Windoze virtual copy, eliminating the need to reinstall it. The file is located in: ~/.virtualboxOSE/HardDisks

---

### Post by unix1adm on 2009-06-25
great. I did not want to reinstall my windoz system. Ill try it hopefully tonight and let you know...

---

