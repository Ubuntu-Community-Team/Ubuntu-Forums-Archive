---
title: "xorg.conf messed up, how to restore?"
date: 2009-02-06
forum: General Help
---

### Post by UranUtan on 2009-02-06
Hi,

I installed a Windows games under Wine. The game started OK but changed the graphic in full screen. After that I go to System, Preference, Screen Resolution. And changed the resolution.

Then the screen becomes blank (like video cable unplugged). I had to power off. After reboot, I have tried a few tricks found on various forum. For example: sudo dpkg-reconfigure -phigh xserver-xorg

But the problem is unchanged. here is the content of my xorg.conf

```
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
```

The video chip is Intel 865G. It works perfectly well, even Visual Effects in "Extra" mode.

Now I have a blue Ubuntu color and the GUI seems to be downgraded and any change to screen resolution is ignored. When changing the Visual effects from None to Normal, I got an error msg "Desktop effects could not be enabled".

While trying the Appearance again, this time the blue skin becomes orange like before but the screen resolution is squished. Looks like the video card is acting on its own.

What is the reason for Ubuntu to decide to change randomly the graphic mode like that? And more importantly is there any way to put the display setting back like before?

So far I can survive a lot of changes from Windows to Ununtu. But when it comes to these graphics bizarreries I am totally frustrated. Please save me from a nervous break down because I don't have time to reinstall everything a 3rd time.

Thanks very much for any help.

EDIT: the weird graphics issue (squished display, ugly fonts) seems to be specific to the user. When logging out, the login screen look nice and one of the user account is not affected by this graphic problem.

---

### Post by UranUtan on 2009-02-07
Any help please?

---

### Post by daengbo on 2009-02-07
The easiest way to handle this is probably deleting the Wine directory, which is in your home directory (abbreviated ~/). You can either use the command line:
> rm -R ~/.wine
or you can open Places > Home, In the window, select View > Show hidden files, and delete delete the .wine file.

When you are finished, fire up Wine configuration and set the configuration in the Graphics tab to run in a virtual desktop of 800x600. 

In the end, you'll need to re-install the game and try again.

Not all games work on Wine. In fact, only about a third work really well. Adventure Inlay (your game) says it requires Win2000 or Win98. Try changing the Wine configuration to Win98 and see if that helps. If the game has serious graphical artifacts, you're probably better off trying a different one. WineHQ's AppDB can help you determine which ones work. PlayonLinux is a Wine helper which can make playing games easier.

Adventure Inlay is a puzzle game. [These puzzle games]("http://games.ibeentoubuntu.com/search/label/Puzzle") have been tested and seem to work well.

---

### Post by UranUtan on 2009-02-08
Hi,

Thanks again for your valuable help. Deleting the .wine folder seems to help a little bit. Now I can change the screen resolution. But if I try changing the screen resolution several times then I end up with a blank screen where Ctrl-Alt-Backspace cannot restart XServer. So basically, among all the possible resolution, there is only one choice which is working. All the other choices either cutoff the bottom, switch the display to black, or simply does nothing.

I have made a lot of searches on the Internet, most of time people fix their issue with dpkg-reconfigure xserver-xorg. I am maybe the only one in the world who have this weird graphics issue, with two totally different computers. Each time it happened after a Windows game is executed under Wine. I think I am done with this exercise. If ever I touch these games again, it will be inside a Virtual Machine running XP. I understand that WINE cannot do miracle to run everything from Windows. But to wreak havoc in the graphics system is something it should not do. Just to make sure that WINE will not interfere with the computer any more, I have removed it completely. Unfortunately the graphics issue still remains.

This weird graphical issue drives me nuts, I am so pissed off that I am actually willing to pay for someone to help me fix this issue. Just for the curiosity to understand the cause. But I will probably go faster by reinstalling Ubuntu again.

---

### Post by unutbu on 2009-02-08
> ... the weird graphics issue (squished display, ugly fonts) seems to be specific to the user. When logging out, the login screen look nice and one of the user account is not affected by this graphic problem.

This implies I think, that the problem is coming from a configuration file that resides in the (problematic) user directory. 

You might want to try moving the .gconf and .gnome2 directories:
```

mv .gconf .gconf_20090208  # This backs-up your originals
mv .gnome2 .gnome2_20090208  # so they are easy to restore
```

Then log out and log back in. GNOME will recognize that these directories are missing, and will regenerate new .gconf and .gnome directories for you. Your GNOME settings (such as background image and theme) will be lost, but perhaps so will the resolution problem.

If this solves the problem, and you would like to find out exactly what inside those directories is causing the problem, then you could post those directories here, and I could "diff" them. (To post a whole directory:

```
tar  cf  gnome2.tar  .gnome2/
tar  cf  gconf.tar  .gconf/
```
Then attach gconf.tar and gnome2.tar to a post.)

If that is successful, we can create a script to fix the problem without having to move the entire .gnome2 and .gconf directories.
Perhaps this way, you could continue using wine.

---

### Post by UranUtan on 2009-02-08
Hi unutbu,

You are the man! deleting .gconf and .gnome2 has fixed the problem. There are still some oddities: 

1. Visual Effects is now "None". Setting to Normal or Extra return a warning dialog form "Desktop Effects cannot be enabled". Before that this computer was able to run Extra mode, but I set it to Normal.  

2. "Screen Resolution" setting screen: I think this issue had always exist. Sometime it could detect the monitor name and display a lots of screen resolutions. I picked "1280x960". After the resolution is set, going back to "Screen Resolution" setting screen now show Unknown monitor and barely a few resolutions "1360 x 768", "1152 x 864", "1024 x 768", "800 x 600", "640 x 480". There is no more "1280x960".

So far, I don't know the factors that make the "Screen Resolution" settings recognise (or not!) the monitor and various screen resolutions.

Attached is gconf_gnome2_BeforeAfter.zip that contains the .gnome2 and .gconf before and after. Hope you can see anything useful.

There is no need to write a script to fix the problem. I have wasted enough of your time already. Deleting .gnome2 and .gconf is simple enough. All the display settings (background, fonts, etc.) which are lost are not important. I could redo them manually.

Thank you very much for your help.

---

### Post by daengbo on 2009-02-08
My apologies. Somehow I understood that you were having problems configuring the virtual desktop resolution in Wine. I must've had a brain fart that day.

---

### Post by daengbo on 2009-02-08
WRT your new problem of no acceleration with the intel driver, that happened a few months back during an update, too, and was only fixed recently. Maybe there's a regression.

---

