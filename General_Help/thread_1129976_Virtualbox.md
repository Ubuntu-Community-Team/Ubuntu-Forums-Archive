---
title: "Virtualbox"
date: 2009-04-19
forum: General Help
---

### Post by axlotxlikexvegas on 2009-04-19
I'm wanting to use Virtualbox to run Vista so I can add music to my Zune (let's be adults and not bash each other for our multimedia preferences) but I can't find a decent guide on how to do any of this. Can anyone give me a good site or reference for this.

---

### Post by Therion on 2009-04-19
This tutorial should get you going.  It uses Widows XP as the Guest but the only "tricky" part to all of this, really, is setting up the Virtual Machine itself set up, not the OS that's going to run IN the virtual machine:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

EDIT: Almost forgot to mention... Don't use the download link that's in the tutorial.  Go here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)  and get the version you need.  

Do NOT get the OSE version, or the version from the Ubuntu repositories.  Neither of those versions will have USB support.

---

### Post by axlotxlikexvegas on 2009-04-19
Im running the 32 bit version of Ubuntu but I do have a 64 bit processor (Intel Core 2 Duo) so do I need the i386 or the AMD64? I don't really understand what they are saying about that.

---

### Post by Therion on 2009-04-20
Install the 32bit version if you're running a 32-bit distro.  You could be running 64-bit Ubuntu but you're not, so you need the 32-bit version of VirtualBox to match your 32-bit disto.

And just so you know, don't be confused by the "amd" part of 64-bit moniker -- any 64-bit processor can run Ubuntu 64-bit.  Like you, I have an Intel Core2 Duo, and I run Jaunty 64-bit just like I ran Hardy 64-bit.

---

### Post by axlotxlikexvegas on 2009-04-20
So everything went smooth except for 2 things. I can access my shared folder. Typing in net use x: \\vboxsvr\share in run does nothing at all. Also when I set it to access my usb external drive it never shows up and if I restart it tries to access it during start up (or so it seems, the light on it is blinking) and just hangs. Any help.

---

### Post by anjilslaire on 2009-04-20
Follow this for getting usb devices recognized in a Windows guest OS:
[http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy](http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy)

---

### Post by albandy on 2009-04-20
Have you installed guest additions?

---

### Post by axlotxlikexvegas on 2009-04-20
No. I seen something about that but nothing useful. How do I get them and install them. Also what do they do?

---

### Post by namegame on 2009-04-20
From VirtualBox's website:
> 
Guest Additions for Windows and Linux. VirtualBox has special software that can be installed inside Windows and Linux virtual machines to improve performance and make integration much more seamless. Among the features provided by these Guest Additions are mouse pointer integration and arbitrary screen solutions (e.g. by resizing the guest window). 

---

### Post by axlotxlikexvegas on 2009-04-21
Got the guest additions. Much better visually but now my vm doesn't recognize anything in the disk drive. Should I just reboot it or is there another problem I need to fix it (Haven't tried rebooting at the moment in the middle of an instillation)

---

### Post by howefield on 2009-04-21
> **axlotxlikexvegas said:**
> Got the guest additions. Much better visually but now my vm doesn't recognize anything in the disk drive.

The guest addition .iso will be mounted meaning you don't have access to the drive. 

Can you select the "Mount CD/DVD ROM" option from the VM Devices menu ?

---

### Post by heatblazer on 2009-04-21
BTW, is Virtualbox that good? I used to emulate WinXp with qemu because of a site made exclusively for windows :S And I had to do virtualization. So... shall I read a thing or two for virtualbox too :)

---

### Post by axlotxlikexvegas on 2009-04-21
And also my zune will link up but my external won't. Could it be cause its a 1TB and it's just gonna take a year to read all the files to display them?

---

### Post by axlotxlikexvegas on 2009-04-21
That fixed my disk drive problem, thanks, but the external hd issue is still open to interpretation. As for vbox, being a new ubuntu user for the first vm program I like it, just a few things to work out, which im sure is the same for all.

---

### Post by John Cheng on 2009-04-21
> **heatblazer said:**
> BTW, is Virtualbox that good? I used to emulate WinXp with qemu because of a site made exclusively for windows :S And I had to do virtualization. So... shall I read a thing or two for virtualbox too :)

Well, I tried VirtualBox after reading [_this_]("http://blogs.zdnet.com/BTL/?p=8880") article. I've found it to be very easy to use so far.

You should check out this _[thread]("http://ubuntuforums.org/showthread.php?t=784959")_ comparing the different virtualization solutions.

---

### Post by axlotxlikexvegas on 2009-04-21
Well if anyone can figure it out when I select to mount the usb device the sound windows has for connected device plays but nothing else happens. Any help?

---

### Post by axlotxlikexvegas on 2009-04-22
Got it.

---

