---
title: "Error loading firmware bcm43xx"
date: 2009-02-12
forum: General Help
---

### Post by JimBuntu on 2009-02-12
Ubuntu stopped working on my dual-boot laptop and don't know why. When I boot in recovery mode I get this:

root@ubuntu-laptop:~# firmware_helper [4452]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:02.0' with driver 'bcm443xx'
[402.795030] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

When I hit enter it takes me back to:

root@ubuntu-laptop:~#

I have done a little research on this and it looks like its some kind of firmware for the wireless card or something. Broadcom?? 

I want to know if there is an easy fix for this, or if I should just do a clean install of Ubuntu on this partition?

---

### Post by Peter09 on 2009-02-12
bcm43-fwcutter is a synaptic package, you could try re-installing through synaptic.

---

### Post by JimBuntu on 2009-02-12
how would I go about doing that? Remember all I can use is a command line and I don't even know how to use that.

---

### Post by Peter09 on 2009-02-12
if you have a command line open 'recovery mode' or if you have a GUI type ALT-F2

and type the following.

```
sudo apt-get install b43-fwcutter 
```
hit enter.

Remember to do the line exactly, all lower case.

apt-get is the command line interface for synaptic.

---

### Post by JimBuntu on 2009-02-12
Just did what you said and it came up with:

E: Couldn't find package b43-fwcutter

---

### Post by Peter09 on 2009-02-12
try the following commands first

```
sudo apt-get update
```

```
sudo apt-get upgrade
```


the b43 package is a standard package in ubuntu so if it cannot find it something is wrong.

---

### Post by JimBuntu on 2009-02-12
I'm going to try those right now. Just a thought, do I have to be connected to the Internet for this stuff to work, or have a disc in the drive?

---

### Post by JimBuntu on 2009-02-12
sudo apt-get update gave me a bunch of lines of "Failed to fetch"

---

### Post by Peter09 on 2009-02-12
You need to be connected to the internet.

---

### Post by JimBuntu on 2009-02-12
I am right now and have tried it all. When i do sudo apt-get upgrade it keeps saying 0 packages upgraded.

---

### Post by JimBuntu on 2009-02-12
Is there anything I can do in the command line to check if the connection is working? I have it connected with an Ethernet cable

---

### Post by Peter09 on 2009-02-12
Just try on the command line

```
startx
```

see if that gives you a GUI


what version of Ubuntu are you running?

---

### Post by JimBuntu on 2009-02-12
So I got it to start up. It gives me the login screen, I log in, and then it plays the music and then the resolution gets really bad and then it crashes and goes back to the login screen. I think I might have screwed up the xorg file. How do I fix? I am pretty sure the only prob right now is the screen res and refresh rate.

---

### Post by Peter09 on 2009-02-12
Are you on Hardy or Intrepid?

You should get a munu up during boot up in recovery mode that lets you reconfigure the x server.

Try 
```
 sudo dpkg-reconfigure -phigh xserver-xorg

```

to reconfigure the server if you have no menu.

---

