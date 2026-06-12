---
title: "Overview in GNOME Classic?"
date: 2012-05-12
forum: Desktop Environments
---

### Post by kohoutek1 on 2012-05-12
Hi, all.

I've been using GNOME Classic lately, and, thanks to Compiz Config, I've got all the desktop features I'd like except one: Overview. GNOME Shell implements it so well... better than Unity, better than Mac OS X with its Launchpad. 

Does anyone know of any way to get the overview into classic?

---

### Post by markbl on 2012-05-12
Wouldn't you be better off using gnome-shell and then applying [extensions](https://extensions.gnome.org/) to recreate your gnome-classic environment?

---

### Post by kohoutek1 on 2012-05-12
> **markbl said:**
> Wouldn't you be better off using gnome-shell and then applying [extensions]("https://extensions.gnome.org/") to recreate your gnome-classic environment?

Yes, true. In nearly every respect, yes.

The one thing that it so crucial to my workflow and DE orientation is the global menu. Development has ground to a halt in the Shell, and the implementation of it is ungainly in Unity. In Shell 3.2, there was a drop-down global menu that worked with GTK apps only, but not with QT apps, or with LibreOffice. Even that implementation is now broken under 3.4. I can't even get it in the repos. I had to remove the old one when I first moved to 12.04.

In Classic, I'm getting (so far) a nice, stable appmenu applet that does exactly what it needs to do... removes the localized menus from the application windows and puts them in the top panel. It does it for LibreOffice, too, without (so far) breaking.

I've got Expo when I point to the top left, all open windows when I point to the top right, show desktop when I point to the bottom right. 

I've got a coverflow shift switcher through ALT-TAB

What I now would like to find is an overview layer that shows all applications, more like Launchpad in Mac OS X. 

What I'm wondering is whether anyone is implementing or knows of some script that would initiate such a feature.

Could it be a widget layer?

---

### Post by kohoutek1 on 2012-05-12
Or... or...

Porting the indicator-appmenu to the Shell? 

It seems that GNOME has concluded that it's not within their broader design plans to do so.

---

### Post by zombifier25 on 2012-05-13
Compiz has the Scale effect.

---

### Post by kohoutek1 on 2012-05-13
> **zombifier25 said:**
> Compiz has the Scale effect.

Yes, Scale is the "window picker." Got that set to initiate at the top right corner of the screen.

I think I may have found it.

Not many people may be aware that GNOME has a fairly advanced widget system, Desklets. This is the basis for the overview in the Shell as well as in Unity.

I've installed the Desklets framework, and I'm beginning to go through the hundred or so widgets that are available, looking for components that are comparable to those in Shell overview.

Using CCSM, I enable the widget layer plugin, then I change the settings for each widget I want to use to "Use as widget" (they are set to the desktop by default). I can also resize to whatever I want.

I haven't yet found the icon-driven application menu that I'm looking for, but I suspect it's in there, somewhere.

I'll post back with screenshots once I get as far as I can with it.

---

### Post by kohoutek1 on 2012-05-14
The screenlet "FolderView" is the one. All done now.

---

### Post by mojo2012 on 2012-08-30
can you post screenshots of your current setup please?

---

### Post by mpmistr on 2012-08-31
> **kohoutek1 said:**
> Or... or...

Porting the indicator-appmenu to the Shell? 

It seems that GNOME has concluded that it's not within their broader design plans to do so.


I can't understand why no one has ported indicator-appmenu to gnome shell.. not the lame drop down appmenu (which is broken now, anyways). Aside from some useful Compiz effects I would actually consider gnome shell if I could get an actual global menu to work..

It's such a space saver and it looks so much cleaner but it seems like global menu/appmenu support is either unsupported or broken every new release.. considering gnome shell is very 'single app' oriented I am very surprised that the gnome developers in their infinite wisdom do not provide global menu support.

/le sigh

---

