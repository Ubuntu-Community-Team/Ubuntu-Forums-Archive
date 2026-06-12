---
title: "Several questions"
date: 2006-01-17
forum: General Help
---

### Post by nanotube on 2006-01-17
hello everyone!
i have just installed ubuntu on my laptop last week, and am enjoying it a lot :) customizing it is pretty easy, and synaptic package manager is the coolest thing ever. now, i have a few questions that i hope are not too hard.

1. how can i add another folder to the "places" menu in the top gnome panel (next to Applications). the menu editor only edits the applications menu... and i could not find anything about the places menu in any conf files either. any hints?

2. when i play an asf file in mplayer, it is all choppy. when i play it in vlc, it is /almost/ perfect, but still with a few chops here and there. and of course, totem does not play it (and it seems, does not play much of anything... :) ). under windows, that same asf file plays without any problems. any hints on what may be causing the choppiness?

3. how can i add menu items to the menu that is displayed when i right click on the desktop? for that matter, how can i create click menus when i middle-click or left-click on the desktop (like in a bunch of other window managers) 

4. how can i tell ubuntu to renew/release the ip address on an interface? my process list shows a dhclient running for both interfaces (wireless and wired), and the man page for dhclient claims that you can control a running dhclient process, but it is not clear to me how to do that. whats the "correct" way to do ip renew?

5. how to set the default size of gnome terminal on opening? the default window size is too small for me, i would like to make it bigger, but cannot find any option for it in the profile editor or anything. hints?

6. installed the flashplayer-mozilla plugin, but there is no sound in any of the flash files. sound works normally for everything else in the OS. what could be wrong?

well, that's it for now, i hope these are all answerable questions. i might be coming back with more soon... :) thank you all in advance!

---

### Post by stuporglue on 2006-01-17
[QUOTE=nanotube]hello everyone!
i have just installed ubuntu on my laptop last week, and am enjoying it a lot :) customizing it is pretty easy, and synaptic package manager is the coolest thing ever. now, i have a few questions that i hope are not too hard.
[/QUOTE]
Welcome! I'll answer what I know, and leave the rest to others. 
> 
1. how can i add another folder to the "places" menu in the top gnome panel (next to Applications). the menu editor only edits the applications menu... and i could not find anything about the places menu in any conf files either. any hints?


Open a nautilus window and navigate to the folder  you want to add. In the Bookmarks menu, click "Add bookmark". 

> 
4. how can i tell ubuntu to renew/release the ip address on an interface? my process list shows a dhclient running for both interfaces (wireless and wired), and the man page for dhclient claims that you can control a running dhclient process, but it is not clear to me how to do that. whats the "correct" way to do ip renew?


GUI: System Menu-->Administration-->Networking (enter password).

Select the interface to renew. Click "deactivate", then "activate". 

Command line for wired:
sudo ifdown eth0 && sudo ifup eth0

Same thing for wireless, but substitute your wireless interface name.

> 
5. how to set the default size of gnome terminal on opening? the default window size is too small for me, i would like to make it bigger, but cannot find any option for it in the profile editor or anything. hints?

You just barely missed it then. In the profile editor under the "general" tab, uncheck "Use the system terminal font" and select your own font in the drop down box below it. 

> 
6. installed the flashplayer-mozilla plugin, but there is no sound in any of the flash files. sound works normally for everything else in the OS. what could be wrong?


I've had trouble with the flash player that Firefox wants to install. Go to the Linux download site on Macromedia's page, and get the latest version. You'll have to unpack it and run the installer from a terminal, but it's pretty easy.

---

### Post by aysiu on 2006-01-17
[QUOTE=stuporglue]
I've had trouble with the flash player that Firefox wants to install. Go to the Linux download site on Macromedia's page, and get the latest version. You'll have to unpack it and run the installer from a terminal, but it's pretty easy.[/QUOTE] You could also try ```
sudo apt-get install flashplugin-nonfree
```

---

### Post by nanotube on 2006-01-17
[QUOTE=stuporglue]Welcome! I'll answer what I know, and leave the rest to others. 

Open a nautilus window and navigate to the folder  you want to add. In the Bookmarks menu, click "Add bookmark". 
[/quote]

oh wow, that was easy :) though not immediately apparent to a new user...

> 
GUI: System Menu-->Administration-->Networking (enter password).

Select the interface to renew. Click "deactivate", then "activate". 

Command line for wired:
sudo ifdown eth0 && sudo ifup eth0

Same thing for wireless, but substitute your wireless interface name.

cool, thanks!

> You just barely missed it then. In the profile editor under the "general" tab, uncheck "Use the system terminal font" and select your own font in the drop down box below it. 

sorry if i was not clear. i did not mean the font size, i meant the size of the window. as in, the number of lines and columns displayed in the terminal window. 

> I've had trouble with the flash player that Firefox wants to install. Go to the Linux download site on Macromedia's page, and get the latest version. You'll have to unpack it and run the installer from a terminal, but it's pretty easy.

aha, i see... ok, i will give it a shot. 

thanks for all your answers!

---

### Post by nanotube on 2006-01-17
oh, and a couple more questions. (i will continue the numbering from the first post).

7. in windows, i am used to double clicking on the window menu (the one that displays minimize, maximize, close, etc), and closing the window. in ubuntu, that does nothing. is it possible to enable "double click window menu to close" feature, or do i just have to change my habits? :)

8. when opening the file manager on a folder with a lot of items (or even not so many), it takes it quite a while to populate the list. i have changed the preferences in the preview tab to disable all the thumbnails etc, but there is still a delay. is there a way to speed up dir listing? (well, besides using the console :) ).

thanks!

---

### Post by morphodone on 2006-01-17
[QUOTE=nanotube]5. how to set the default size of gnome terminal on opening? the default window size is too small for me, i would like to make it bigger, but cannot find any option for it in the profile editor or anything. hints?
[/QUOTE]

I know this isn't the answer you are looking for but...

hit these keys together:   Ctrl+Alt+F1

for a virtual terminal.

Sometimes I find it's easier to get work done that way.

Forgot to add - hit these keys to get back to the gui:  Alt+F7

---

### Post by nanotube on 2006-01-20
hey all,

so i have managed to resolve some questions on my own. 
for the default terminal size, see my solution on here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Gnome_Terminal_default_size](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Gnome_Terminal_default_size)

for flashplayer and sound, see my solution here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Sound.2C_Firefox.2C_and_Flash](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Sound.2C_Firefox.2C_and_Flash)

some questions are still open, however:
1. how to make double click on window menu to close the app?

2. how can i add items to the right-click-on-desktop menu?

3. choppy .asf playback, choppy dvd playback (hdparm -i shows that mode is udma2).

would appreciate any help and suggestions!

---

### Post by 504harry on 2006-01-20
[QUOTE=nanotube]hey all,

so i have managed to resolve some questions on my own. 
for the default terminal size, see my solution on here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Gnome_Terminal_default_size](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Gnome_Terminal_default_size)

for flashplayer and sound, see my solution here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Sound.2C_Firefox.2C_and_Flash](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Sound.2C_Firefox.2C_and_Flash)

some questions are still open, however:
1. how to make double click on window menu to close the app?

2. how can i add items to the right-click-on-desktop menu?

3. choppy .asf playback, choppy dvd playback (hdparm -i shows that mode is udma2).

would appreciate any help and suggestions![/QUOTE]

Interesting thread - as a Newbie myself I can confirm (1)the clicking does work like windows (minimise, etc) on my Ubuntu 5.10  [and 504 before]
\
But I also use: File > Close ....however, I've recently noticed if I use "File>Quit" then all my Firefox windows auto-close themselves......odd.
/
Whilst I don't need/want Flash, have you posted the Plug-in process for any of these?
a) Java, b) PDF, c) Realplayer, d) (suggestions)
- Or come across simple process?
- it strikes me that these are the minimum to make Firefox  "the same as Windows*"..... and it is really frustrating  trying to find something that is really essential for internet use.
/ 
Here in UK (Jan06 issue)"Linux Format" [LXF] showed how to upgrade Firefox in Ubuntu 5.10, but it was really complicated and didn't use straight synaptic - It involved fiddling with sources.list - - their preferred s/w was Vim, but I can only find Gedit......am I barking mad?
I was rather hoping they/someone might make a cover-mount cd that  would install these plug-ins, ...but that would take out the fun.....huh.
Cheers
PS * (currently I'm  on Win98SE - that's 6 years back!)
RealPlayer: my test is the BBC - radio 4 (try [www.bbc,co,uk](www.bbc,co,uk))

---

### Post by nanotube on 2006-01-20
hey harry,

the file>quit is /supposed/ to completely exit firefox and close all windows. so that is not odd... just have to know about it :)

i have just posted the java install section. as to pdf, firefox by default is associated with a pdf viewer called 'evince'. realplayer... dont need it :)

in the meantime, anyone can post some answers to my questions?

---

### Post by nanotube on 2006-01-25
Still looking for answers:

1. how to make double click on window menu (the top left corner) to close the app?

2. how can i add items to the right-click-on-desktop menu?

---

### Post by nanotube on 2006-02-05
ok, i have found somewhat of a way to add items to the desktop-  with the nautilus scripts. just add scripts to the ~/.gnome2/nautilus-scripts directory, and they will show up on your desktop menu under "scripts". 

the question of making windows close with double click on the window menu still remains, though. any takers? :)

---

### Post by luminair on 2007-04-22
> **nanotube said:**
> 
the question of making windows close with double click on the window menu still remains, though. any takers? :)

I was wondering how to do this too.  Bumping for an answer!  :guitar:

---

