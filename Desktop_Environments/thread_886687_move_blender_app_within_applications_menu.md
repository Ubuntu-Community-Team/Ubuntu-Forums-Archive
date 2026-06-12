---
title: "move blender app within applications menu"
date: 2008-08-11
forum: Desktop Environments
---

### Post by groundnut on 2008-08-11
I have added Blender manually (via desktop preferences / behaviour) to the applications menu. At this moment it's not in a folder.

How can I move it into the graphics folder of the applications menu?

---

### Post by x1a4 on 2008-08-11
Hi,

You can't.  Instead create a launcher (.desktop file) in /usr/share/applications and make sure that **Categories** is set to **GTK;Graphics;**
An example of a launcher would be:
```

[Desktop Entry]
Version=1.0
Name=Blender
Comment=3D modeller/renderer
GenericName=Blender
Exec=blender %F
Icon=blender
Terminal=false
Type=Application
Categories=GTK;Graphics;
StartupNotify=false
MimeType=image/png;image/gif;image/jpeg;image/bmp;image/x-ico;image/x-pixmap;image/tiff;

```
Modity to fit Blender.

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by groundnut on 2008-08-12
Thanks x1a4,

This is to messy for me. I gave it a try but I failed.

For me it's not really a problem that Blender doesn't sit in the Graphics folder. It would have been more elegant though.

---

### Post by x1a4 on 2008-08-12
My fault.  I'm not always sufficiently clear in my instructions.  Here's what you do:

1) In your home directory, create a file called [color=blue]blender.desktop[/color]

2) Using your favourite editor (gedit for example) paste the following into the file:
```

[Desktop Entry]
Version=1.0
Name=Blender
Comment=3D modeller/renderer
GenericName=Blender
Exec=[color=red]/path/to/blender[/color] %F
Icon=[color=red]/path/to/icon[/color]
Terminal=false
Type=Application
Categories=GTK;Graphics;
StartupNotify=false
MimeType=[color=red]image types supported by blender[/color]

```

Where [color=red]/path/to/blender[/color] enter the blender executable.  Best if you include the full path.  I think that's 
[color=blue]/usr/bin/blender[/color] if you installed it from the repos. Than again if you had this wouldn't be an issue.

Where [color=red]/path/to/icon[/color] is the icon you want to use.

Where [color=red]image types supported by blender[/color] are all the mime types (file types) supported by Blender separeated by a semicolon.

Once your launcher is complete, save the file, then open a terminal and move it to [color=blue]/usr/share/applications[/color].  
```
sudo mv ~/blender.desktop /usr/share/applications
```

---

### Post by groundnut on 2008-08-13
I quit.

I failed again. Still to messy.

Thanks anyway x1a4.

---

