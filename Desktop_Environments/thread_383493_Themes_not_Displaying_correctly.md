---
title: "Themes not Displaying correctly"
date: 2007-03-13
forum: Desktop Environments
---

### Post by aashay on 2007-03-13
As you might guess, im new to this stuff...
Anyway, i was trying to install this theme called "Frozen Plastic Suite" from [http://www.robertourso.com/?cat=3]("http://www.robertourso.com/?cat=3")
Installation was okay.. extracted it to /home/myname/.themes/ ..
The theme shows up in the Preferences->Themes . However, it looks aweful once applied. Looks nothing like the preview 
[IMG]http://www.robertourso.com/images/second.jpg[/IMG]
instead.. it looks like this:
[IMG]http://http://img250.imageshack.us/img250/1038/screenshotgw6.jpg[/IMG]
Many other themes that i installed failed to skin the buttons/panels/scrollbars.
Is there something i'm missing? Or am i just plain unlucky ??

---

### Post by ardchoille42 on 2007-03-13
> **aashay said:**
> As you might guess, im new to this stuff...
Anyway, i was trying to install this theme called "Frozen Plastic Suite" from [http://www.robertourso.com/?cat=3]("http://www.robertourso.com/?cat=3")
Installation was okay.. extracted it to /home/myname/.themes/ ..
The theme shows up in the Preferences->Themes . However, it looks aweful once applied. Looks nothing like the preview 
Many other themes that i installed failed to skin the buttons/panels/scrollbars.
Is there something i'm missing? Or am i just plain unlucky ??

You have to be aware that there are many different types of themes:

GTK2 themes - these themes take care of 'skinning' the controls (or widgets), like the scrollbars, buttons, etc.

Metacity themes - These themes take care of 'skinning' the titlebar and window borders.

Icon themes - these themes dictate which icon set you are using.

GDM themes - these themes dictate how the GDM screen (login screen) will look.

It helps to know which type of theme you are installing. The theme in your first screenshot appears to be a Metacity theme - window border and titlebar only. It's doing a good job of themeing the titlebar but your complaint is the rest of the window. That is taken care of by your GTK2 theme (the theme under the "Controls" tab in the theme manager), not the Metacity theme you installed. That is why the second screenshot looks bad.

---

### Post by aashay on 2007-03-13
Well.. iprobably should've mentioned it, but it IS a GTK theme and also has a metacity border. i.e GTK + Metacity
As you said.. the metacity part of it works fine.. the GTK one fails.
Also, its not this theme.. many more themes fail to do what their screenshots claim
Is there a package i should install to make em work good?

---

### Post by fallout75 on 2007-03-14
[ATTACH]27352[/ATTACH]

This is what I get, it's flat and rounded. not sure what I did to get this to happen.

Any help or direction is appreciated.

---

### Post by aashay on 2007-03-14
your screenshot is the metacity part of the theme. Im having trouble with the gtk part

---

### Post by ComplexNumber on 2007-03-14
> **aashay said:**
> your screenshot is the metacity part of the theme. Im having trouble with the gtk part
have you installed the gtk2-engine-pixbuf  package?

---

### Post by aashay on 2007-03-14
i havent installed it (if it dint come preinstaled or as a dependency)... Lemme look into this. I'll post an update soon

---

### Post by ComplexNumber on 2007-03-14
> **aashay said:**
> i havent installed it (if it dint come preinstaled or as a dependency)... Lemme look into this. I'll post an update soon
if you want the theme to look right, then you're going to have to install it because it uses the pixbuf theming engine. either install it through synaptic or type the following on the commandline:
**sudo apt-get install gtk2-engines-pixbuf**

---

### Post by aashay on 2007-03-14
aah... finally got it to work with the pixbuf engine
just a little correction.. it was **gtk2-engines-pixbuf**:)

---

### Post by aashay on 2007-03-14
> **ComplexNumber said:**
> if you want the theme to look right, then you're going to have to install it because it uses the pixbuf theming engine. either install it through synaptic or type the following on the commandline:
**sudo apt-get install gtk2-engines-pixbuf**
thanks a lot for your help

---

### Post by ComplexNumber on 2007-03-14
nice one :). i really don't know why the pixbuf engine isn't installed by default because there are a lot of themes that use it.

---

### Post by girard on 2007-03-15
> **ComplexNumber said:**
> if you want the theme to look right, then you're going to have to install it because it uses the pixbuf theming engine. either install it through synaptic or type the following on the commandline:
**sudo apt-get install gtk2-engines-pixbuf**

how do we find out which is needed by what anyway? also goes for installing software etc...

---

### Post by girard on 2007-03-15
> **ardchoille42 said:**
> You have to be aware that there are many different types of themes:

GTK2 themes - these themes take care of 'skinning' the controls (or widgets), like the scrollbars, buttons, etc.

Metacity themes - These themes take care of 'skinning' the titlebar and window borders.

Icon themes - these themes dictate which icon set you are using.

GDM themes - these themes dictate how the GDM screen (login screen) will look.

this really helped a lot in understand how to customize the look of our desktop. in gnome-look.org, they have a lot of other things in the left side panel where gtk2, metacity, icon themes are found such as xmms, topaz brainstorm, beryl. compiz. etc... what are those?

---

### Post by ComplexNumber on 2007-03-15
> **girard said:**
> how do we find out which is needed by what anyway? also goes for installing software etc...
in the case of pixbuf engine, often its quite obvious by looking at how the theme is supposed to look (eg on gnome-look) because various parts have a pattern.

the direct way of finding out is looking through the gtkrc file within the theme and doing a search for "engine".

---

### Post by aashay on 2007-03-15
> **girard said:**
> this really helped a lot in understand how to customize the look of our desktop. in gnome-look.org, they have a lot of other things in the left side panel where gtk2, metacity, icon themes are found such as xmms, topaz brainstorm, beryl. compiz. etc... what are those?

Finally... something i can help out with:
XMMS: Music Player somewhat like the older winamp
Beryl: Composite manager [http://www.beryl-project.org](http://www.beryl-project.org)
Compiz: Another Composite manager  [http://www.go-compiz.org/](http://www.go-compiz.org/)

Composite managers have transparency effects and lotsa such fancy stuff

---

### Post by girard on 2007-03-16
so is beryl totally different from 3d desktop? or are they basically the same? i installed 3ddesk but i don't know how to configure the system for it.

---

### Post by aashay on 2007-03-18
if i'm not mistaken, beryl is a complete window manager much like the default "metacity". Hovewer it has much more eye candy. To run 3ddesk, just type in 3ddesk in the terminal. Beryl does a much better job of 3d desktop switching than 3ddesk

---

### Post by girard on 2007-03-19
> **aashay said:**
> if i'm not mistaken, beryl is a complete window manager much like the default "metacity". Hovewer it has much more eye candy. To run 3ddesk, just type in 3ddesk in the terminal. Beryl does a much better job of 3d desktop switching than 3ddesk

so it's like openoffice and microsoft office. i tried to install beryl but it was a disaster. when i rebooted, i ended up in a terminal and i could not get back to the GUI. i decided to reinstall everything so i get everything back to normal - it was time consuming though. thanks a lot.

---

