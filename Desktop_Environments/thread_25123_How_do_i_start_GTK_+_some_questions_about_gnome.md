---
title: "How do i start GTK? + some questions about gnome"
date: 2005-04-09
forum: Desktop Environments
---

### Post by cheniz on 2005-04-09
hi, i am a total beginner in linux.
is there an integrated development environment in gnome like kdevelop in kde?
there is not such a program listed in the applications menu.
i tried to install gtk, and it seems i did but it is still not in the applications menu.
why isn't it listed in the menu in ubuntu? i'm learning programming in C and it's a really important issue for me. 

another tiny problem, how do i change the color depth in gnome? there is an item in the preferences menu for screen resolution, but i couldnt figure out how to change the color depth. cause i think it's not 24bit by default

isn't there a control center in gnome like in kde, where i can see/change all the settings? 

maybe these are stupid, trivial questions but a real frustration for people like me who are new to linux/ubuntu.

thanks for help.

---

### Post by p!=f on 2005-04-09
[QUOTE=cheniz]hi, i am a total beginner in linux.
is there an integrated development environment in gnome like kdevelop in kde?
there is not such a program listed in the applications menu.
i tried to install gtk, and it seems i did but it is still not in the applications menu.
why isn't it listed in the menu in ubuntu? i'm learning programming in C and it's a really important issue for me. 
[/quote]
Sure...
> 
[~] > wajig show anjuta monodevelop
Package: anjuta
Priority: optional
Section: universe/gnome
Installed-Size: 2048
Maintainer: Rob Bradford <robster@debian.org>
Architecture: i386
Version: 1.2.2-6ubuntu1
Filename: pool/universe/a/anjuta/anjuta_1.2.2-6ubuntu1_i386.deb
Size: 863996
MD5sum: d683e9f8687088a71b453f5cfa433bb0
Description: A GNOME development IDE, for C/C++
 This IDE for C/C++ and GNOME/Gtk+ applications has features that enable easy
 debugging and management of code. It also integrates with glade and CVS.
 .
 [http://www.anjuta.org](http://www.anjuta.org)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

Package: monodevelop
Priority: optional
Section: universe/devel
Installed-Size: 5568
Maintainer: Debian Mono Group <pkg-mono-group@lists.alioth.debian.org>
Architecture: i386
Version: 0.5.1-3
Provides: monodoc-viewer
Filename: pool/universe/m/monodevelop/monodevelop_0.5.1-3_i386.deb
Size: 1570140
MD5sum: 1a84b82415597873d2c46add3eecfa06
Description: C#/Java/Nermele/ILasm Development Environment
 MonoDevelop is a GNOME IDE primarily designed for C# and other .NET
 languages.
 .
 Features: Debugger Integration, Class Browser, Monodoc Integration,
 Code Completion, Embedded HTML viewer, Gettext support, Java project support,
 Nemerle project support, ILAsm project support
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

Note: Section "Depends" cut to save some space...
[QUOTE=cheniz]
another tiny problem, how do i change the color depth in gnome? there is an item in the preferences menu for screen resolution, but i couldnt figure out how to change the color depth. cause i think it's not 24bit by default
[/quote]
Take a look at the /etc/X11/xorg.conf file, section "Screen"
> 
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34 [GeForce FX5200]"
        Monitor         "AOC HT731"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection


[QUOTE=cheniz]
isn't there a control center in gnome like in kde, where i can see/change all the settings? 
[/QUOTE]
gnome-control-center or use entries in your System menu
Feel free to ask and good times with Ubuntu.

---

