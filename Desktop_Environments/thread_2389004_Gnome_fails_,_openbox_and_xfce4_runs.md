---
title: "Gnome fails , openbox and xfce4 runs"
date: 2018-04-10
forum: Desktop Environments
---

### Post by ccarminati on 2018-04-10
Good day!

After an update, my Ubuntu 16.04.24 server doesn't run gnome anymore. Open-box and Xfce4 are fine (see attached files).

It didn't allow me to update log and conf files, so contents of xorg.conf  below:

```
Xorg.log
Section "ServerLayout"
 Identifier     "X.org Configured"
 Screen      0  "Screen0" 0 0
 InputDevice    "Mouse0" "CorePointer"
 InputDevice    "Keyboard0" "CoreKeyboard"
EndSection
Section "Files"
 ModulePath   "/usr/lib/xorg/modules"
 FontPath     "/usr/share/fonts/X11/misc"
 FontPath     "/usr/share/fonts/X11/cyrillic"
 FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
 FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
 FontPath     "/usr/share/fonts/X11/Type1"
 FontPath     "/usr/share/fonts/X11/100dpi"
 FontPath     "/usr/share/fonts/X11/75dpi"
 FontPath     "built-ins"
EndSection
Section "Module"
 Load  "glx"
EndSection
Section "InputDevice"
 Identifier  "Keyboard0"
 Driver      "kbd"
EndSection
Section "InputDevice"
 Identifier  "Mouse0"
 Driver      "mouse"
 Option     "Protocol" "auto"
 Option     "Device" "/dev/input/mice"
 Option     "ZAxisMapping" "4 5 6 7"
EndSection
Section "Monitor"
 Identifier   "Monitor0"
 VendorName   "Monitor Vendor"
 ModelName    "Monitor Model"
EndSection
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"            # [<bool>]
        #Option     "Rotate"              # <str>
        #Option     "fbdev"               # <str>
        #Option     "debug"               # [<bool>]
 Identifier  "Card0"
 Driver      "vesa"
 BusID       "PCI:10:0:0"
EndSection
Section "Screen"
 Identifier "Screen0"
 Device     "Card0"
 Monitor    "Monitor0"
 SubSection "Display"
  Viewport   0 0
  Depth     1
 EndSubSection
 SubSection "Display"
  Viewport   0 0
  Depth     4
 EndSubSection
 SubSection "Display"
  Viewport   0 0
  Depth     8
 EndSubSection
 SubSection "Display"
  Viewport   0 0
  Depth     15
 EndSubSection
 SubSection "Display"
  Viewport   0 0
  Depth     16
 EndSubSection
 SubSection "Display"
  Viewport   0 0
  Depth     24
 EndSubSection
EndSection 
```

---

### Post by TheFu on 2018-04-10
For troubleshooting, create a new userid. Logout, login going for gnome with the new userid.  Does this work?

---

### Post by ccarminati on 2018-04-10
Created new user.
Startx
Same error.

---

### Post by TheFu on 2018-04-10
Did you logout and login with the new userid?
I expected you'd be using gdm or some other login manager to select the DE/WM.

Does the xorg.log file show anything useful?

---

### Post by ccarminati on 2018-04-10
Xorg.log attached.

I logout and login again. TTY, no gui or gdm running...

---

### Post by ccarminati on 2018-04-11
Hi there.

My issue is either more complex or simple.

I can get lxde ,openbox, xfc4 to run but for some reason apps wont open.

Disk Analyzer, Virt-Manager, Firefox, etc  fail (no error, clicking doesnt do anything).

Filezilla, gimp and others run just fine.


Ideas?

---

### Post by TheFu on 2018-04-11
Open a terminal.
Run each program.
See the output.  What does it say?  Sometimes the error will clearly say what the issue is.  Fix it.
If not, Google for the error messages, hoping to find a solution. 

Don't expect a GUI popup error.

Did the xorg.log have anything interesting inside it?

---

### Post by ccarminati on 2018-04-11
xorg.log attached on one of my posts, no errors that could help....


Running Firefox and virt-manager on terminal returns nothing.... see attach

---

### Post by TheFu on 2018-04-11
Perhaps some library dependencies are missing? IDK. Would think errors would be seen in that case.
Sorry - I don't have any other ideas.

Is this a desktop install?

---

### Post by ccarminati on 2018-04-11
Server. Gnome was loading fine before the system was updated.... I can work without it, but virt-manager does makes things very easy since I have to constantly clone vms...Well... I will keep trying...

---

### Post by TheFu on 2018-04-12
Well, gnome usually means gnome3, but xfce4 is based on gnome2, which is why I asked to to make a new userid, logout and login using the new userid.  That also proved it wasn't config file conflicts for a single user. It is system-wide.

So, almost every program that has any failure will give error messages to stderr or stdout saying SOMETHING. Without that, it seems the system libraries are confused or missing to the point that some programs can't even be loaded. But since others are working (clearly), that removes incompatible libc and other system files.  Over the last few months, thanks to those Intel and AMD CPU bugs, there have been huge system-level changes between firmware updates, compiler changes and OS changes to combat those problems. Along the way, seems something on your system has been caught in a strange situation.  My best guess for how that might have happened is due to a manually installed .deb file that is holding some other files back so they can't be updated.  That is just a guess, but if you have manually installed a .deb file or 20, you have a choice to make.

I use virt-manager a little, but always from a different computer than my VMs are hosted.  Works the same, just graphics are a little slower due to the ssh+network overhead.  I don't use it for day-to-day needs, there are better tools for that which I find faster, especially for accessing a desktop, but for creating a new VM, I definitely use virt-manager.  I make new VMs about once a month and have to VM servers that run 16.04, while my main VM server is still on 14.04. I access these with virt-manager from 16.04 clients to perform VM management things that are possible through the GUI.  Some things are better done from shell - mainly storage management things, IMHO.

Probably nothing you didn't already know.

What are your choices to solve this? I have 3 ideas:
a) Backup whatever you can't loose, wipe the system and load a fresh 16.04.4.
b) Purge all GUI stuff (DEs,programs,settings,dependencies), including any manually installed .deb files and all GUI configs in your ~/, then reload which ever GUI you must have - pick only 1.
c) Use those versioned backups and restore the system from the day prior to the update that broke things. It is fairly easy to have 60-120 days of daily backups at this point. How long you need depends on the risk mitigation you feel is needed.  I treat VMs like physical machines, so I do not backup entire VMs as part of the host backups. I backup each VM separately. This makes backups for each just 1-3 minutes a day after the first backup version is completed.

Wishing you luck.

---

### Post by ccarminati on 2018-04-12
First thanks for your time and help.

In my case I create vms for distribution all the time,  virt-manager helps... I can live without, but it is good to have it. This server is currently running too many vms and at this point I cannot bring it down to reload the os (unless I tell them is an emergency, which would be a lie).

I removed gdm, gdm3, lightdm .... Which version of gnome would be the most basic? Dont need the OS to start in GUI, just need to be able to run a few apps once in a while...

---

### Post by TheFu on 2018-04-13
Can you not use remote X11 instead of running a full X11 stack directly on the system?  That would limit the libraries and their dependencies to only the X/Client ones, not the huge and more complex X/Server ones.

My VM hosts don't have a GPU, so all access is effectively remote.

XFCE is based on Gnome2.  Gnome2 isn't maintained as a DE anymore, at least I don't believe it is.

---

