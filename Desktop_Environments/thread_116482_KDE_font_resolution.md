---
title: "KDE font resolution"
date: 2006-01-12
forum: Desktop Environments
---

### Post by Rumpty on 2006-01-12
Running a clean install of Kubuntu. Monitor resolution 1024x768. In the quest for nicer looking fonts, I have been trying to change the system resolution to 96dpi, without success. Had no trouble doing it in Ubuntu (Gnome) which is on another partition, but in Kubuntu, no luck.

Tried the DisplaySize 270 203 entry in xorg.conf, which worked in Ubuntu, but it has no effect in KDE on my machine. Then I tried putting -96 dpi into the ServerArgsLocal line in /etc/kde3/kdm/kdmrc. This changes things, but the result is strange. With the entry -96 dpi, xdpyinfo reports a resolution of 77x72 dpi. If the -96 dpi entry is changed to (for instance) -124 dpi, xdpyinfo reports a resolution of 99x93 dpi! (After rebooting)

Can anyone tell me what is going on, and why I don't get the expected resolution please? Should I expect xdpyinfo to report 96x96 with the -96 dpi entry in kdmrc, or have I got things wrong?

---

### Post by skript on 2006-01-13
Yes, you should expect xdpyinfo to display 96x96 dpi after adding the -dpi 96 parameter to kdmrc... At least that's how I got it to work, but I have no idea why it isn't working in your setup... good luck anyway !

---

### Post by obibok on 2006-01-13
Double check that you put *DisplaySize 271 203* in *Section "Monitor"*. Instead of 270, try 271 or more (276, 280,... experiment). Same for the other value.

---

### Post by Rumpty on 2006-01-13
Thanks for the tip. I'll experiment more with the numbers.

---

### Post by mo_x on 2006-01-14
Maybe the dpi is calculated for the wrong screen resolution.
Can you post /etc/X11/xorg.conf and /var/log/Xorg.0.log (as attachments).

---

### Post by pelle.k on 2006-01-14
Sorry for hijacking this thread, but the issue i'm having is <kindof> the same.
Everytime i make a clean install, using the nv driver gives me the correct font size. And also, everytime i install the "nvidia" driver all fonts get rather big. This bugs the *hell* out of me really, and i havent figured out how to get my old state back. why, is this happening?
I dont think DisplaySize was set before, and it isn't now so what made the difference... 
As always, any suggestions would be greatly appriciated.

---

### Post by obibok on 2006-01-14
[QUOTE=pelle.k]Sorry for hijacking this thread, but the issue i'm having is <kindof> the same.
Everytime i make a clean install, using the nv driver gives me the correct font size. And also, everytime i install the "nvidia" driver all fonts get rather big. This bugs the *hell* out of me really, and i havent figured out how to get my old state back. why, is this happening?
I dont think DisplaySize was set before, and it isn't now so what made the difference... 
As always, any suggestions would be greatly appriciated.[/QUOTE]

Yep, the *nv* driver does that indeed. I solved the oversized font issue by setting *DisplaySize* to get 96dpi.

---

### Post by codejunkie on 2006-01-14
[QUOTE=pelle.k]Sorry for hijacking this thread, but the issue i'm having is <kindof> the same.
Everytime i make a clean install, using the nv driver gives me the correct font size. And also, everytime i install the "nvidia" driver all fonts get rather big. This bugs the *hell* out of me really, and i havent figured out how to get my old state back. why, is this happening?
I dont think DisplaySize was set before, and it isn't now so what made the difference... 
As always, any suggestions would be greatly appriciated.[/QUOTE]
i was having the same problem with my nvidia card using the latest nvidia driver on debian stable and heres how i fixed it, the same steps should work just fine with ubuntu also.
edit your /etc/X11/xorg.conf file and scroll down to the "Device" section and add this after the BusID
```
	Option		"UseEdidDpi" 		"FALSE"
```
it should look something like this
```

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseEdidDpi" 		"FALSE"
	Option		"NoLogo"
	Option 		"RenderAccel" 		"true"	
EndSection

```
then follow the steps here [http://www.ubuntuforums.org/showthread.php?t=20976](http://www.ubuntuforums.org/showthread.php?t=20976)
to find the display size option for your resolution
i use 1024x768@85hz so mine would be 
```
	DisplaySize	270	203
```and add that to the "Monitor" section mine looks like this
```

Section "Monitor"
	Identifier	"COMPAQ FS7600CPQ"
	HorizSync	30-70
	VertRefresh	50-160
	Option		"DPMS"
	DisplaySize	270	203
EndSection

```
save the file and restart the xserver now when you run
xdpyinfo | grep resolution
it should display 
resolution:    96x96 dots per inch
hope this helps.

---

### Post by pelle.k on 2006-01-15
I acctually followed this guide
[http://www.ubuntuforums.org/showthread.php?t=68779&highlight=large+fonts+nvidia]("http://www.ubuntuforums.org/showthread.php?t=68779&highlight=large+fonts+nvidia")
yesterday, wich is essentially what you recommended, but it didn't work. But with your UseEdidDpi option it did :)

> Option          "UseEdidDpi"            "FALSE"

Thanks man, you  truly are my hero ;)

---

### Post by obibok on 2006-01-15
Instead of calculating *DisplaySize*, apparently you can simply set DPI in a clear way:

```
Option   "UseEdidDpi"   "FALSE"
Option   "DPI"   "96 x 96"
```

I haven't tested this but if you want to give it a shot and post your comments, others could learn something too :smile:

---

### Post by Rumpty on 2006-01-17
mo x, sorry I have not posted for a couple of days. Work intervened, or my wife was using the computer.

Here are my two files, xorg.conf and xorg.0.log. See what you think, and thanks for your help.

---

### Post by RaisedFist on 2006-01-17
[QUOTE=obibok]Instead of calculating *DisplaySize*, apparently you can simply set DPI in a clear way:

```
Option   "UseEdidDpi"   "FALSE"
Option   "DPI"   "96 x 96"
```

I haven't tested this but if you want to give it a shot and post your comments, others could learn something too :smile:[/QUOTE]
I did this and it didn't work. Only with DisplaySize it worked...

---

### Post by mo_x on 2006-01-17
You said you are running the display at 1024x768. Can you remove "1280x1024"from the Modes lines in your xorg.xonf and then try again. Maybe also try again with -dpi server option.

---

### Post by Rumpty on 2006-01-17
mo x, your information worked nicely. I removed the 1280 x 1024 entry from the modeline(s) in xorg.conf, and changed the ServerArgsLocal line in /etc/kde3/kdm/kdmrc to -96dpi, restarted X and all was as expected. xdpyinfo now reports 96 x 96dpi.

So the X server takes its default resolution info from the first entry in the modeline? Is that how it works? And then for some reason my ServerArgsLocal entry wasn't changing it properly to 96 x 96dpi. Beyond me, but you sorted it out. Many thanks.

---

### Post by pelle.k on 2006-01-17
I'm impressed! rock on :D

---

### Post by mo_x on 2006-01-18
The virtual resoltion was set to 1280x1024, which showed in the Xorg.0.log, probably because it was the largest available resolution. I think X currently can not change dpi when changing resolution.

---

### Post by pelle.k on 2006-02-08
*I'll post this, as it worked for me. Really simple for you newbs...*

The resolution i am using is the >first< one in the mode lines. (in my case 1400x900). I only used the option:
```
Option          "UseEdidDpi"            "FALSE"
```
in my nvidia device section (/etc/X11/xorg.conf of course), restarted, and now xdpyinfo reports:
```
screen #0:
  dimensions:    1440x900 pixels (488x305 millimeters)
  resolution:    75x75 dots per inch
```
which is exactly how i want it. KISS!

---

### Post by f1dave on 2006-02-09
[QUOTE=Rumpty]mo x, your information worked nicely. I removed the 1280 x 1024 entry from the modeline(s) in xorg.conf, and changed the ServerArgsLocal line in /etc/kde3/kdm/kdmrc to -96dpi, restarted X and all was as expected. xdpyinfo now reports 96 x 96dpi.

So the X server takes its default resolution info from the first entry in the modeline? Is that how it works? And then for some reason my ServerArgsLocal entry wasn't changing it properly to 96 x 96dpi. Beyond me, but you sorted it out. Many thanks.[/QUOTE]

Yep, it pretty much worked the same way for me. From my /etc/kde3/kdm/kdmrc file: 
```

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-nolisten tcp -dpi 96
ServerCmd=/usr/X11R6/bin/X
```

And outputted from xdpyinfo | grep resolution :
```
  resolution:    96x96 dots per inch
```

So yeah, I've fixed mine up now too, after killing my X server once :P

---

