---
title: "Firefox looks too Gnomish in Kubuntu"
date: 2005-11-04
forum: Desktop Environments
---

### Post by vitorsouza on 2005-11-04
Hi there,

I just installed Kubuntu 5.10 and I'm slowly installing the programs that I use. The goal is to migrate from Windows. I installed Firefox using Adept and it looks too Gnomish.

I've searched the forum for a solution and I found two related threads:

1. [http://www.ubuntuforums.org/showthread.php?t=75474](http://www.ubuntuforums.org/showthread.php?t=75474): talks about the mouse pointers and provides a solution on monkey89's reply. It worked alright, so the mouse pointers are OK now, but the scrollbar, menus and dialogs are still gnomish;

2. [http://www.ubuntuforums.org/showthread.php?t=77899](http://www.ubuntuforums.org/showthread.php?t=77899): explains that a package gtk2-engines-gtk-qt should be installed and configured under Appearances -> Gtk Styles. It is installed and configured properly (I think), but Firefox refuses to have a KDE look...

Am I the only one going through this? Is everyone else using Firefox 1.5 :) or am I using the wrong repository? See below my apt/sources.list:

```
# Main Ubuntu packages:
deb http://br.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://br.archive.ubuntu.com/ubuntu breezy main restricted

# Major bug fix updates produced after the final release of the distribution.
deb http://br.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://br.archive.ubuntu.com/ubuntu breezy-updates main restricted

# Security fixes:
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Universe (unsupported) packages:
deb http://br.archive.ubuntu.com/ubuntu breezy universe
deb-src http://br.archive.ubuntu.com/ubuntu breezy universe

## Universe packages bug fixes.
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

Thanks for any pointers.

Vitor Souza

---

### Post by shinygerbil on 2005-11-04
I haven't fund a way to change it, but then again I use [Opera](www.opera.com/download) so I haven't really invested much effort. The best I can suggest is to apply some nice skins...

Steve

---

### Post by Donza on 2005-11-04
I had exactly same problem. For me "solution" was to go to System settings->Appearance->GTK styles & fonts. I changend the "Use KDE style in GTK applications" to "Use another style". After applying this and restarting firefox nothing had changed. Then I went back to GTK styles & fonts and I changed the "Use KDE style..." option back and my Firefox looked qute as a baby. It's shame that there is still so annoying little bugs in Kubuntu... but on the other hand, many things work a lot better than on other distros.

---

### Post by mpettitt on 2005-11-04
I just themed Firefox with the PlastikFox theme... Go see my screenshot in the Kubuntu gallery to see how it looks.

---

### Post by shinygerbil on 2005-11-04
The above works for me.

The only theme worth having is PimpZilla ;)

(still looks a bit ugly though... imo)

Steve

---

### Post by vitorsouza on 2005-11-04
[QUOTE=Donza]I had exactly same problem. For me "solution" was to go to System settings->Appearance->GTK styles & fonts. I changend the "Use KDE style in GTK applications" to "Use another style". After applying this and restarting firefox nothing had changed. Then I went back to GTK styles & fonts and I changed the "Use KDE style..." option back and my Firefox looked qute as a baby. It's shame that there is still so annoying little bugs in Kubuntu... but on the other hand, many things work a lot better than on other distros.[/QUOTE]
Yes, I was fooling around the configuration and did exactly what you described and it looks all KDE-ish, except for the Open and Save As dialogs, which have that Gnome structure, but with KDE theme now. 

But I guess that's probably the most I will get, right? I mean, I have Gaim installed on Windows and its dialogs are just like that, which means it is "hardcoded" with the GTK dialogs instead of using the system's default, I guess. But it's weird that Firefox does that, since I also have it installed on Windows and it uses Windows' dialogs...

Does anyone have a Firefox that uses KDE's open/save dialog? Care to share how to do it?

Thanks,

V&#237;tor Souza

---

### Post by B.B on 2005-11-04
Or you could just configure your userChrome.css file. It's locatet in your profiles /chrome folder. If it doesnt exist there should be a UserChrome-example.css file, just rename it.

Delete everything in it and just do the typical CSS stuff, you can style almost everything.

! Reminder:
   The < !important > needs to be there.

This is how mine looks (I have the msttcore package installed, therefore the 'verdana' font) : 

* {
   font-size: 12px !important;
   font-family: verdana !important;
   }

And this is how it looks :
    [http://bblauritzen.net/kubuntu/screendumps/firefox_gui_makeover.png](http://bblauritzen.net/kubuntu/screendumps/firefox_gui_makeover.png)

Here are some other examples:

different font:
    [http://bblauritzen.net/kubuntu/screendumps/firefox_gui_makeover2.png](http://bblauritzen.net/kubuntu/screendumps/firefox_gui_makeover2.png)

different font size:
    [http://bblauritzen.net/kubuntu/screendumps/firefox_gui_makeover3.png](http://bblauritzen.net/kubuntu/screendumps/firefox_gui_makeover3.png)

---

### Post by victorche on 2005-11-05
I have my GTK Styles And Fonts in "Settings", but it is not starting at all :(
It is Kubuntu 5.10 and up-to-date
How can I use it? It looks like GTK-Qt Theme Engine... But it is not starting at all :(

---

### Post by stimpack on 2005-11-05
[QUOTE=vitorsouza]Does anyone have a Firefox that uses KDE's open/save dialog? Care to share how to do it?[/QUOTE]

Yes this is badly needed.

---

### Post by peanut butter on 2005-11-06
ifound that if you use the official firefox build on mozilla.org it has a betterkdeish look.
this may be out dated since i use Konquerer. and this happened last year:cool:

---

### Post by mlomker on 2005-11-06
I installed the Plastik theme.  I'd rather that it have used my KDE theme, but that didn't seem to work properly for me in Breezy.

---

