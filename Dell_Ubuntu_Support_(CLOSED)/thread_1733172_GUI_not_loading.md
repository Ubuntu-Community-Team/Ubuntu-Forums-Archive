---
title: "GUI not loading"
date: 2011-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tesla67 on 2011-04-18
the GUI isnt loading when i start up my new ubuntu net book 10.10. what i mean is that once loaded the top and side bar do not appear but when i hover over the location of wher the side bar should be i get a white box that pops up to the right of my pointer. any help would be welcome this is my first use of any lunix operating system so im lost.


tesla

---

### Post by varunendra on 2011-04-19
Can you post screenshots (of default screen and also when the pop-up box appears)? I guess from your description that you are able to get to the desktop but might have accidentally deleted the panels.

---

### Post by Tesla67 on 2011-04-19
[IMG]http://a6.sphotos.ak.fbcdn.net/hphotos-ak-snc6/215451_202916246406131_100000632701328_619331_2123550_n.jpg[/IMG][IMG]http://a2.sphotos.ak.fbcdn.net/hphotos-ak-snc6/206457_202916323072790_100000632701328_619333_7611481_n.jpg[/IMG][IMG]http://a5.sphotos.ak.fbcdn.net/hphotos-ak-snc6/206474_202916369739452_100000632701328_619335_7067793_n.jpg[/IMG]

---

### Post by Cyrusw on 2011-04-20
I have the same problem on my dell mini 9 installed UNE yesterday and did update installed a few apps then did a restart and it won't load the GUI just shows my wallpaper I think one of the apps I installed or maybe an update stuffed it up.

I can get into terminal but that was about it. so I reinstalled UNE again since it was a fresh install anyways cause I can't seem to find a quick fix for it online.

my suggestion is back up ur docs and stuff through terminal if u can access it and then do a fresh install again.

---

### Post by varunendra on 2011-04-20
Try any of these:
[http://ubuntuforums.org/showpost.php?p=10275856&postcount=2](http://ubuntuforums.org/showpost.php?p=10275856&postcount=2)

or

[http://ubuntuforums.org/showpost.php?p=9253183&postcount=2](http://ubuntuforums.org/showpost.php?p=9253183&postcount=2)

---

### Post by Tesla67 on 2011-04-20
I tryed bolth of the ones you gave me and neither worked. the first one said basicly that that wasnt a comand i will post what it said.


tesla

---

### Post by Tesla67 on 2011-04-20
the termanal said this

matthew@matthew-Latitude-D610:~$  gconftool --recursive-unset /apps/panel && killall gnome-panel
gnome-panel: no process found
matthew@matthew-Latitude-D610:~$ gconftool --recursive-unset /apps/panel && killall gnome-panel
gnome-panel: no process found


tesla

---

### Post by varunendra on 2011-04-21
> **Tesla67 said:**
> the termanal said this

matthew@matthew-Latitude-D610:~$  gconftool --recursive-unset /apps/panel && killall gnome-panel
[COLOR=Red]**gnome-panel: no process found**[/COLOR]

Seems as if gnome-panel is not even running. Press '**Alt+F2**' and enter **gnome-panel**. See if this brings up the panel.

Also, check this:

- in terminal, enter **gconf-editor**. This will open gconf editor window.

- in the left pane of the editor window, expand to **desktop > gnome > session > required_components**

- in the right pane, see if **panel** is listed.

If the panel entry is there, and the "Alt+F2 > gnome-panel" trick doesn't do anything, please tell us if you did any customization on desktop settings before this happened (like trying some compiz settings, windows-decorations etc.). I mean was is okay earlier or is it same from the very beginning of your installation?

---

### Post by Tesla67 on 2011-04-21
the problem seems to be with using the net book layout because when i switch to desktop it works fine. i never change anything it was like that from the start.

tesla

ps maybe im suposed to run the desktop not net book well its easy enough to switch when logging in.

---

### Post by varunendra on 2011-04-21
Good to hear that at least you found a way around that works.

Just out of curiosity - did you check whether the gnome-panel is running or not in netbook mode?

(I guess the "panel" entry should be there at **desktop > gnome > session > required_components **in gconf-editor even in netbook mode)

Your feedback may help me offer better help next time someone needs it.

---

