---
title: "Firefox, strange menu font...."
date: 2006-11-19
forum: Desktop Environments
---

### Post by mazu on 2006-11-19
Is it possible to change font in firefox? I'm using KDE, I've changed fonts in KDE control Panel, Gnome Control panel (as far as I know forefox uses GTK+), but the font remains the same. Here is a screenshot firefox and Konqueror with the systen font.

[[IMG]http://img20.imageshack.us/img20/8278/screenje2.th.jpg[/IMG]](http://img20.imageshack.us/my.php?image=screenje2.jpg)

Maybe someone had a symilar problem?

---

### Post by rfruth on 2006-11-19
A different theme for Firefox :rolleyes:

---

### Post by paparucino on 2006-11-19
> **mazu said:**
> Is it possible to change font in firefox? 
Edit-> Preferences -> Contents -> Fonts & Color

---

### Post by mazu on 2006-12-19
> Edit-> Preferences -> Contents -> Fonts & Color

Yes, but I want to change the interface font. As far as I know firefox uses gtk. On my machine I use KDE and I have installed the gtk lib and gtk-qt-engines to render gtk application, all works fine (thunderbird, synaptic) except of the firefox which has the interface fonts much bigger than the rest of the application.

Any other ideas?

UPDATE:
I found the solution in this thread: [http://www.ubuntuforums.org/showpost.php?p=1259120&postcount=6]("http://www.ubuntuforums.org/showpost.php?p=1259120&postcount=6")

---

### Post by ozorba on 2006-12-19
The Menu Fonts are set by the settings in 
./mozilla/firefox/XXXXXXX.XXXXX/chrome/userChrome.css 

Here is what my my one looks like. I found it from the web a while ago.

-----------

menubar > menu, menubar, menubutton, menulist, menuitem {
   font-size: 12px !important;
   font-family: sans !important;
   font-weight: normal !important;
}

menupopup > * {
   font-size: 12px !important;
   font-family: sans !important;

   font-weight: normal !important;
}

#urlbar {
   font-size: 12px !important;
   font-family: sans !important;
   font-weight: normal !important;
}

#ubhist-popup > .popup-internal-box, .textfield-popup > .popup-internal-box {
   font-size: 12px !important;
   font-family: sans !important;
   font-weight: normal !important;
}

dialog, box, button, page, label, caption, textbox, input, select {
   font-size: 12px !important;
   font-family: sans !important;
   font-weight: normal !important;
}

window {
   font-size: 12px !important;
   font-family: sans !important;
   font-weight: normal !important;
}

#sidebar {
   font-size: 12px !important;
   font-family: sans !important;
   font-weight: normal !important;
}

-----
Hope it helps...

OZ

---

### Post by mazu on 2006-12-19
Unfortunately I'm heaving more trouble with firefox. After I've used custom userChrom.css the all fonts looks fine except of font used in buttons and edit boxes (so fonts on the web sites), problem is that these fonts are too big. They look fine in Opera, Konqueror, but not in Firefox :(
Look at the screenshot below:

[[IMG]http://img474.imageshack.us/img474/1725/screenci9.th.jpg[/IMG]](http://img474.imageshack.us/my.php?image=screenci9.jpg)

Maybe these fonts are related to GTK??? Please help me becouse I'm getting more and more confused...

---

### Post by mazu on 2006-12-20
OK, after some research I found out that is GTK-QT issue, connected with DPI. I have under my KDE the gtk-qt-engines, recently I've installed gnome-control-center to change font settings there. After I decrease DPI setting in gnome-control-center do value 64 the same size fonts from KDE looks the same as these from GNOME, and the problem with bigger buttons disappear. Everything is ok until I restart Xserver. After that everything returns back and buttons are again too big. But just after I run the gnome-control-center->fonts (it keeps the 64DPI) and close it, the problem once again disappear until next restart.

Can anyone halp me with this??? ](*,)

---

### Post by reformedgeek on 2006-12-24
try adding this line after 
$ gnome-font-properties

Setup font sizes then:

$ ln -s /usr/lib/control-center/gnome-settings-daemon ~/.kde/Autostart/
;)

---

### Post by capital on 2007-02-19
The problem is with Firefox, not the system.  Here is the easiest fix:

type about:config in the address bar [enter]
find layout.css.dpi (type dpi in the filter)
change the value to '0' -- this forces firefox to use system font settings
restart firefox

No need to mess with other configuration files.
That was for Firefox 2.0 and up.

For Firefox 1.5, just go to Preferences > Content > Fonts & Colors
Go to the advanced dialog box, and tell it to use system font settings.

---

### Post by tommie74 on 2007-05-05
I found this somewhere in this forum:

The problem is with Firefox, not the system. Here is the easiest fix:

type about:config in the address bar [enter]
find layout.css.dpi (type dpi in the filter)
change the value to '0' -- this forces firefox to use system font settings
restart firefox

No need to mess with other configuration files.
That was for Firefox 2.0 and up.

For Firefox 1.5, just go to Preferences > Content > Fonts & Colors
Go to the advanced dialog box, and tell it to use system font settings.

---

