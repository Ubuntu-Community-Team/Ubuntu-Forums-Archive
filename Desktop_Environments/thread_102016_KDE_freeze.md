---
title: "KDE freeze"
date: 2005-12-11
forum: Desktop Environments
---

### Post by TudorB on 2005-12-11
I experience some KDE freezes, and the only way I can gain back control is to reboot the system (by using the magic reset button).
The sounds keeps going, amaroK was still playing the songs, but i couldn`t do anything else. 
Are there any drivers I should update? 
Thank you...

---

### Post by Knomefan on 2005-12-11
Are you by any chance using the nvidia drivers and did enable RenderAccel in your xorg.conf?

---

### Post by TudorB on 2005-12-11
Uummmm....Maybe. How do I find out if I am using those drivers?

---

### Post by Knomefan on 2005-12-11
Well, do you have a nividia card and did you install a package named nvidia-glx?

But as they are not installed by default, did you in anyway change your xorg.conf, or follow a howto that changed it?

P.S.: Also, can you still switch to a virtual console when X freezes, that is use Ctrl+Alt+F1?

---

### Post by Rackerz on 2005-12-11
Also if it inconveniently decides to do it again just press ctrl + alt+ backspace

It will take you back to the login screen.

---

### Post by TudorB on 2005-12-11
Yes, I have an nvidia card, GeForce 2 (I don`t play games, don`t need more) and the nvidia-glx driver is installed. I`ve used Synaptic to locate it! 

I`ve added the line 
DisplaySize	270	203	# 1024x768 96dpi
in xorg.conf following the "How to install windows fonts" howto.

I don`t know, I`ve only tried CTRL+ALT+BACK SPACE in kill the X Server and didn`t work!

---

### Post by Knomefan on 2005-12-11
And did you enagle RenderAccel?
Look at your xorg.conf.
In the device section (Section "Device")
you should see something like Option "RenderAccel"   "true" if you did.

If you did, disable it by putting a # in front of this line.
RenderAccel with the nvidia drivers from the repositories is know to cause lock ups.

---

### Post by TudorB on 2005-12-11
```

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

```
This is how the device section....

---

### Post by Knomefan on 2005-12-11
Hm, well then you are using the nv driver, not the nvidia driver.

Sorry, I don't have any idea what could be causing this then.
You could take a look at the logs though and see if you get any error messages there:
less /var/log/Xorg.0.log

---

### Post by xvolks on 2005-12-18
Hi,

You should see [http://ubuntuforums.org/showthread.php?t=40845](http://ubuntuforums.org/showthread.php?t=40845)
perhaps it's related to our problem (Yes, I have it too :( )

---

### Post by Adrian_b on 2006-02-05
[QUOTE=xvolks]Hi,

You should see [http://ubuntuforums.org/showthread.php?t=40845](http://ubuntuforums.org/showthread.php?t=40845)
perhaps it's related to our problem (Yes, I have it too :( )[/QUOTE]

Sorry for bumping the old thread, but i have the same problem.
I installed it twice and it still happens.
I'm using the first kubuntu BB version that came out.
When it came out, i didn't have this problem, but that was when i still had my nvidia Geforce 4 MX(i've upgraded to a 6600GT)
If the KDE package in the current Kubuntu BB release differs from the first one, i'll try to download it and install it to see if that helps.
Meh :cry:

---

### Post by broxtor on 2006-02-24
I have also the exact same problem with Breezy. KDE randomly locks up. Then the only way to fix it is to push the reset button. The strangest thing is that I have Breezy installed on two other machines. One of those has almost the exact same hardware configuration as the one I'm having the problems with. The only difference is the graphics cards. The one without the problems has a Geforce 4 graphics card, the one that causes the problems has a Geforce 6600 GT card. Based on this and the comments of Adrian_b, I think it has got something to do with the Geforce 6600GT.

---

