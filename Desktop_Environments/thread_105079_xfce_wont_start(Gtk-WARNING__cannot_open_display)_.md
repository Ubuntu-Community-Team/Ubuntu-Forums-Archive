---
title: "xfce wont start(Gtk-WARNING **: cannot open display) - fresh xubuntu install"
date: 2005-12-17
forum: Desktop Environments
---

### Post by sup on 2005-12-17
hi, i tried to install xubuntu on my old computer (300mhz, 96MB of RAM) and all went fine - i was following the wiki howto - but when i run xfce4-session (I did not install gdm or kdm at first due to slowness of the computer, but when i tried and installed gdm, it didnot help anything)it prints out this:```
Gtk-WARNING **: cannot open display 
``` - i have probably something wrong with my setup, but i have no idea how to deal with it. Probably i should set up xfce (or xserver) somehow, but i have no idea what video driver I am using (which is I think the problem):-(. Any ideas how to get out of this?

---

### Post by aysiu on 2005-12-17
I don't what the Wiki page told you, but did you do a server install and then ```
sudo apt-get install xubuntu-desktop
```? If so, it should work...

---

### Post by sup on 2005-12-17
Yes, I followed this article [https://wiki.ubuntu.com/InstallingXubuntu]("https://wiki.ubuntu.com/InstallingXubuntu") and i did  server install and then sudo apt-get install xubunut desktop.

---

### Post by aysiu on 2005-12-17
So are you at a black screen with white text?
How about this? ```
startx
``` If that doesn't work, have you tried this? ```
sudo apt-get install kdm
```

---

### Post by psychicdragon on 2005-12-17
Xfce has it's own startup script called startxfce4.

---

### Post by sup on 2005-12-17
alright, with your help, I got so far. From command line I tried ```
startxfce4
``` which did not suceed in starting fce, but which told me where the problem was - it said my monitor does not support given colour depth. So I run ```
sudo dpkg-reconfigure xserver-xorg
``` and change it. Then I tried to run ```
xserver
``` and voila, xfce started loading and even form that I can say they are really fast. However, I ended up in X windows yet with resolution only of 320x200 or something. I tried to run terminal even though, but when I tried to type, whenever I hit a key, it appeared several times (ergo upon "k" "kkkkk" showed up). So I tried to reboot, but since I installed gdm (something I probably should not have), i ended up in exactly same situation. 

So, now I am facing a problem I think I know the direction in which I should solve it but I do not exactly know how. Several questions:
1)How do I boot up into command line without gdm even starting? (I need to hold some keys during boot up, right - which ones?)
2)Can I somehow determine which monitor and videocard I am using from command line? Dmesg does not give anything I can understand:-(.
3)How can I changethe resolution used by x-server from command line?

---

### Post by afhp on 2005-12-17
> 1)How do I boot up into command line without gdm even starting? (I need to hold some keys during boot up, right - which ones?)
Wrong, you can't stop it that way... but it doesn't matter because there are other ways. 
Let the system come up, then switch to a text console using Ctrl-Alt-Fn (By default you have 6 consoles available, on F1 through F6. Ctrl-Alt-F7 brings you back to X). Login there, then
```
sudo /etc/init.d/gdm stop
```
to stop gdm.

> 2)Can I somehow determine which monitor and videocard I am using from command line? Dmesg does not give anything I can understand:-(.
There's a lot in dmesg, it's easy to get lost... and it might be misleading in this case (for instance on my machine, dmesg shows that the system boots with a generic framebuffer, but X uses a hardware-specific driver).
What you want, then, is ```
lspci
```

For the monitor the simplest way is to locate its documentation -- either on paper or through Google. What you're looking for are the available horizontal and vertical refresh rates.

> 3)How can I changethe resolution used by x-server from command line?
You can't, directly. You have to edit /etc/X11/xorg.conf and restart X (which is not running after "gdm stop" above) -- or use ```
sudo dpkg-reconfigure xserver-xorg
```

Please post the output of lspci and your existing xorg.conf file here, we'll have a look.

---

### Post by sup on 2005-12-18
thank very much for your advice. After some swearing about someone suggesting me finding papers from my more-then-ten-year-old monitor;-), I turn on the internet and found what I needed:[http://www.griffintechnology.com/archive/monitors/Samsu07.html]("http://www.griffintechnology.com/archive/monitors/Samsu07.html") Somehow, when in 320x200 mode, alt+ctrl+fn did not worked, but when I switched keyboards (ps/2 instead of another more-then-ten-year-old one with a connector name of which I am far too young to know), I was able to type in the terminal (xwindows probably had some problem with the switch from that ooold connector to ps/2),so I killed gdm as you suggested, tried to run ```
sudo dpkg-reconfigure xserver=xorg
``` and ```
lspci
``` several time (and was blind to results of lspci:-D)and succeded with driver sis. Just for completenes, my lspci result:
```
root@viki:~# lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 620 Host (rev 02)
0000:00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)0000:00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) (rev b3)
0000:00:01.1 ff00: Silicon Integrated Systems [SiS] ACPI
0000:00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 11)
0000:00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0a.0 Communication controller: ESS Technology ES2898 Modem (rev 02)
0000:00:0c.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter (rev 2a)

```
as you can see, there is the needed driver named on almost the last line(and elsewhere).  DId not stop me from trying some other drivers starting with S (aka Silicon):-D. Well, luckily I finally got there.
My xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "cz"
        Option          "XkbVariant"    "qwerty"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "sis"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    8
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```
Although I run dokg-reconfigure...,  it can be easily edited by hand anv vim hand.

So, now everything works perfectly (I had to login as root for some reason, but I hope it is just for this session) but rather slow. (300MHz  and 96MB of RAM, free gives this:
```
root@viki:~# free
             total       used       free     shared    buffers     cached
Mem:         86404      84540       1864          0       1300      30680
-/+ buffers/cache:      52560      33844
Swap:       120448      55640      64808

```

How can I speed up the system? I will surely uninstall some packages I know I do not need (like dvdrw tools, this computer has not heard of DVDs yet:-D), but there are lots of libraries I know nothing about (a most of them wants to uninstall everything with them so I keep all of them installed). Yet as far as I know, this solves only harddisk space, to actually free up some RAM memory, I would need some modules not to load, right? Or wrong:-)? Where can I find some info related to this, I was trying to search Ubuntu forums, but I did not find anything really on topic...

---

### Post by afhp on 2005-12-18
[QUOTE=sup] (ps/2 instead of another more-then-ten-year-old one with a connector name of which I am far too young to know)[/QUOTE]

:D 

That would probably be an AT connector, if the machine is that old. Also known as 5-pin DIN.

> Although I run dokg-reconfigure...,  it can be easily edited by hand anv vim hand.

That's exactly what is so likeable about Linux. No matter the wizards and graphical configuration tools, there is always a text configuration file at the end, and some documentation somewhere. Ease of use not preventing ease of learning. 

> 300MHz  and 96MB of RAM, ...8<...
How can I speed up the system? 

If at all possible, add some memory. If you can go up to 128 MB, you'll already feel the difference. 

> to actually free up some RAM memory, I would need some modules not to load, right?

Right. Disable any daemons you don't need, don't try to multitask too much...  Can't really give you direct pointers, but in general forums, wikis, HOWTOs and so on should give you enough background to figure it out. I'll admit I never had
to fine-tune to such a level.

---

### Post by sup on 2005-12-18
Too painful that buying more memory would cost about as much as the whole computer does. But I will somehow figure out how to overcome it (will try to post some results here), when an application starts, it is actually usable, although it takes some time. It is just an old computer for my dad who wants to type some basic stuff, print it, get some photos from a digital camera, rename them (no tweaking) and maybe send some friends. He is actually sniffing about using linux instead of W95, but, well, I was not able to connect those damn windows to the internet, so I figured out it would be easier with linux:-D - and Ubuntu is the system I am using, so the choice was easy.

---

### Post by grumpymole on 2005-12-18
cancel

---

