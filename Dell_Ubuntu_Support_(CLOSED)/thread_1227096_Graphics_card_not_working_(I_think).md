---
title: "Graphics card not working (I think)"
date: 2009-07-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Evelyn on 2009-07-30
This has been a problem for about a week.  I've tried to fix it by searching the forums, however I have not found a solution.

When I first turn on the computer this is what I see (first 5 pictures).  There is nothing I can do except do a hard shut down.  The next time I boot up the computer, I press escape when I see the screen that looks like picture 3.  Then I see picture 6.  I select the recovery mode.  Then a bunch of type lines that go by too fast to take a picture.  Then picture 7 appears.  I select "Repair Broken Packages".  More type lines go by that I can't take a picture of then picture 8.  I press return.  Back to picture 7.  I select "Try to fix X server".  Then picture 9 appears.  Then back to picture 7.  I select "resume normal boot".  After more type lines go by I sometimes see picture 5 or a normal screen, but mostly I see picture 5.  Even if I see a normal screen and can log in, even then the mouse will all of a sudden have a box around it like in picture 10 which means I can move the mouse but it will not work and also the keyboard will not work.

I can only load five files/pictures below, but I hope someone can help me.  I don't know how to put the pictures in the thread, sorry.

How can this be fix?  Can someone please help me?

---

### Post by FirstByté on 2009-07-30
I'm not an authority on GDMs but, try running a LiveCD and see if the issues persist. If not, you might need to re-install your Ubuntu

---

### Post by Vakman on 2009-07-30
On screenshot three, press ESC and then choose recovery mode.
Drop to down to shell and reset the xserver to it's default.
```
sudo dpkg-reconfigure xserver-xorg
```
Then resume normal boot.

---

### Post by Evelyn on 2009-07-30
When I first turn on the computer this is what I see (first 5 pictures on the original post). There is nothing I can do except do a hard shut down. 

So here are the steps I have taken to try and fix this:
1.  The next time I boot up the computer, I press escape when I see the screen that looks like picture 3 (above on original post).  Then I see picture 6 (below as picture 1).

2.  I select the recovery mode. Then a bunch of type lines that go by too fast to take a picture. Then picture 7 (below as picture 2) appears.

3.  I select "Repair Broken Packages". More type lines go by that I can't take a picture of then picture 8 (below as picture 3). 

4.  I press return. Back to picture 7 (below as picture 2).

5.  I select "Try to fix X server". Then picture 9 (below as picture 4) appears. Then back to picture 7 (below as picture 2).

6.  I select "resume normal boot". After more type lines go by I sometimes see picture 5 (above in original post) or a normal screen, but mostly I see picture 5 (above as original post). 

Even if I see a normal screen and can log in, even then the mouse will all of a sudden have a box around it like in picture 10 (below as picture 5) which means I can move the mouse but it will not work and also the keyboard will not work.

---

### Post by Evelyn on 2009-07-30
"Thisislaw  	
Re: Graphics card not working (I think)
On screenshot three, press ESC and then choose recovery mode.
Drop to down to shell and reset the xserver to it's default.
Code:

sudo dpkg-reconfigure xserver-xorg

Then resume normal boot. "

I tried that and it didn't help.  The screens that came up were asking questions about the keyboard.

---

### Post by FirstByté on 2009-07-30
can you post:

```

/etc/X11/xorg.conf

```

and

```

~$ lspci -nn | grep -i vga

```

---

### Post by Vakman on 2009-07-30
> **FirstByté said:**
> can you post:

```

/etc/X11/xorg.conf

```

and

```

~$ lspci -nn | grep -i vga

```

Agreed, please post that.

---

### Post by Evelyn on 2009-07-30
"FirstByté  	
Re: Graphics card not working (I think)
can you post:

Code: /etc/X11/xorg.conf
and
Code: ~$ lspci -nn | grep -i vga"

I went to picture 7 above and then to root and entered the code. For both commands it said "No such file or directory"

I've had the computer since 2007.  Bought it with Fiesty Fawn version of Ubuntu on it from Dell.  Since then I've kept up on the updates and it is currently running version 8.04 of Ubuntu. Thus, I do not have a liveCD of Ubuntu.

Could this have anything to do with my computer problem? (see link) [http://ubuntuforums.org/showthread.php?t=990978&highlight=graphics+card](http://ubuntuforums.org/showthread.php?t=990978&highlight=graphics+card)

I didn't follow any of the instuction on the other thread, but I do have a nVidia graphics card.

---

### Post by Evelyn on 2009-07-31
Is there anything I can do to fix the problem?

---

### Post by Evelyn on 2009-07-31
> **FirstByté said:**
> can you post:

```

/etc/X11/xorg.conf

```

and

```

~$ lspci -nn | grep -i vga

```

I tried again to
```

/etc/X11/xorg.conf

```

and

```

~$ lspci -nn | grep -i vga

```

after the first I got "bash: /etc/X11/xorg.conf: Permission denied"
and after the second I got "bash: ~$: command not found"

Am I doing something wrong?

As far as I know, I'm in the root shell prompt.

---

### Post by FirstByté on 2009-07-31
@Evelyn:
How are you able to surf the net? Is it through the same computer? If yes,

Just enter this in a terminal
```

~$ sudo gedit /etc/X11/xorg.conf

```

a GEdit Editor should pop up. Then just copy the content and paste it here.

**Else**
Insert a flash drive in a usb port and enter this at the recovery console *(from the boot options at the beginning)*...
```

~$ sudo mkdir /media/myusbdrive
~$ sudo mount /dev/sdb1 /media/myusbdrive

~$ sudo cp /etc/X11/xorg.conf /media/myusbdrive

```
NOTE: depending on the number of usb stuff you have plugged in the 'sdb**1**' could be **1 or 2 of 3** one of them should work

That way you would have the file copied into your flash drive. Get Internet access anywhere and post the file's [*"xorg.conf"*] content here. 

Good luck!
And did you try the other command?

```
~$ lspci -nn | grep -i vga
```

---

### Post by truckerjay on 2009-07-31
I have a dell with and nvidia and I am having the same problem when I input those also have been trying to start the Xorg so far nothing works.  I get the same result.

---

### Post by Evelyn on 2009-07-31
Ok, I think I have the information that might help you help me.

I'm working through another computer to get to the internet.

I did ```
~# lspci -nn | grep -i vga
``` and it came back with 01:00.0 VGA compatible controller [0300]: nVidia Corporation G72M [Quadro NVS110M/GeForce Go 7300] [10de:01d7] (rev a1)

I also ```

~# sudo mkdir /media/myusbdrive
~# sudo mount /dev/sdb1 /media/myusbdrive

~# sudo cp /etc/X11/xorg.conf /media/myusbdrive

``` and the file has this on it: 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by FirstByté on 2009-08-01
@Evelyn:

Your nVidia driver is "G72M [Quadro NVS110M/GeForce Go 7300]". To make things pretty simple. You would have to remove any previous instance (installation) of nvidia-graphics-* drivers that *might* be on your system before installing this:

[B][http://www.nvidia.com/object/linux_display_ia32_185.18.31.html]("http://www.nvidia.com/object/linux_display_ia32_185.18.31.html")
[/B]
A post **[here]("http://ubuntuforums.org/showpost.php?p=6235436&postcount=1")** explains the HowTo [*To avoid duplication*]

@TrukerJay:
You might wanna give this a shot too.


Note: Most of the commands you'll be working on would be at the console [TTY] mode, so you are most advised to 
1. Download the driver in a path/folder you can easily remember/locate
2. Print out the instructions before you issue commands such as
```
~$ sudo /etc/init.d/gdm stop
``` or even "Ctrl + Alt + F1"
3. You might ensure you have all the necessary tools in;
```
sudo apt-get update
sudo apt-get install linux-kernel-hearders
sudo apt-get install linux-headers-generic
sudo apt-get install build-essential
sudo apt-get upgrade #this would update your sys if you haven't

```

---

### Post by Evelyn on 2009-08-01
Thanks, that looks like it might work only if I can get to the desktop on my computer that runs Ubuntu.  As it is I can't.  

~Is there a way those directions will work when all I can get to is the root shell in the recovery mode?
~How do I download the drivers?
~Can I download them onto a usb drive from a computer running Windows XP?
~Then how can I use them in the root shell that I can get to in the recovery mode?
~How do I remove any previous instance (installation) of nvidia-graphics-* drivers that might be on your system?

---

### Post by FirstByté on 2009-08-01
> **Evelyn said:**
> 
~Is there a way those directions will work when all I can get to is the root shell in the recovery mode?
~How do I download the drivers?
~Can I download them onto a usb drive from a computer running Windows XP?
~Then how can I use them in the root shell that I can get to in the recovery mode?
~How do I remove any previous instance (installation) of nvidia-graphics-* drivers that might be on your system?

Fine, if you can get any system that can get to the Net.

Just get to this link [**http://www.nvidia.com/object/linux_display_ia32_185.18.31.html**](**http://www.nvidia.com/object/linux_display_ia32_185.18.31.html**) and download the file into a flash drive. I might suggest you save the file in the root directory of your flash for easier access... *just my thought :)*
> 
[B]To download and install the drivers, follow the steps below:

STEP 1:[/B] Review the [**NVIDIA Software License**]("http://www.nvidia.com/object/nv_swlicense.html").

You will need to accept this license prior to downloading any files.

**STEP 2:** Download the Driver File

Download - [URL="http://us.download.nvidia.com/XFree86/Linux-x86/185.18.29/NVIDIA-Linux-x86-185.18.29-pkg1.run"]**NVIDIA-Linux-x86-185.18.29.pkg1.run**
[/URL]
**STEP 3:** Install
Type "sh NVIDIA-Linux-x86-185.18.29-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X server configuration file. Please see Chapter 3 of the [README]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.29/README/index.html") or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the [README]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.29/README/index.html"). 

Now if you've have downloaded the file and saved it in your desired location on the flash drive, you would need to 'mount' the usb drive at the recovery prompt [Just as done earlier].

NOTE: _You can always choose the recovery mode at the startup* (Drop down to shell)*_

```
~# sudo mkdir /media/myusbdrive
~# sudo mount /dev/sdb1 /media/myusbdrive

```

To remove any trace of previous nVidia stuff try this, dont worry if it returns errors: 'command not found'
```
~$ sudo nvidia-uninstall
```

[B] Go to the location on the usb that you stored the file you downloaded from nVidia's site:
[/B]```
~$ cd /media/myusbdrive
~/media/myusbdrive$
~/media/myusbdrive$ sudo chmod a+x NVIDIA*.run

```

Next
** Turn off X.org/GDM** (Gnome Display Manager): I doubt if it's gonna be necessary for you though.
```

~/media/myusbdrive$ sudo /etc/init.d/gdm stop

```
** Run the installer:**
```

~/media/myusbdrive$ sudo sh ./Nxxx.run

```
(If you hit TAB after the first N the rest of the filename will automatically appear. Remember, Linux is case sensitive)

[B] Choose x.org automatic configuration at the last step inside the installation program.

 Then restart your computer
[/B]
```

sudo reboot

```
 Enjoy!:popcorn:

For more: go [here http://ubuntuforums.org/showpost.php?p=6235436&postcount=1]("http://ubuntuforums.org/showpost.php?p=6235436&postcount=1")

---

### Post by FirstByté on 2009-08-01
A typo up there... the link should be 
[http://www.nvidia.com/object/linux_display_ia32_185.18.29.html]("http://www.nvidia.com/object/linux_display_ia32_185.18.29.html")

---

