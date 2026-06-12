---
title: "I have no 3D acceleration"
date: 2006-02-10
forum: Desktop Environments
---

### Post by Cysman on 2006-02-10
I'm now at a point where I'm pretty satisfied with Ubuntu.  I can play movies, burn cd's and convert audio formats.  The one thing I don't have is any 3D acceleration.  I have a Radeon 9800 pro with the latest drivers installed for ATI, 1.5g P4, 512 mb RAM on an HP machine.  I've displayed the fps before on other posts and it was told to me that they were pretty low.  Does anyone know of any other thing I can do to Ubuntu to improve my performance?  If Cedga is an alternative, will it deliver the performance of my video card?  

Just asking,

Ken

---

### Post by Ubuntuud on 2006-02-10
You could get "easyubuntu" or "automix", they install the driver for you, I don't know any websites though... (I don't know if they work either, I got a laptop with a build in Intel thingey.)

---

### Post by danhm on 2006-02-10
What's the output when you type "fglrxinfo" in a terminal

It should be something like this:
```
dan@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)
```


If it says the Vendor is MESA (or anything that isn't ATI, I suppose), you don't have the driver installed correctly. I suggest [this how to](http://www.ubuntuforums.org/showthread.php?t=75378); it worked great for me.

---

### Post by TrendyDark on 2006-02-10
Use this one for the newest drivers.

[http://ubuntuforums.org/showthread.php?t=78466](http://ubuntuforums.org/showthread.php?t=78466)

---

### Post by Cysman on 2006-02-10
Ok, I followed the link and got up to the part where I installed the new driver.  The How To says to "Change to the download directory (cd /path/to/directory)".  How do I do that?  I actually accomplished this command but did it get installed to the right place?  "sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base".  I'm asking because I didn't "Change to the download directory (cd/path/to/directory) first.  Basically, there are some things in these How To's that I don't quite understand yet.  Please help

---

### Post by dcstar on 2006-02-10
[QUOTE=Cysman]Ok, I followed the link and got up to the part where I installed the new driver.  The How To says to "Change to the download directory (cd /path/to/directory)".  How do I do that?  I actually accomplished this command but did it get installed to the right place?  "sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base".  I'm asking because I didn't "Change to the download directory (cd/path/to/directory) first.  Basically, there are some things in these How To's that I don't quite understand yet.  Please help[/QUOTE]
You downloaded the package to a directory, you use the command:

"cd wherever-the-directory-is" to change to it.

---

### Post by Cysman on 2006-02-10
[QUOTE=dcstar]You downloaded the package to a directory, you use the command:

"cd wherever-the-directory-is" to change to it.[/QUOTE]

Thanks for your reply,

The file was downloaded to my desktop, so do I need to move the file somewhere or what would the directory be if the file is on my desktop?

---

### Post by Cysman on 2006-02-10
Oh, wait I think I figured out the directory thing.......

---

