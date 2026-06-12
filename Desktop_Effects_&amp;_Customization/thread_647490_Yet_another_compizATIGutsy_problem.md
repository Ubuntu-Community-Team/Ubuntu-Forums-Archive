---
title: "Yet another compiz/ATI/Gutsy problem"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by daylond on 2007-12-22
I have an HP dv8000 with an ATI Radeon Xpress 200m video card.  I never tried using compiz before, but saw it at a local linux user's meeting and decided to give it a try.  Enabling it from System->Preferences->Appearance gives me a "desktop effects could not be enabled" warning.  I went to the terminal and tried "compiz --replace".  Here's the output:

```
dhooper@Onesimus:~$ compiz --replace
Checking for Xgl: xvinfo: symbol lookup error: /usr/X11R6/lib/libXv.so.1: undefined symbol: XextFindDisplay
not present. 
AIEEEEH, no Log file found 
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfffef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  5/2    threshold:  2
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /home/dhooper/.gnome2/share/cursor-fonts,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/,/home/dhooper/.gnome2/share/fonts
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Display is not capable of DPMS 
Blacklisted PCIID '1002:5955' found 
aborting and using fallback: /usr/bin/metacity 
```

I assume the source of my problem is in the symbol lookup error in the first line.  So I reinstalled Xorg, libxv1, and libxext6.  No change to the problem.  Running xvinfo gives me the same error. Any ideas?

---

### Post by divague on 2007-12-22
i have that same card, if you want to run compiz you have to install xserver-xgl, logout and then login, and now you can enable desktop effects
hope it helped

---

### Post by daylond on 2007-12-22
Actually, I did that already, too.  I forgot to mention it.  Thanks for the suggestion, though.

---

### Post by divague on 2007-12-22
which driver did you installed the one that comes in the ubuntu repos or another?
Because in that error ther's a line that says "Blacklisted PCIID '1002:5955' found" i had that problem when i was using the ati driver that i downloaded from ati's web site, and the solution i found for that was this, in a terminal i typed
$ sudo gedit ~/.config/compiz/compiz-manager (it's a new file)

and in that file typed SKIP_CHECK=yes

---

### Post by daylond on 2007-12-22
I'm using the restricted driver that I selected from the restricted drivers manager.  Using the Xorg driver worked fine on Feisty (I don't do much 3D stuff), but is painfully slow on Gutsy.  Here's the additional results of running Compiz with the SKIP-CHECKS switch:

```
Blacklisted PCIID '1002:5955' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: xvinfo: symbol lookup error: /usr/X11R6/lib/libXv.so.1: undefined symbol: XextFindDisplay
not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

---

### Post by daylond on 2007-12-22
This part of it looks like it goes back to the ATI graphics driver thing.  I guess I'll look at that. [http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654) appears to have another approach and I'll give it a shot.

---

### Post by Saint Angeles on 2007-12-22
the new restricted drivers (fglrx) dont need xgl... it now uses AIGLX...

download the newest fglrx from [www.ati.com](www.ati.com) , remove xgl, then add this to your /etc/X11/xorg.conf:
```

Section "ServerFlags"
        Option "AIGLX" "true"
EndSection

```
also make sure composite is enabled. i'll attatch a copy of my xorg.conf...

---

### Post by daylond on 2007-12-23
Well, I have it "working" now. I reinstalled the ATI restricted driver and it's now giving me appropriate 3D acceleration. However, now my desktop starts up with a white screen. I can see the menu bars and the splash screen, but when it goes away my desktop flashes up then turns white.  I can see the mouse move around and the menu bar still, until I click on something.  Then the item also turns white with the mouse cursor still visible.  I can load up fine using a failsafe GNOME session.  I've tried miscellaneous xorg.conf edits, and have even performed a removal of Compiz to see if Compiz was the source of the problem.  Most of the white screen stuff I've seen in other forums relates to Compiz/Beryl, and I assume this ties into a desktop manager, also. I'll try the server flags entry in xorg.conf from above, and if that doesn't work, I guess I'll try a reinstall of Metacity and see where things go from there.

---

