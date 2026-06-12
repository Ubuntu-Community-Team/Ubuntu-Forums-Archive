---
title: "Help with Gutsy and Compiz Problem"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by thermg on 2007-10-27
Hi All,

I am having some problems with running Compiz Fusion on my Gutsy Setup. The desktop spec is:

AMD 3800+ X2 (AM2)
1GB RAM
250GB HDD (SATA)
ATI X600 PCI-E Graphics Card

I have installed the ATI drivers successfully and all appears to be working after following the thread below:

[http://ubuntuforums.org/showthread.php?t=575843&highlight=gutsy+ati]("http://ubuntuforums.org/showthread.php?t=575843&highlight=gutsy+ati")

The output:

```
ross@ross-ubuntu704:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.0.6747 (8.40.4)
```

and:
```

ross@ross-ubuntu704:~$ glxinfo | grep direct
direct rendering: Yes
ross@ross-ubuntu704:~$ 
```

I followed this guide to install compiz fusion:

[http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html]("http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html")

The guide seems to work fine with no errors at any stage. The problem I get is that when I run compiz fusion by typing "compiz --replace gconf" in the run application, the window bars are removed from the top as shown in this screenshot:

[IMG]http://i91.photobucket.com/albums/k319/thermg_1982/Screenshot.png[/IMG]

I was wondering if this is a known problem with ATI cards and Compiz or if I have missed something. Can anyone help to get the top bars back please.

Thanks,

TheRMG

---

### Post by thermg on 2007-10-27
If I try to start compiz from the terminal, I get this output:

```
ross@ross-ubuntu704:~$ compiz --replace gconf
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
```

Not sure If it would help but I thought what the heck the more info the better.

---

### Post by DJSpeed on 2007-10-27
Same problem here, please help.
I also add to xorg.conf this lines:

```

Section "Extensions" 
    Option "Composite" "1" 
EndSection

```

---

### Post by jimerickso on 2007-10-27
make sure aiglx is enabled in /etc/X11/xorg.conf

Section "ServerLayout"
	Option		"AIGLX"	"True"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	
EndSection

---

### Post by thermg on 2007-10-27
Hi,

My xorg.conf files looks like this:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection
```

So do I just add the line for AIGLX?

Cheers

---

### Post by thermg on 2007-10-27
I added that line to the xorg.conf file but the problem still remained. Any ideas why? I rebooted the Xserver with ctrl+alt+backspace. I also tried changing it to fglrx but no luck either.

Any help greatly appreciated.

Cheers

---

