---
title: "/usr/local/bin/compiz: not found"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by Disillusion on 2007-10-21
Does anyone know a fix for this problem? Compiz hasn't worked since I upgraded to gutsy. I think there was a problem with ubuntustudio-menu, but I removed it and it is still doing this.

```
compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2704x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found
```

---

### Post by Disillusion on 2007-10-22
Nobody knows anything about this?

---

### Post by pilsna on 2007-10-23
I haven't been able to run compiz since the upgrade either. My error message is similar:

> $ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


---

### Post by ChiaGod on 2007-10-28
Hey, check to see that you have two things enabled in your xorg.conf located in:

/etc/X11/xorg.conf 

1) in a section called **Module** if you have it you may have other things in there, but apparently the line "**Load "glx"**" was missing 

Section "Module"

    Load           "glx"

EndSection

2) Then in the section Extensions there should be an option to enable Composite: 

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

I followed that advice from:
[http://ubuntuforums.org/showthread.php?t=526957](http://ubuntuforums.org/showthread.php?t=526957)

and now my compiz is up and running (granted I had to launch it twice...)

---

### Post by smcintyre on 2007-12-21
I had this message after upgrading to ATI fglrx 7.12.
This fixed it:

change lines 30 and 31 to:
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/"

and then a few lines down, change to:
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real)

Before, these lines said:
COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/"
...
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real)

Hope this helps.

---

### Post by ravenon on 2007-12-21
Nice tip smcintyre. I had just updated to the ati 7.12 driver and was happy that suspend and hibernate now work on my X700. But suddenly compiz was failing and for exactly the reason you provided. Bravo!

---

### Post by electro1984 on 2007-12-22
install on my ATI 600 pro driver 7.12 and was problem on compiz run and write file gedit /usr/bin/compiz
This fixed it:

change lines 30 and 31 to:
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/"

and then a few lines down, change to:
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real)



 OK it is now my full efect in Compiz =D>=D>:biggrin:

---

### Post by VeN0mizer on 2008-01-19
Thank you so much! the changed worked well :)

---

### Post by coldthunder on 2008-02-03
Thanks a ton ! I installed the ATI x1400 driver 8.45.4 on Gutsy and was stuck at this problem. Modifying the above three variable values has solved the problem for me.

> **electro1984 said:**
> install on my ATI 600 pro driver 7.12 and was problem on compiz run and write file gedit /usr/bin/compiz
This fixed it:

change lines 30 and 31 to:
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/"

and then a few lines down, change to:
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real)



 OK it is now my full efect in Compiz =D>=D>:biggrin:

---

### Post by StampU on 2008-02-05
Woot!
Finally.  That fixed my problem.

Thanks

---

### Post by Weazl on 2008-02-14
Thanks, this finally fixed the problem for me too. Although it does seem to run awfully slow on my HD 2600RX. I'm talking about 2fps...

---

### Post by Visitor.Q on 2008-04-27
Very nice, after an update from gutsy to hardy heron using a laptop with ATI (fglrx) videocard, compiz desktop effects did not work anymore (desktop effects could not be enabled). After a lot of searching, I found this, so editting the compiz file worked. Hopefully people stuck with this problem will find this solution.

---

### Post by niekko on 2008-05-03
Brilliant! This worked also with my Thinkpad T60 with ATI X1300. I upgraded from Gutsy to Hardy.

---

