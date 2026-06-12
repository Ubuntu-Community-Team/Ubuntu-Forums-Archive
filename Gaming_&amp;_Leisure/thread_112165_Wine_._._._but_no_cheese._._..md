---
title: "Wine . . . but no cheese. . ."
date: 2006-01-03
forum: Gaming &amp; Leisure
---

### Post by cptncatholic on 2006-01-03
I've installed the latest version of wine under ubuntu and edubuntu. I'm trying to get my son's edubuntu machine set up to play his pc games (like, Reading with Pooh, Thomas the Tank Engine, etc. -- not anything like halflife or warcraft). 

Here's what I've done so far:
1. Added the sourceforge repositories to sources.list
2. sudo apt-get update
3. sudo apt-get install wine
4. Wine installed successfully.
5. Inserted CD
6. cd /media/cdrom
7. wine Setup.exe
8. Installation successful
9. cd "~/.wine/drive_c/Program Files/Disney Interactive/Ready to Read with Pooh/"
10. wine Launcher.exe

At that point, the screen goes black and changes to 640x480, but an error window opens saying that the screen resolution must be set to 256 colors. So after closing the window and resetting my resolution back to where it was, I read the following errors in the terminal window:

```
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel(0x7fdc8c38)->(0x10022,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
```

I've searched the forums and google, but I can't seem find anyone who has fixed this error. Maybe I'm not looking in the right places, but my New Year's day off has already been eaten up trying to solve this issue. Any help or direction from you knowledgeable people would be very much appreciated!

Update: Someone mentioned that I should update Xserver to run in 256 color mode by updating the XF86Config file. Is this safe to do without breaking Ubuntu?

Thanks!
tc

---

### Post by akiro.yamamoto on 2006-01-03
Try this....
At the desktop <ALT>+<F2>
Type "winecfg"
Click > Add Application
Browse to the Seteup.exe file.... click Add
Click the Graphics Tab
Un Check > Enable Double Buffering
Then you can select the color depth for that app. at the top.
You can also try Emulate Virtual Desktop If you need a certain screen size for that app as well....
I hope this helps....
As always however..... YMMV....
:smile:

---

### Post by akiro.yamamoto on 2006-01-03
Post back with any error messages you get.....

---

### Post by akiro.yamamoto on 2006-01-03
EDIT:  Browse to the Launcher.exe file not Setup.exe :smile:
From your post it seems that you got it installed correctly....

---

### Post by cptncatholic on 2006-01-03
Thanks! Getting closer ... maybe.

Making your changes in winecfg gave me the following output:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
Major opcode of failed request:  1 (X_CreateWindow)
Serial number of failed request:  23
Current serial number in output stream:  30
```

not sure what this means...
tc

---

### Post by akiro.yamamoto on 2006-01-03
OK let me do a little checking....
Will post Back with anything I find that may help.
BTW...
Did you use the Emulate Virtual Desktop setting and setting it to the size the prog. needed.
The only other thing I can think of in the interim is setting the desktop to 8bpp 
which is really going to suck! and setting it back..... ;-)

---

### Post by akiro.yamamoto on 2006-01-03
Perhaps you should try the CVS version of TransGaming software....
I've heard that it provides much better graphics support that the default wine software.

---

### Post by akiro.yamamoto on 2006-01-03
Enable Double Buffering
Use the Emulate Window Setting.
Leave The color depth as blank....
Wine should create the screen and dynamically provide the correct color depth to the game....

---

### Post by jonny on 2006-01-03
The games that you mention hardly stress the graphics subsystem so you might get adequate performance with qemu if you have a valid Windows licence hanging about.

I've had some success running simple games under qemu.  My kids have quite enjoyed  revisiting a number of games that stopped working when we upgraded our solo Windows PC to XP from 98 a few years back.  It's a little ironic that the only way I can now get those old programs to run is by using Linux!

---

### Post by cptncatholic on 2006-01-04
Jonny: Your suggestion to use qemu sounds good. But after looking at qemu, it seems like I would be duplicating my initial attempts to install win98 in VMware. I have two copies (with licenses) of Win98, but the first one is on a Gateway CD that will only install Win98 on a Gateway computer. And the second is on the HP Recovery CD that initially came with my son's computer, however trying to install it under VMware makes the CD think that it's not on a HP computer and the install is aborted.

Now, if there's a workaround for this, I could just follow through with that plan. Playing with the winecfg file is not getting me anywhere. Sorry, Akiro!

There was a day when I had just a straight Windows98 install cd (with license) but I don't know where that CD got to. Probably self-destructed as per Microsoft's plan when they decided to no longer support it.

Peace!
tc

---

