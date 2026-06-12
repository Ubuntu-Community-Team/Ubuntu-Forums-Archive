---
title: "GMAMEUI Player 2 Controls Are Greyed out when I change them to Player 3!"
date: 2010-06-03
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2010-06-03
Hi.
I play a certain game whereby it is player 1 and the cpu Vs player 3 and the cpu.
The controls for player 2 are blanked (for this game only) and I assign player 3 controls for my second game pad. When I do that, all player 3 controls are not greyed out. I have no problem playing other 2 player games in Mame. This was not a problem in Karmic.
Anyone know what to do?

Also from the picture attached, I accident change the key for '1 Player Start' from the number key 1 to mouse button 1. When I changed it back to the number key 1, that too is now greyed out! :mad:

---

### Post by Rytron on 2010-06-03
How can i reset all controls to their default settings?

---

### Post by warnec on 2010-06-03
I'd like to know that as well. I have a different problem, but I also need to reset the key bindings:

[http://ubuntuforums.org/showthread.php?p=9405283#post9405283](http://ubuntuforums.org/showthread.php?p=9405283#post9405283)

EDIT:

Hey! I did it! I can't believe I haven't seen it before! I googled for 2 days, and then I lost my faith in finding the answer. I found it now in Google. Looks like it's just a matter of  a right keyword.

Simply delete contents of ~/.config/mame/cfg. In my case, deleting "default.cfg" did the trick, because it is responsible for general MAME settings like UI. 
You can delete the .cfg file with the name of Your game, it should do the trick.

---

### Post by BigSilly on 2010-06-03
I ended up using the "Use default MAME options" or whatever it was in the GMameUI settings. Seems to give me a better control over things because it then uses the sdlmame.ini in /etc/sdlmame, rather than the GMameUI settings.

---

### Post by Rytron on 2010-06-04
> **BigSilly said:**
> I ended up using the "Use default MAME options" or whatever it was in the GMameUI settings. Seems to give me a better control over things because it then uses the sdlmame.ini in /etc/sdlmame, rather than the GMameUI settings.

I get the message 'GMAMEUI could not load the ROM' when I use that option. I had to uncheck it to play the mame roms. Then though there is the problem with controls again withot that option! :(

---

### Post by BigSilly on 2010-06-04
> **Rytron said:**
> I get the message 'GMAMEUI could not load the ROM' when I use that option. I had to uncheck it to play the mame roms. Then though there is the problem with controls again withot that option! :(

Yes, you'll need to edit the sdlmame.ini. It's worth a shot imho.

```
sudo gedit /etc/sdlmame/mame.ini
```

Edit this file to point it at your roms and whatnot. So rompath is /home/rytron/roms or wherever you have them stored. You can edit a whole bunch of other options there too. I tend to prefer to use that than the GUI, because it simply has more options.

It might not work, but I do think it's worth a try. :) The GMameUI options could have a problem somewhere that the mame.ini does not.

---

### Post by Rytron on 2010-06-04
> **BigSilly said:**
> Yes, you'll need to edit the sdlmame.ini. It's worth a shot imho.

```
sudo gedit /etc/sdlmame/mame.ini
```

Edit this file to point it at your roms and whatnot. So rompath is /home/rytron/roms or wherever you have them stored. You can edit a whole bunch of other options there too. I tend to prefer to use that than the GUI, because it simply has more options.

It might not work, but I do think it's worth a try. :) The GMameUI options could have a problem somewhere that the mame.ini does not.

Thanks BigSilly. I will give it a go.

Update: It worked in that it found the roms. However changing the controls is still a problem!

---

### Post by BigSilly on 2010-06-04
Hmmm. You could try deleting the default.cfg file in .mame and just start again. :confused:

It's a funny one innit? I generally just press the tab button to set the controls while in a game, but on mine the players have completely separate menus.

---

### Post by Rytron on 2010-06-05
> **BigSilly said:**
> Hmmm. You could try deleting the default.cfg file in .mame and just start again. :confused:

It's a funny one innit? I generally just press the tab button to set the controls while in a game, but on mine the players have completely separate menus.

No joy! :(

---

