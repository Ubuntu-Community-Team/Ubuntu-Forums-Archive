---
title: "KDE resolution issue"
date: 2009-11-13
forum: Desktop Environments
---

### Post by lang79james on 2009-11-13
KDE~not to my liking
[IMG]http://jameslang-world.com/files/print2.png[/IMG]

Gnome~more to my liking but KDE :tongue: 
[IMG]http://jameslang-world.com/files/print1.png[/IMG]

Now how to I make in KDE looks like Gnome?
Meaning that every thing is not big, well not huge. 
It is not just Ubuntu I have have tried other flavers. 

Computer:
The video card I am running is:
Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
Unbuntu 9.10 

Have both Gnome and KDE installed and want to try out KDE for a bit. I have search and found something of promise about editing the xorg.conf but can not find it.

In thinking that default-display-manager in the X11 would be it. To my very shock it was not and got the command prompt instead. Luckily I know about vi and was able to fix that.

---

### Post by lang79james on 2009-11-14
bump, any ideas please......?

---

### Post by pataphysicianu on 2009-11-14
Click on the K start button, choose "System Settings",click on "Appearance" and then click on the "Fonts" icon (you might have to scroll around as somethings will be large) on that screen you'll see a selection for "Force font DPI", change it to "96 DPI", and hit "Apply" button, you'll need to relogin for it to effect things that have already been loaded.

---

### Post by Tickborn on 2009-11-14
Uhm.. i had similar problem s while using Kubuntu, but everything was too small. You should play with font size and with DPI (but as far as i know DPI should be not a  problem when you using a standard monitor.
So what about going to System settings->Appearance->Fonts and chancge the size of all fonts?

---

### Post by pataphysicianu on 2009-11-14
> **Tickborn said:**
> Uhm.. i had similar problem s while using Kubuntu, but everything was too small. You should play with font size and with DPI (but as far as i know DPI should be not a  problem when you using a standard monitor.
So what about going to System settings->Appearance->Fonts and chancge the size of all fonts?

It's the DPI, it is a problem sometimes with the default system resolution that is used by kubuntu, if you run on the command line.

xdpyinfo | grep resolution

You'll get the resolution the kubuntu system thinks your screen is at, if it is incorrect, you'll need to force the DPI to 96. my guess is it will say 305X339 DPI, a massively huge DPI.

---

### Post by pataphysicianu on 2009-11-14
Another tip, after you install kubuntu-desktop, you will probably notice that your firefox fonts suck, both in kubuntu and ubuntu. This is due to a .fonts.conf being added by the kubuntu-desktop install. It's not needed and it screws up firefox fonts. So check out firefox and see, then if you want to get rid of the horrible look, either delete the .fonts.conf file in your home directory or maybe rename it to .fonts.old just in case you want to bring it back.

---

### Post by lang79james on 2009-11-14
> **pataphysicianu said:**
> It's the DPI, it is a problem sometimes with the default system resolution that is used by kubuntu, if you run on the command line.

xdpyinfo | grep resolution

You'll get the resolution the kubuntu system thinks your screen is at, if it is incorrect, you'll need to force the DPI to 96. my guess is it will say 305X339 DPI, a massively huge DPI.

Is there a way to change the DPI by command line??

Update 
I ran the xdpyinfo | grep resolution on both gnome and KDE and it came out both being 112x968

---

### Post by pataphysicianu on 2009-11-14
> **lang79james said:**
> Is there a way to change the DPI by command line??

Update 
I ran the xdpyinfo | grep resolution on both gnome and KDE and it came out both being 112x968

This doesn't matter for Gnome Desktop or Ubuntu as they ignore the X server dpi setting. Gnome is set to default to 96dpi, though you can change it to anything you want quite easily. Fonts tend to be made to be displayed at 96dpi or 120dpi so can look bad if not set to those dpi.

KDE looks at the Xserver dpi by default, which is often very wrong. To change KDE to force the proper dpi, you can also edit a KDE configuration file located under you home directory in a hidden file.

the file is:

~/.kde/share/config/kcmfonts


Make a backup of the file, then try the nano editor(or any editor you wnat) in the command line while in ubuntu gnome:

```
nano ~/.kde/share/config/kcmfonts
```

My file looks like this, change your file to match

```
[General]
dontChangeAASettings=true
forceFontDPI=96

```

Save it, and then go into KDE to see if it has changed.

---

### Post by lang79james on 2009-11-14
Thanks that did it. I knew it was something simple like that :P

---

### Post by Zorael on 2009-11-15
> **pataphysicianu said:**
> KDE looks at the Xserver dpi by default, which is often very wrong. To change KDE to force the proper dpi, you can also edit a KDE configuration file located under you home directory in a hidden file.

the file is:

~/.kde/share/config/kcmfonts
This will work but won't affect KDM (nor other users). A system-wide alternative would be to add '-dpi 96' to the server arguments used when starting X. But obviously, this would necessitate root privileges.

In **/etc/kde4/kdm/kdmrc** (excerpt);
```
# Additional arguments for the X-servers for local sessions.
# This string is subject to word splitting.
# Default is ""
ServerArgsLocal=-br -nolisten tcp **-dpi 96**
```

---

### Post by pataphysicianu on 2009-11-15
> **Zorael said:**
> This will work but won't affect KDM (nor other users). A system-wide alternative would be to add '-dpi 96' to the server arguments used when starting X. But obviously, this would necessitate root privileges.

In **/etc/kde4/kdm/kdmrc** (excerpt);
```
# Additional arguments for the X-servers for local sessions.
# This string is subject to word splitting.
# Default is ""
ServerArgsLocal=-br -nolisten tcp **-dpi 96**
```

Thanks Zorael, I was wondering though if that would work even if your not using kdm? Do you know if it does?

When you install kubuntu-desktop ontop of ubuntu like the OP, it asks what you want to use, gdm or kdm, and defaults to a selection of gdm, which is what I used. I assume the OP did as well, or they would have noticed the massive fonts at the login screen.

---

### Post by Zorael on 2009-11-15
> **pataphysicianu said:**
> Thanks Zorael, I was wondering though if that would work even if your not using kdm? Do you know if it does?

When you install kubuntu-desktop ontop of ubuntu like the OP, it asks what you want to use, gdm or kdm, and defaults to a selection of gdm, which is what I used. I assume the OP did as well, or they would have noticed the massive fonts at the login screen.
I don't know where gdm starts X or keep its arguments defined, really. Googling after examples of gdm.conf however I find the following;
```
# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 
flexible=true
```
Perhaps Ubuntu's current gdm.conf still has similar entries, and you can just append **-dpi 96** to the command line?

```
# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 **-dpi 96**
flexible=true
```
I don't know where under /etc/ you'll find gdm.conf. /etc/gnome/gdm.conf? 
```
$ cd /etc
$ find -name gdm.conf
```

---

