---
title: "Nexuiz"
date: 2008-08-11
forum: Gaming &amp; Leisure
---

### Post by s3a on 2008-08-11
Ok, I have two questions:

1)Alt-tab doesn't work so is there another way to pause the game and go back to Ubuntu to answer lets say people on msn? Pressing F10 closes the game but how do I minimize the game?
2)It keeps saying that little yellow box that it wants me to update to the newest Nexuiz how do I make it not show the box? (at least during gameplay)

---

### Post by s3a on 2008-08-11
I think I found the answer to my own question at:
[http://gentoo-wiki.com/HOWTO_minimize_fullscreen-Games](http://gentoo-wiki.com/HOWTO_minimize_fullscreen-Games)

I'll check it out now and see if it works.

---

### Post by Abras on 2008-08-11
hmmm, nice find. I'll have to try that out for myself.
In the meantime, opening the Nexuiz terminal (by pressing the "~" key) and then pressing Alt+Tab also works. :)

---

### Post by s3a on 2008-08-11
I can't seem to get it working anyway where is the Nexuiz terminal? Like ETSwitch is located in Applications-->Games but running it doesn't seem to do much. I thought it would work if i left it running while running Nexuiz then doing alt tab but that didn't work.

For others searching for this, I downloaded it from:
[http://linux.softpedia.com/progDownload/ETSwitch-Download-34172.html](http://linux.softpedia.com/progDownload/ETSwitch-Download-34172.html)

---

### Post by detrate on 2008-08-12
Create a file in your Nexuiz data directory (~/.nexuiz/data) called autoexec.cfg and paste the following:

```
bind F9 "+fullscreen" // Toggle fullscreen
alias +fullscreen ""
alias -fullscreen "fullscreen_off"
alias fullscreen_off "vid_fullscreen 0 ; vid_restart ; alias -fullscreen fullscreen_on" 
alias fullscreen_on "vid_fullscreen 1 ; vid_restart ; alias -fullscreen fullscreen_off"
```

The code above binds your **f9 key** to toggle fullscreen.  This is a barebones solution, there are many powerful options, **[here's a list of cvars](http://www.nexuizninjaz.com/toolz/cvar/index.php?search=vid_)** that may interest you.

---

### Post by jpeddicord on 2008-08-17
My solution: don't run nexuiz in fullscreen, and bind F9 to "enter console" on the options menu. When you want to escape from the game, hit F9 and the mouse is freed.

---

