---
title: "Totem Broken after installing ATI Binary Drivers"
date: 2005-11-09
forum: Desktop Environments
---

### Post by sciurus on 2005-11-09
When I first installed Breezy, xorg.conf included the following:

Section "Module"
Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

When I reconfigured after installing fglrx, I wasn't sure what modules to include. I went with the ones listed below based on their inclusion in the ouput of an online tool for generating xorg configurations using fglrx:

Section "Module"
Load "dbe"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "type1"
EndSection

My problem is that xvimagesink no longer works. Could this be caused by my current module configuration? I can't find enough documentation online to tell what each module does, so I don't know what to add or remove. For now I changed my video output in the multimedia systems selector to XWindows(no xv), but it seems jerky.

---

### Post by Kyral on 2005-11-09
I had the same problem. I just reenabled all the modules that were there before :P

---

### Post by sciurus on 2005-11-21
Now I have

Section "Module"
	Load	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"type1"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"int10"
	Load	"vbe"
EndSection

and it still doesn't work ("fails to construct pipeline").

---

### Post by sciurus on 2005-11-25
I reverted to the orginal modules, still no luck. My "solution" was to switch to mplayer, which has smooth playback even without xv.

---

