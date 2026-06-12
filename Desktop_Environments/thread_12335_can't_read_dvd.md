---
title: "can't read dvd"
date: 2005-01-23
forum: Desktop Environments
---

### Post by roms on 2005-01-23
hello,
it's my first post on this forum; i'm a newbie and ubuntu is my first release, since october. 
My problem is that i can't read any dvd on my ubuntu. i use totem, gxine ... nothing works.
this the error messages of xine :
[I]
xine engine failed to start.

No input plugin found.
Maybe the file does not exist, has wrong permissions or
URL syntax error.[/I]

and a next window :* Read error from: /dev/dvd*

the shell says : [I]

([I]gxine:21466): Gtk-WARNING **: Failed to set label from markup due to error parsing markup: Erreur à la ligne 2 caractère 9 : Texte encodé UTF-8 non valide

(gxine:21466): Gtk-WARNING **: Failed to set label from markup due to error parsing markup: Erreur à la ligne 2 caractère 9 : Texte encodé UTF-8 non valide

(gxine:21466): Gtk-WARNING **: Failed to set label from markup due to error parsing markup: Erreur à la ligne 2 caractère 9 : Texte encodé UTF-8 non valide

(gxine:21466): Gtk-WARNING **: Failed to set label from markup due to error parsing markup: Erreur à la ligne 2 caractère 9 : Texte encodé UTF-8 non valide

(gxine:21466): Gtk-WARNING **: Failed to set label from markup due to error parsing markup: Erreur à la ligne 2 caractère 9 : Texte encodé UTF-8 non valide

(gxine:21466): Gtk-WARNING **: Failed to set label from markup due to error parsing markup: Erreur à la ligne 2 caractère 9 : Texte encodé UTF-8 non valide
lirc: lirc_init failed. Make sure that you have lircd running
lirc: and that you have the permissions to connect to the socket[/I]

and when i press play:

libdvdnav: Using dvdnav version 1-rc7 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: LOTR_TWO_TOWERS_D1
libdvdnav: DVD Serial Number: 2EBD6E43
libdvdnav: DVD Title (Alternative): LOTR_TWO_TOWERS_D1
libdvdnav: Unable to find map file '/home/roms/.dvdnav/LOTR_TWO_TOWERS_D1.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1-rc7 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: LOTR_TWO_TOWERS_D1
libdvdnav: DVD Serial Number: 2EBD6E43
libdvdnav: DVD Title (Alternative): LOTR_TWO_TOWERS_D1
libdvdnav: Unable to find map file '/home/roms/.dvdnav/LOTR_TWO_TOWERS_D1.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).[/I]
l*ibdvdnav: vm: faild to read VIDEO_TS.IFO*

thanks for help me. i spent 10 hours today on the web to find a solution but nothing...
only one person have the same problem! :confused: 

i don't want to go back to windows  :-& 

thanks for all

---

### Post by Perfect Storm on 2005-01-23
Have you checked [http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html) on howto setup dvd player?

Or [http://www.ubuntuforums.org/showthread.php?t=9850](http://www.ubuntuforums.org/showthread.php?t=9850)

---

### Post by roms on 2005-01-24
Awesome it works! =D>  =D>  =D>  =D>  =D>  =D>  =D>  =D>  =D>  =D> 

thanks for all. :D

---

### Post by Datchew on 2005-02-06
ok... i'm lost. 

followed the ubuntu installation faq guide (blue page) and got xine installed and working beautifully. 

then, i tried to rename the shortcut in the launcher panel and it disappeared and i couldn't find it again. 

so i went to the synaptic package manager and uninstalled xine (complete uninstall) and then went back through the ubuntu installation faq blue page and did it all again. 

now, my xine does this when i try to run a dvd. 

[IMG][IMG]http://img.photobucket.com/albums/v147/talk2frog/Screenshot.png[/IMG][/IMG]


If i click on the "more" button, it shows a list of stuff and one of them says

"cannot find input plugin for MRL [dvd:/]

---

### Post by valadil on 2005-02-06
Did you install libdvdcss2?

---

### Post by Datchew on 2005-02-06
yes.  [IMG][IMG]http://img.photobucket.com/albums/v147/talk2frog/Screenshot2.png[/IMG][/IMG]

---

### Post by Datchew on 2005-02-07
bump...

do i have to pay someone to get help on these thing???
 :D

---

### Post by Perfect Storm on 2005-02-08
Did you try to uninstall all the packages and start all over?

---

### Post by Datchew on 2005-02-08
Yes. 
I mentioned that in my first post. 

however, since i'm new at this, i probably missed some of the packages. 

Do you know which ones i should uninstall from synaptic?
Thanks much.

---

### Post by valadil on 2005-02-08
(This may not be relevant but it's worth a try.)

There's no libdvdcss for amd64 bit users.  However libdvdread3 gives us a script we can use to generate libdvdcss and install it.

Try using the locate command line to find libdvdcss.  There should be a shell script (.sh file) that can be run to install everything for ya.  If it doesn't exist then I guess this isn't the real problem.

---

### Post by Datchew on 2005-02-09
Thanks much for the suggestion. 

That one is already installed as well. 

Any other ideas???

---

### Post by earobinson on 2005-03-10
[QUOTE=Datchew]Thanks much for the suggestion. 

That one is already installed as well. 

Any other ideas???[/QUOTE]
 i have the same problem 2

earobinson@earobinson:~ $ xine
This is xine (X11 gui) - a free video player v0.99.1.
(c) 2000-2003 The xine Team.
libdvdnav: Using dvdnav version 1-rc7 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: FUTURAMA_S4_D1
libdvdnav: DVD Serial Number: 30A668D8
libdvdnav: DVD Title (Alternative): FUTURAMA_S4_D1
libdvdnav: Unable to find map file '/home/earobinson/.dvdnav/FUTURAMA_S4_D1.map'libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdread: Invalid IFO for title 2 (VTS_02_0.IFO).
libdvdnav: ifoOpenVTSI failed
xiTK received SIGSEGV signal, RIP.
Aborted

---

