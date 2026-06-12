---
title: "desktop effects problem"
date: 2009-06-16
forum: General Help
---

### Post by saposhcoffz on 2009-06-16
so i used wubi to install ubuntu tonight, but i'm having problem getting the desktop effects to work, i get the error, "desktop effects could not be enabled". i have managed to install compiz though...and when i use SKIP_CHECK i get this:

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Segmentation fault
Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

i'm not very linux savy, so i've come here for help. what is the problem? is my driver blacklisted?:(

---

### Post by mk1w86 on 2009-06-16
Are you using the binary drivers for your graphics card?

To check go to System >> Administration >> Hardware Drivers

Also what graphics card are you using?

---

### Post by 3rdalbum on 2009-06-16
What graphics card do you have?

The part that worries me about your post is this sentence: "i have managed to install compiz". Compiz is preinstalled - it has been preinstalled in Ubuntu for over a year. Have you followed an old HOWTO of "How to install Compiz on Ubuntu"? If so, then your Compiz is probably too old to work on Ubuntu today.

---

### Post by Villiam on 2009-06-16
May be your driver does not support texture_from_pixmap and thus cannot run compiz properly. You have to use the open source driver (if you can) or use Xgl. Install the xserver-xgl package, logout, and when you login it'll be running and compiz should automatically start (unless you turned it off).

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by abhilashm86 on 2009-06-16
maybe you download compiz-check and run, it'll tell which went wrong while running compiz..........[http://forlong.blogage.de/entries/2008/4/28/Introducing-Compiz-Check--a-script-to-test-and-troubleshoot-your-Compiz-install](http://forlong.blogage.de/entries/2008/4/28/Introducing-Compiz-Check--a-script-to-test-and-troubleshoot-your-Compiz-install)

---

### Post by mhgsys on 2009-06-16
please post output of lspci. (open a terminal and type; 

```

lspci | grep VGA

```

---

### Post by saposhcoffz on 2009-06-16
hi, thanks for all the input, and to answer all those questions:

all i get shown up under hardware drivers is software modem, which for some reason can't be enabled....my graphics card is 
an Intel Corporation Mobile GM965/GL960

and apparently wubi did not come preinstalled with compiz, so i had to manually do that

i've tried searching for xserver-xgl but for some reason synaptic can't find it? i'll have to manualy download it- hope it works!

lspci resulted in :00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)- which would be my graphics card i presume

i also tried compiz check script and here's what i got: Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
_____


thanks for all your advice

---

### Post by Mka on 2009-06-16
I am also having a similar problem, so I'll stay glued to this thread. I am using a Sony VAIO VGN290P laptop. lspci gives me:
```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
```

I downloaded the compiz-check script and here is its output:
```
~$ compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

and glxinfo fails with this output:
```
~$ glxinfo 
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

I am trying to be as more verbose as possible. Running compiz on terminal gives:
```
~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

What is this "texture_from_pixmap"? Oh, I am using the default xorg.conf file now since at some point I messed everything up and couldn't log in.

I've read a lot of threads but seem to be much more concerned with ATI/nVidia cards ... adapting similar advices didn't work.

---

