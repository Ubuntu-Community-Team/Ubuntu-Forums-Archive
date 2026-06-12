---
title: "Can't run Compiz Fusion with Gusty Gibbon.."
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by zamurai on 2007-10-25
Hi, 

I just installed 7.10. I read that with 7.10, Compiz Fushion is enabled by default but I can't get it run on my laptop. I think the driver is not right. What kinda driver should I get?

Please help.



Thanx in advance.

---

### Post by jazzgossen on 2007-10-25
Depends on what graphics card you have. Is it an nVidia, ATI, or something else?

---

### Post by jffmetall on 2007-10-25
Hi,
 I've got the same problem...I've got a Mobile Intel Graphics Media Accelerator X3100 but the compiz fusione already installed on G.G 7.10 doesn't work.how can I make it work? thanks

---

### Post by Forlong on 2007-10-25
jffmetall, what's the ouput of ```
compiz
``` in a terminal?

---

### Post by zamurai on 2007-10-25
> **jazzgossen said:**
> Depends on what graphics card you have. Is it an nVidia, ATI, or something else?

I'm using NVIDIA Geforce Go 6200. So which driver should I get?

---

### Post by rundee_f on 2007-10-25
have u tried System > Preference > Advanced Desktop Effect on LiveCD before u install 7.10?

---

### Post by Forlong on 2007-10-26
> **zamurai said:**
> I'm using NVIDIA Geforce Go 6200. So which driver should I get?
If you're on GNOME, going to **System &#8594; Administration &#8594; Restricted Drivers Manager** and enabling the proprietary driver should do the job.

If it's already installed/enabled, post the output of ```
compiz
``` in a terminal.

---

### Post by jffmetall on 2007-10-26
Hi Forlong ,
the output of compiz in a terminal is>

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

What's up?how can I forward this problem?Can I right?

---

### Post by Forlong on 2007-10-26
> **jffmetall said:**
> Blacklisted PCIID '8086:2a02' found
That means you have problematic hardware, so Ubuntu has to blacklist it to prevent Compiz is run by default.
If you want to run Compiz anyhow, you have to run it like this:
```
SKIP_CHECKS=yes compiz
```
If it works see the 12th step [here](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support) (the steps before are about ATI but don't worry).

---

### Post by bkf3rreus on 2007-10-26
i get this cute series of characters..

i have disabled Xgl by putting a "disable" file in ./config/xserver-xgl/

SKIP_CHECKS=yes compiz (seems to do nothing..)

( i have i945 card and i810 driver)

```
:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'core'

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)
Fönsterhanterarvarning: "" som hittades i konfigurationsdatabasen är inte ett giltigt värde för tangentbindningen "toggle_shaded"

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)


```

---

### Post by Forlong on 2007-10-26
> **bkf3rreus said:**
> ```
(emerald:7054): Wnck-WARNING **: Unhandled action type (nil)
```
You're not on Gutsy, are you?

---

### Post by bkf3rreus on 2007-10-26
i am! :confused:

---

### Post by Forlong on 2007-10-26
> **bkf3rreus said:**
> i am! :confused:
Then you should update your profile.

I asked, because the libwnck bug has been resolved in Gutsy - did you upgrade from Feisty?

And please tell us what exactly is not working for you.

---

### Post by bkf3rreus on 2007-10-26
well compiz just doesn't start (it worked before the upgrade). gnome-control-panel > appearance > visual effects crashes when i try to choose anything but "nothing"

compiz config settings doesn't start, nor does the GL Desktop (in cp)..

i tried this one..

```

:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

---

### Post by bkf3rreus on 2007-10-26
heh.. fixed it

[This thread is great]("http://ubuntuforums.org/showthread.php?t=580063")

---

### Post by zamurai on 2007-10-26
Ran Compiz on terminal, and here's the results:


Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0167 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format





just hangs there and I have to cancel it, after that my bottom desktop bar hangs too.
I have to do a restart.....

---

### Post by jffmetall on 2007-10-27
Now it woks in the best way as possible!!!thanks a lot guy!:guitar:

---

### Post by b0rt on 2007-10-27
Hey guys, sorry to bother but i have troubles with my compiz con Gusty. I have alredy install the restricted drivers for mi Nvidia Geforce4 420 Go, but when I type compiz on the terminal, it doesnts work
```
bort@Leviathan:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0175 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity

``` 
Can Anyone Help me? any help will be apreciatted.

---

### Post by zamurai on 2007-10-27
> **bkf3rreus said:**
> heh.. fixed it

[This thread is great]("http://ubuntuforums.org/showthread.php?t=580063")



No luck for me. I don't know what's wrong...


Please help

---

### Post by kar0puz on 2007-10-28
Hi all,

Compiz does not work on Gusty with x3100 - it's blacklisted in compiz config. 

To make it work:

1. run   sudo gedit /usr/bin/compiz

2. find and comment string **T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965**  by adding **#** in front of the line

Then just enable visual effects and enjoy :)


:guitar:

---

### Post by ][soSo][ on 2007-10-28
i have the same problem 

compize is not running!! 

 i installed Cumpiz but when i click on CompizConfig Settings Manager it's not open!!
i don't know why!:confused:

Today i uninstalled all compiz packages and reinstaled it but it's still not run :(

this is my laptop [http://za.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=ZA&DISC_MODEL=0&highlightOption=94688&com.broadvision.session.new=Yes&PRODUCT_ID=114275](http://za.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=ZA&DISC_MODEL=0&highlightOption=94688&com.broadvision.session.new=Yes&PRODUCT_ID=114275)

i have ATI and installed xgl

and maybe this will help


```
S@Ubuntu:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

```
S@Ubuntu:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
S@Ubuntu:~$ 

```

---

### Post by MiniZiper on 2007-10-28
I have a similar problem...
but with a different output

```

chilean@chilean-gamer:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

---

### Post by Kaji on 2007-10-28
I am also having trouble getting Compiz Desktop Effects to run. on an 8800gts nVidia.

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2960x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 346 error_code 178 request_code 156 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)

```

That is my output from compiz

Running a dual monitor setup, 
Monitor 0: 21" Widescreen 1680x1050
Monitor 1: 19" Normal 1280x1024

---

