---
title: "Firefox Flash Problem"
date: 2005-12-24
forum: General Help
---

### Post by naruto11111 on 2005-12-24
I just upgraded to firefox 1.5 and everything was fine.  A page prompted me to install flash 7 so I clicked the install plugin button.  It installed but said it wasn't successful so I'd better try a manual install.  

I ran the installation and for location of browser I put /usr/lib/mozilla-firefox (which I believe is correct) 

When I reloaded the webpage I was on, it still said I was missing the plug-in.  I clicked install again, this time it said it had installed properly.  But now whenever I go to a page that requires flash, firefox immediately closes itself and doesn't say why.  Anyone know what I might have done wrong?  Or at least how I can uninstall the plug-in/get the system back to where it was?

---

### Post by cbudden on 2005-12-24
If you installed firefox in the location described in the wiki it is /opt/firefox/firefox-bin .

---

### Post by VR6Pete on 2005-12-24
I had same problems as you.

I uninstalled flashplayer-mozilla and installed flashplayer-nonfree using synaptic  This resolved the error for me.

Pete

---

### Post by mr_mar on 2005-12-24
There is a problem with Firefex 1.5 and Flash player 8.0 when Adblock plugin is installed !

---

### Post by mztriz on 2005-12-24
[QUOTE=VR6Pete]I had same problems as you.

I uninstalled flashplayer-mozilla and installed flashplayer-nonfree using synaptic  This resolved the error for me.

Pete[/QUOTE]

I don't have flashplayer-nonfree in synaptic?

---

### Post by naruto11111 on 2005-12-24
flashplayer-mozilla didn't show up in synaptics for me.  it looks like i did install it in the wrong directory, any thoughts on how to get it back to normal or reinstall it?  thanks!

---

### Post by briancurtin on 2005-12-24
[QUOTE=mr_mar]There is a problem with Firefex 1.5 and Flash player 8.0 when Adblock plugin is installed ![/QUOTE]
that is firefox's problem then

does adblock really work as well as everyone says it does?

---

### Post by GazaM on 2005-12-24
[QUOTE=mr_mar]There is a problem with Firefex 1.5 and Flash player 8.0 when Adblock plugin is installed ![/QUOTE]
mr_mar: I think your problem isn't the Adblock plugin, but rather the fact that Flash Player 8 isn't yet available for linux...

---

### Post by TimelessRogue on 2005-12-24
Hey, guys, I had the same problems getting some of this stuff to install.  Guess what!  Jump on over to:  [http://ubuntuforums.org/showthread.php?t=66563&page=1&pp=40](http://ubuntuforums.org/showthread.php?t=66563&page=1&pp=40)  and check out the info about Automatix.  

That's what finally eased the pain of getting the Flash (and other stuff we all use) situation squared away.  Download it, use it in good health and relax a bit.  Oh, and don't forget to run Synaptic Package Manager AFTER using Automatix.  It works great ...

---

