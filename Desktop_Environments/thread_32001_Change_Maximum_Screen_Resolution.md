---
title: "Change Maximum Screen Resolution"
date: 2005-05-05
forum: Desktop Environments
---

### Post by davidmigl on 2005-05-05
Hello,

I just installed the latest release of Ubuntu on an old 233 mhz machine.  It has integrated video on the motherboard and (according to Windows 2000), can support 32 bit color @ 800*600 and 16  bit @ 1024*768.  The problem is that when I go into System -> Preferences -> Screen Resolution, the maximum resolution I can set it is 800*600.  I have a 17" CRT, and have run it at 16 bit 1024*768 in Windows before.  How can I set my monitor to run at 1024*768.

Yes, the code is correct in /etc/x11/xorg.conf:```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage II+ 215GTB (Mach64 GTB)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Thanks!

P.S. As a side question, what is the equivalent of a .bat file in Linux and how do I create one?  In Windows, when I needed to specify parameters for starting an application, I could simply type program.exe "-conf configfile.txt" in a .bat file.

You'll have to be very patient and explicit in your directions, as this is my first experience with Linux.

Thanks!!

davidmigl

---

### Post by nad on 2005-05-05
Any file in linux can be marked exectuable by simply changing the permissions. chmod a+x somefile  will mark it as executable by anyone. That being said, simply write your script, chmod your file and put it in a path known to your shell.

As far as passing parameters, read the manual page for the software. For the bash shell, this would be: man bash .

For information regarding your screen resolution problems, please see hundreds of posts here for suggestions and instructions.

---

### Post by GTvulse on 2005-05-05
It would seem that the monitor is not reporting its capabilities back to the video subsystem in the mobo, or the mobo itself does not support PnP (Plug-and-Pray) fully (BIOS setting?). You might try generating a new xorg.conf file. Boot up the machine in single user mode and when at the root prompt, type 

 ```
X -probeonly > /var/tmp/new-xorg.conf

``` 

Examine the resulting file, if the X server detected a higher resolution it would be there. Back up the old xorg.conf, overwrite it with the new one and reboot normally.

Else, you will need to write your own modeline definition. It is a dark art, but fortunately most of the work has been done already. See [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl") for an automated generator. As well, you may want to read this thread: [http://ubuntuforums.org/showthread.php?t=31712&highlight=modeline]("http://ubuntuforums.org/showthread.php?t=31712&highlight=modeline")  for further ideas.

--
Alejo

---

### Post by davidmigl on 2005-05-06
Ah. I think I'm on the right track.  In the last line of this section:```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage II+ 215GTB (Mach64 GTB)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
```, the default color is set to 24 bit, which the video card can only support at resolutions up to 800*600.  

I have edited the xorg.conf file, putting 16 as the default pixel depth.  The card can display 1024*768 at 16 bit color.  Now all I need to do is replace the old xorg.conf.  Could you walk me through how to do this?  I couldn't replace it within Gnome, because it was in use.  I also couldn't save anything to the /etc/x11 folder.  This is my first experience with linux, so I'm not too knowledgeable about it.

Thanks for all your help!!

---

### Post by GTvulse on 2005-05-06
This is what I do:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
sudo vim /etc/X11/xorg.conf [butcher the file... Change default depth to 16 bit]

```

And then I restart X by hitting ctrl-atl-backspace. Sometimes, in my setup at least, X hangs and you are left with a black screen, in that case, use the Vulcan grip (ctrl-alt-delete) and the box will reboot and come back again fine (unless you made a typo, you'll be kicked in console mode in that case; correct the typo in xorg.conf and rebooot. In fact, you don't need to reboot, but rather type "sudo xstart").

---

### Post by davidmigl on 2005-05-07
[QUOTE=dradul]This is what I do:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
sudo vim /etc/X11/xorg.conf [butcher the file... Change default depth to 16 bit]

```

And then I restart X by hitting ctrl-atl-backspace. Sometimes, in my setup at least, X hangs and you are left with a black screen, in that case, use the Vulcan grip (ctrl-alt-delete) and the box will reboot and come back again fine (unless you made a typo, you'll be kicked in console mode in that case; correct the typo in xorg.conf and rebooot. In fact, you don't need to reboot, but rather type "sudo xstart").[/QUOTE]
 Thanks for the help.  I'm still having some trouble getting it to work, though.  Please bear with me as I know these are dumb questions but I'm still new to Linux.

I get through the terminal commands well enough, but what do I do then?  Do I ctrl-alt-bkspc with the terminal still open?

Thanks!

---

### Post by GTvulse on 2005-05-07
> 
Thanks for the help. I'm still having some trouble getting it to work, though. Please bear with me as I know these are dumb questions but I'm still new to Linux.

I get through the terminal commands well enough, but what do I do then? Do I ctrl-alt-bkspc with the terminal still open?


Yes, if you do ctrl-alt-bkspc with the terminal open it will kill your logged in session and restart the X server. If for some reason it hangs there for a while, it means that the X server couldn't reset the video card (or chipset in your case, as you have an integrated mobo). If this is the case, you have two options:

1.  Hit ctrl-alt-del (the Vulcan grip) and do a forced warm reboot.

2. Hit ctrl-alt-F1 (in fact, F1 through F6 will do) to access one of the virtual console sessions, log in as your user and then do a warm reboot the "right" way with the command below. BTW, ctrl-atl-F7 corresponds to the graphical session.

```

sudo shutdown -r now

```

Does a clean system reninitialization.

---

### Post by davidmigl on 2005-05-10
Awesome.  There's only one more issue now.  I have the desktop running in 1024 x 768, but the refresh rate is only 60hz - something that drives me nuts.  I know this box can do 1024* @ 75 hz, since that's the way it was in windows.  Is there any way to get around this?

Thanks!!


EDIT: nm, I found what I was looking for in another thread.  It's working now!  Thank you all!

---

### Post by az on 2005-05-10
you can do 
sudo dpkg-reconfigure -plow xserver-xorg
from the command line or use synaptic (select the package and do configure from the drop down menu.)

There you can change all your settings for the package. This way, when the package gets updated, the file you modified by hand does not get clobbered since the values are rewritten by debconf.

---

