---
title: "Xgl and Beryl Problems- Ati mobility 9600 Pro Turbo M10"
date: 2007-02-25
forum: Desktop Environments
---

### Post by Brooklyn on 2007-02-25
Hello, I need some help setting up Xgl and beryl on Ubuntu Edgy Eft.  I followed these guides for install of ati drivers and xgl/beryl:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

[http://wiki.cchtml.com/index.php/XGL-Ubuntu]("http://wiki.cchtml.com/index.php/XGL-Ubuntu")

When I start an Xgl session, during startup the screen goes gray and the pointer becomes an "X".  It still boots up, and everything looks like my regular gnome session when it is finished.  Here are some responses I get from commands in terminal in that session:

jon@jon-laptop:~$ ps -e | grep Xgl
 5737 ?        00:00:00 Xgl


jon@jon-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)


jon@jon-laptop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
jon@jon-laptop:~$ 

Here is a little bit of info from my xorg.conf that you might need:

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection


When I try to change to Beryl from Metacity from the drop down menu on the desktop, the screen goes white.  My pointer is still there, but I just have to end up turning off my computer.  Could anyone help me in my situation?  Are there any other 3d-desktop programs that are similar that I might be able to run?  Also, I am not sure what versions of Xgl and Beryl I am running.

Also, I should note I am using a Dell Inspiron 8500 laptop 2.2ghz Pentium 4m, 1gb ram, 128mb ATI mobility radeon 9600 pro turbo (M10).

Thanks!

---

### Post by lemoniceblock on 2007-02-25
To solve the white screen problem you can either type in the terminal
```

beryl-manager --no-force-window-manager
beryl-xgl --use-copy

```

or

```

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &

```

I think the 'use copy' method is more sluggish while the LD_PRELOAD is definitely smoother but I've had my computer crash randomly (and sometimes it doesn't crash at all) using either those methods anyway =P  Will let you know if I find a way to resolve the crashes.
An alternative 3d desktop program would be compiz but I had problems loading that with fglrx.

---

### Post by Brooklyn on 2007-02-25
Ok, thanks for the reply!  Using the first method, beryl will run, however whenver I close the terminal window beryl crashes.  Also the second method did not work.  The use copy method is sluggish, but at least now I can get a feel for beryl.  Any other advice would be greatly appreciated as well.

Thanks.

EDIT:  I tried the second method again and it worked, and its less sluggish(I forgot to run the first command first).   Again, when I close terminal, beryl crashes.  Is there anyway to run the second method along with running beryl on startup?  Also, have it so I don't have to keep the terminal window open?

---

### Post by Brooklyn on 2007-02-25
OK, I created an executable script file with the 2 commands, and set it to run on startup.  Now beryl runs on startup!  Hurray!

---

### Post by lemoniceblock on 2007-02-25
=^^= That's great!  I really like Beryl so in spite of all the hassles I'm quite determined to keep using it xD  I'm not too sure about the terminal.  Once I left the terminal open and worked on another face of the cube and there were no crashes.  When I was about to switch off my computer I turned back to the terminal and there were actually lines of words that came after 'reloading options'.  So I've left my terminal open after that and so far there hasn't been more crashes (I'm still waiting and seeing though =P ), but then again, I haven't seen those words again on the terminal.  Now it just says 'reloading options' and if I want to type anything in the terminal, I have to open a new one alongside.  I've been trying to get the LD_PRELOAD stuff to run as I log in but I don't know anything about scripts ^^;;  Would it be ok if you posted that script up?  Thanx~

---

### Post by Brooklyn on 2007-02-26
By the way, when I used the script, I didn't have to keep terminal open.  All the script file contained was:

```
beryl-manager --no-force-window-manager
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &
```

Just type in terminal: sudo gedit berylstartup

Then enter the commands in the file.  Save the file somewhere you want, I just put mine in my home directory.  Then make it executable by either logging in as root, going to properties of that file, and select allow execution or whatever.  Or type in terminal

```
$ sudo chmod 755 /directory/where/file/is/berylstartup
```

Then goto sessions in preferences, and goto startup programs.  select the file you just made, and then beryl should start at your next startup.

---

### Post by Brooklyn on 2007-02-26
I've been trying to get a screen shot, but somethings screwed up in taking screenshots of xgl/beryl.  You should check this out anyway, it like a work of art, lol.

[IMG]http://img83.imageshack.us/img83/6839/screenshot2ja8.png[/IMG]

---

### Post by lemoniceblock on 2007-02-27
W00t, got it working thanx!~
I think I've set my Beryl cube to rotate too quickly to take a screencap xD  But the 'reflection' of Tux on the bottom face of the cube is cool~  Was that on purpose or accidental?  Either way, it's a cool effect ^^  Very Cubist/Picasso-like! xD
Also, to reconfirm (this was before I used the startup script), keeping the terminal open with LD=PRELOAD is no guarantee against crashes.  And about the 'words' that came after 'reloading options' mentioned earlier, I caught a glimpse of them again and managed to copy them: 
> 
beryl: pixmap 0x160465a can't be bound to texture
core: bind Window(): XGetWindowAttributes() returned non-success.  Window: 0x2C09BD
core: bind Window(): XGetWindowAttributes() returned non-success.  Window: 0x2C03C2
core: bind Window(): XGetWindowAttributes() returned non-success.  Window: 0x2C0369

I don't think that their appearance in the terminal is some "foreteller of doom" though because I have crashed without seeing those lines, and I have seen those lines without crashing =P
I've just started using the script so I can't say if it solves the crash problem or not, but I'll be keeping an eye out and fingers crossed!  Thanks again for posting that up :)

---

