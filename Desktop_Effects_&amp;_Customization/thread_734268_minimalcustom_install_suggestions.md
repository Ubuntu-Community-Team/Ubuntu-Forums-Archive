---
title: "minimal/custom install suggestions"
date: 2008-03-24
forum: Desktop Effects &amp; Customization
---

### Post by aztektum on 2008-03-24
i'm looking to start configuring my own Ubuntu setup. i am going with openbox as the window manager. thinking thunar for the file manager. conky to watch sys perf (can conky monitor laptop battery?). idesk for icons

however i'm lookin' for suggestions in the following areas:

wifi network manager (test sys is a laptop)
cd burning
notification area for things like pidgin

---

### Post by spupy on 2008-03-24
I use Brasero for CD/DVD burning on my Fluxbox setup.
For wifi manager: wifi-radar.

Yes, conky can display battery status. Look at the link for a list of all things conky can display:
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by aztektum on 2008-03-24
awesome. that saved me time looking for that exact list :)

i will check out the burning software

i was thinkin' of usin' openbox's ability to run scripts update a menu item for wireless networks in the area. but that's just an idea :D

i used fluxbox but i didn't click with it. out of curiosity have you used openbox? wondering if there is a reason you prefer flux.

---

### Post by spupy on 2008-03-25
> **aztektum said:**
> i was thinkin' of usin' openbox's ability to run scripts update a menu item for wireless networks in the area. but that's just an idea :D
Yeah, that's a cool feature. It is tempting me to check out Openbox.

> **aztektum said:**
> i used fluxbox but i didn't click with it. out of curiosity have you used openbox? wondering if there is a reason you prefer flux.
Fluxbox was the first one i stumbled upon after Gnome and KDE. I haven't had time yet to play around with Openbox. I might like it, but the lack of a toolbar/systray is holding me back.

---

### Post by reacocard on 2008-03-25
wicd for wireless, brasero for disc burning (note: needs a couple gnome libs), and trayer for the systray (see 'man trayer' for how to set it up).

---

### Post by eriqjaffe on 2008-03-25
> **spupy said:**
>  I haven't had time yet to play around with Openbox. I might like it, but the lack of a toolbar/systray is holding me back.Getting a nice-looking panel in Openbox is very easy.

```
sudo apt-get install pypanel
```
...and then just add it to the end ~/.config/openbox/autostart.sh

You could also use fbpanel/lxpanel, those will give you a "start" menu that gets dynamically generated from all your .desktop files.  Personally, I just have my Openbox menu stuck in the task launcher of pypanel using [xdotool](http://crunchbang.org/archives/2008/03/14/invoke-openboxs-menu-with-xdotool/)..

Oh, and +1 for wicd.  wifiradar claimed my (older) card couldn't scan for available networks, but wicd just worked immediately.

---

### Post by aztektum on 2008-03-26
i discovered stalonetray by snooping around the forums. so far this is coming together nicely.

thinkin' of usin idesk for icons, but i get by well enough with just the menu right now

any other bits n pieces that i might find useful???

---

### Post by urukrama on 2008-03-26
Docker is a good system tray

Also have a look at my Openbox guide (see link in signature) for more ideas.

---

### Post by aztektum on 2008-03-28
sweet actually i found your guide through a Google search and have it bookmarked. good info there :D

---

