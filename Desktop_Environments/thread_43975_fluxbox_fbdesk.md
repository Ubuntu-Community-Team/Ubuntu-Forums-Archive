---
title: "fluxbox fbdesk"
date: 2005-06-24
forum: Desktop Environments
---

### Post by trash on 2005-06-24
I just can't figure out what i'm not understanding in the readme file, so can somebody help dummy this up a bit?
On starting fluxbox I have no desktop icons but if i run 'fbdesk' from a shell i get the single desktop icon as explained in the readme. I'm guessing that somewhere i need to tell fbdesk to start. I guess could place it in a startup script that I have made for my transparent eterm but I kinda want to know the right way... thanks

```
From README: Usage: ./fbdesk [option] 
Option:    
-rc    (default: ~/.fluxbox/init)    
-display     -na     disables antialias    
-v      show version 
To execute the icon command: double click on the icon. 
To bring up icon menu: right click on the icon.  

Resource file:  
fbdesk.iconFile:  filename to icon file (default: ~/.fluxbox/fbdesk.icons)
fbdesk.font: icon font name (default: fixed) 
fbdesk.textColor:  color for icon text  (default: black) 
fbdesk.snapX: x snap size (default: 5) 
fbdesk.snapY: y snap size (default: 5) 
fbdesk.doubleClickInterval: time interval between clicks for a 
double click (default: 200) 
fbdesk.textPlacement: placement for text around icon image  (default: Bottom) 
# Possible values for text placement: Left, Right, Top and Bottom 
session.styleFile: style file for menu (default: none) this one is 
read from ~/.fluxbox/init   

Icon file format: 
# this is a comment 
# Start of one icon entry 
[Deskop Entry] 
Icon=the image filename 
Name=the icon label 
Exec=what it executes 
Pos= 123 456  # position of the icon 
[end] # end of one icon entry  

example:  
[Desktop Entry] 
Icon=/usr/share/pixmaps/gnome-home.png 
Name=aterm 
Exec=aterm 
Pos= 100 100 
[end]  

Note: To make FbDesk use the same style as fluxbox you need to put the 
resource  items in the same file as Fluxbox resource file (~/.fluxbox/init) If the 
icon file is missing or empty, FbDesk will create a single default  
icon on position 64 64.
```

---

### Post by eskaypey on 2005-06-24
There are three ways you can start programs on start up in fluxbox --

[list]
Editing the user's ~/.fluxbox/startup. [/list] 
[list]
Editing the user's .xinitrc. [/list] 
[list]
Using another bash script to be run everytime flux starts. [/list]

---

### Post by trash on 2005-06-24
cool thanks,
I'm using 

session.screen0.rootCommand:	~/startup.sh

in the ~/.fluxbox/init so that works. Kinda wierd that fluxbox would install a sample icon file but no startup file, thats what made me think i'm missing something.

---

### Post by eskaypey on 2005-06-24
Fluxbox creates ~/.fluxbox/startup directory with the first use of "startfluxbox".

---

### Post by trash on 2005-06-24
ok finally got a ~/fluxbox/startup... way better! fbdesk is great, thanks.

---

### Post by trash on 2005-06-24
spoke too soon, any idea's why my ~/fluxbox/startup is not being used at startup?
it seemed to work before I rebooted.

---

### Post by trash on 2005-06-25
in the end what did work best was to put stuff in a ~/.xsession file:

fbdesk
eterm...
startfluxbox

---

