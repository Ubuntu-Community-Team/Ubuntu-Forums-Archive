---
title: "enlightenment"
date: 2005-03-22
forum: Desktop Environments
---

### Post by gogodidi on 2005-03-22
I have heard a lot of good things about this desktop, and would like to give it a try

so I searched for enlightenment under synaptic and install the base files nd all its dependancies, and the skins amde available.

then, i log out, session --> no enlightenment, so I say 'hmm strange' and reboot my machien, still nothing, what can I do?

---

### Post by bored2k on 2005-03-22
[QUOTE=gogodidi]I have heard a lot of good things about this desktop, and would like to give it a try

so I searched for enlightenment under synaptic and install the base files nd all its dependancies, and the skins amde available.

then, i log out, session --> no enlightenment, so I say 'hmm strange' and reboot my machien, still nothing, what can I do?[/QUOTE]
 [HOWTO: Install and tweak E17 Enlightenment](http://ubuntuforums.org/showthread.php?t=20216&highlight=enlightenment)

If you would just use the search button .

---

### Post by gogodidi on 2005-03-22
[QUOTE=bored2k][HOWTO: Install and tweak E17 Enlightenment](http://ubuntuforums.org/showthread.php?t=20216&highlight=enlightenment)

If you would just use the search button .[/QUOTE]


i did, belive it or not

but then again, im no good at much

thanks tho!

---

### Post by bored2k on 2005-03-22
[QUOTE=gogodidi]i did, belive it or not

but then again, im no good at much

thanks tho![/QUOTE]
 Well , can you tell us where you THINK you failed or was confronted by and evil root shell ?

---

### Post by Psquared on 2005-03-27
[QUOTE=bored2k][HOWTO: Install and tweak E17 Enlightenment](http://ubuntuforums.org/showthread.php?t=20216&highlight=enlightenment)

If you would just use the search button .[/QUOTE]

bored2k, I think he is referring to E16 which is available on Synaptic without modifying the sources/repos. I did the same thing and it is not a choice in "Sessions." I started Gnome and opened a terminal and typed Enlightenment. It offers to edit the startup files for you, but there are all sorts of WARNINGS. It looks like the safest thing to do is to edit them manually.

However, the HOW-TO is for E17 and does not explain how to do this for E16.

We need a how to for adding E16 to the Sessions Menu in Warty.

Thanks.

---

### Post by cdhotfire on 2005-03-27
For e16 do the same thing:
 Create a file called **e16.desktop** in **/usr/share/xsessions/**
 Add the following lines to this file:
```

[Desktop Entry]
Encoding=UTF-8
Name=e16
Comment=
Exec=enlightenment
Icon=
Type=Application 

```
that should make it appear in sessions

---

### Post by Psquared on 2005-03-27
[QUOTE=cdhotfire]For e16 do the same thing:
 Create a file called **e16.desktop** in **/usr/share/xsessions/**
 Add the following lines to this file:
```

[Desktop Entry]
Encoding=UTF-8
Name=e16
Comment=
Exec=enlightenment
Icon=
Type=Application 

```
that should make it appear in sessions[/QUOTE]

Is it Exec= or Exec: ???

---

### Post by cdhotfire on 2005-03-27
[QUOTE=Psquared]Is it Exec= or Exec: ???[/QUOTE]

Exec=

---

### Post by Psquared on 2005-03-28
[QUOTE=cdhotfire]Exec=[/QUOTE]

Thanks a million. I got it working.   :smile: 

BTW, is there an easy way to add programs to the user menu? Right now the only way to start a program is to open terminal and type the name. I want to add everything that is available in Gnome. (Firefox, Openoffice,  Evolution, and Gaim) [-o<

---

### Post by cdhotfire on 2005-03-28
[QUOTE=bobmitch]This is a quick guide to menu/launcher editing - but I haven`t done extensive testing. If all is well, I`ll add this to the howto. It deals mainly with creating entries, but will show the path to removing entries as well, using the *.order* files.
 
 First off, launch the application you want to create an 'icon' for.
 
Click the top left corner (but not the border!) with the left mouse button and select "Create Icon". Note that you need e_utils (which needs e17/libs/engrave) installed in order for this to work. (You should have this package installed already if you followed the howto.)
 
 An .eapp file will be created and moved to **~/.e/e/applications/all**.
 
 Next, you need to add this .eapp file to the relevant **.order ** file.  These order files are what e17 parses when starting the apps, and are stored in the following directories:
 
 ```
**iBar:** ~/.e/e/applications/bar
 **E17 menu:** ~/.e/e/applications/favourite
 **Engage:** ~/.e/e/applications/engage
 
``` 
 
 Here's and example iBar .order file:
 
 ```
firefox.eapp
 xmms.eapp
 engage.eapp
 entice.eapp
 evidence.eapp
``` 
 
 Note that you can also create subdirectories for the menu. Simply make directories within **~/.e/e/applications/favourite ** and create **.order ** files in each one of them.
 
 Here's an example: 
 assuming that you have the following directories 
 
 ```
~/.e/e/applications/favourite/music
 ~/.e/e/applications/favourite/web
```
 
 you can make a **~/.e/e/applications/.order ** which contains the following text:
 
 ```
terminal.eapp
 music
 web
```
 
 This would create a menu that first shows the terminal icon and then has 2 directories - *music* and *web*. Following this system you'll also need to create .order files in those directories to select what .eapp files to have and in what order you want them to be in.
 
 
 If you don`t want to create your own icons - the author of engage has a ton of them rolled already for your pleasure [here]("http://aje.codewordt.co.uk/Files_files/applications.tar.gz") .
 
Note, that this has been heavily lifted from the site I linked to in the howto - but I`ve parsed it and packaged nicely for my fellow Ubuntians. :)
 
 Good luck, and let us know if it works. :)[/QUOTE]

might work on e16, i havent really used it much.[img]http://www.ubuntuforums.org/images/smilies/icon_redface.gif[/img]

---

### Post by bobmitch on 2005-03-28
The guide I wrote is most definitely for E17 only - E16 is, for most intents and purposes, a completely different desktop system.

---

### Post by Psquared on 2005-03-28
[QUOTE=bobmitch]The guide I wrote is most definitely for E17 only - E16 is, for most intents and purposes, a completely different desktop system.[/QUOTE]

When will E17 be final?

---

### Post by bobmitch on 2005-03-29
[QUOTE=Psquared]When will E17 be final?[/QUOTE]

Probably around the same time Duke Nukem Forever is released.

;)

Joking aside, the real power of E17 comes from the libraries it compromises - and these will undoubtably reach maturity/completion waaay before the desktop environment as a whole.

It is my hope that Gnome/KDE along with apps like metacity take advantage of these libraries, rather than try to reinvent the wheel themselves.

---

### Post by songochain on 2005-03-29
[QUOTE=bobmitch]Probably around the same time Duke Nukem Forever is released.[/QUOTE]
HAHAHAHA (i agree)

---

### Post by Monika on 2005-04-06
But ehem how does one launch an application in Enlightenment (16)? *blush* Have not been able to open anything other than "help" in which I didn't find anything about launching applications. I have found nothing that seems to be called "User Menu" and have no "applications" folder in ~/.enlightenment. But if I had any idea about how to launch anything in it, it looks kind of cool ;)

---

### Post by odrop on 2005-04-07
I don't remember exactly how to do it, nor will this probably help you much since i havent used it in years.  :-P 

But the app-list and other stuff can usualy be accessed by either right clicking the desktop, or middle mouse button... or i think you could use the windows key also.

Since I'm not on Linux right now I cant really check it out, but I hope this helps.

---

### Post by Monika on 2005-04-07
It says in the help that the right-click and middle-click should have all the possible menus... but I just haven't found a menu that has any application launchers in it in these two menus, nor can I see a prompt anywhere :( And weirdly, from what I can gather, I should have an application folder somewhere in my /home/.enlightenment/ but I don't!!

---

### Post by PMO6022 on 2005-04-07
Try looking for "regenerate menus" in one of the middle/right click menus.

---

