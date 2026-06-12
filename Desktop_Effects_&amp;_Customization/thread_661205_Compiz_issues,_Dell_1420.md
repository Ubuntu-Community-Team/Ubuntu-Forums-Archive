---
title: "Compiz issues, Dell 1420"
date: 2008-01-07
forum: Desktop Effects &amp; Customization
---

### Post by Penguinnerd on 2008-01-07
I just got a Dell Inspiron 1420 with ubuntu. 

I got the standard graphics card (Intel x3100)
1 Gb Ram
80 Gb Hard drive
1.66 Ghz core 2 duo
And the hi-res glossy screen.

When I try to enable desktop effects, it says simply: "Desktop effects could not be enabled"

So what's wrong with it? I've tried changing the screen resolution and it doesn't help.

---

### Post by sowelie on 2008-01-07
Run compiz in a console and post the output.  I'm not familiar with getting it working on intel cards.  But there's a lot of info on it out there. It may be as simple as enabling the composite extension in xorg.  Posting your xorg.conf may also reveal the issue.

---

### Post by Penguinnerd on 2008-01-07
alan@dell-desktop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 


I located a file titled xorg.conf (Yes, I'm still a noob) and here are it's contents.

# bare-bones XFree86 config to start the server in probe-only mode
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	RgbPath		"/etc/X11/rgb.txt"
EndSection
Section "ServerFlags"
	Option "AllowMouseOpenFail"
EndSection
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"vbe"
EndSection
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection
Section "InputDevice"
	Identifier	"Generic Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
EndSection
Section "Device"
	Identifier	"Generic Device"
	Driver		"::DRIVER::"
EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Generic Mouse"
EndSection


Thanks for the help so far.

Edit: there is not really a smiley face in the contents of xorg.conf  Obviously that is something the site did.

---

### Post by sowelie on 2008-01-07
Okay so you don't have the correct driver set up it sounds like.  I am unsure how to go about this with your intel card.  But, to get started go to system -> administration -> restricted driver manager.  If there is a video driver listed there enable it and see where that gets you.  If that doesn't work we'll have to find an article to get the correct driver installed.

---

### Post by Penguinnerd on 2008-01-07
There are two restricted drivers installed and both were already enabled.

one is the "Conexant modem engine" and the other is "Intel(R) PRO/Wireless 3945 Network Connection driver for Linux"

Maybe I should post something under the Dell section of the forum?
I'll look for an article on the driver now.

---

### Post by Penguinnerd on 2008-01-07
I just realized that it is supposed to be a 1420 N.
There don't seem to be any markings implying that it is. It just says 1420. 


Edit: I just noticed the sticker that says that it is N series. Nevermind.

---

### Post by sowelie on 2008-01-07
Looks like you need to install the xserver-xorg-video-intel package.  If this doesn't work there are other options.

EDIT: I think the above suggestion get your graphics drivers straightened out but there may be more to do to get compiz working, check out [this]("http://knowledge76.com/index.php/GutsyCompizIntelX3100") article for more info.

---

### Post by Forlong on 2008-01-08
> **Penguinnerd said:**
> alan@dell-desktop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
Try running Compiz like this: ```
SKIP_CHECKS=yes compiz
```
Tell me if it worked.

---

### Post by sowelie on 2008-01-08
Ah, I just noticed too that the xorg.conf you posted was the wrong one.  That's a template.  The correct one is /etc/X11/xorg.conf.  You probably already have the drivers installed and my just need to follow the directions in the above post.

---

### Post by Penguinnerd on 2008-01-08
I'll try all that stuff when I get home from school in several hours. Thanks.

---

### Post by Penguinnerd on 2008-01-08
Okay, sorry it took so long, I had something else planned after school.

Forlong: "SKIP_CHECKS=yes compiz" solved the problem.

Is there anything I need to do inorder to make it permanent?

---

### Post by Forlong on 2008-01-08
So I guess it does work, right?

Then do this:
```
gedit ~/.config/compiz/compiz-manager
```
Put the command in there:
```
SKIP_CHECKS=yes
```
And save.

---

### Post by Penguinnerd on 2008-01-08
Okay, thanks! That works. 

Now, time to enjoy the fact that my Ubuntu system looks better than Winblows Vista... (And works better)

---

### Post by Penguinnerd on 2008-01-08
Oh, wait. I rebooted and it's not working anymore. It still worked after the first reboot...

I looked at ~/.config/compiz/compiz-manager again and it still says SKIP_CHECKS=yes.

Am I supposed to add compiz to the end? (SKIP_CHECKS=yes compiz)

---

### Post by Penguinnerd on 2008-01-08
I added "compiz" to the end of "SKIP_CHECKS=yes" in  "~/.config/compiz/compiz-manager" and it definitely didn't help. 

It put dashed lines accross the screen. I got it back to the way it was, but I still can't make compiz permanent."

---

### Post by Forlong on 2008-01-09
No, do not add 'compiz' there!

Remove that again (so there's only 'SKIP_CHECKS=yes') and post the output of
```
compiz
``` in a terminal again.

---

### Post by Penguinnerd on 2008-01-09
alan@dell-desktop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by Forlong on 2008-01-09
There's no error message. What exactly is not working for you?

---

### Post by Penguinnerd on 2008-01-09
When I close the terminal window Compiz closes too. I want it to be working by default on startup. (and preferably with no terminal window open)

---

### Post by Forlong on 2008-01-09
Just go to *System &#8594; Preferences &#8594; Appearances &#8594; Visual Effects* and enable them there.

---

### Post by Penguinnerd on 2008-01-09
Oops, I guess I must have posted twice or something.

---

### Post by Penguinnerd on 2008-01-09
Thanks for all the help, that seems to have worked. I had already tried that, but It didn't work. After some updates and a reboot it seems to be working.

That solves everything.

---

### Post by coulamac on 2008-02-25
> **Penguinnerd said:**
> Thanks for all the help, that seems to have worked. I had already tried that, but It didn't work. After some updates and a reboot it seems to be working.

That solves everything.

Just checking: what did you do again?  When I try to enable compiz on my 1420n stderror gives me the following:

Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

The terminal also spits out the following:

/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this is not going to work

/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display 0:0
Window manager warning: Workarounds for broken applications diabled.  Some applications may not behave properly.

Ater this, the manager reverts to Metacity, and I cannot change the Desktop effects setting.

Any clues?  I already set SKIP_CHECKS to yes.

Thanks in advance.

~Andrew

---

### Post by Virgilius on 2008-03-01
I seem to have a problem since Compiz isn't working permanently. I type in "Compiz" from the Terminal, and I get this:
> Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
 Any reason why it's doing this? Oh, wait, don't worry, I found a "solution" here: [http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4434057#post4434057]("http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4434057#post4434057")

---

