---
title: "AWN/Docky help"
date: 2009-04-29
forum: General Help
---

### Post by _IRiX on 2009-04-29
Can anyone tell me if it is possible using AWN or Docky to keep the docks above the bottom panel? I followed the instructions from here [http://ubuntuforums.org/showthread.php?p=3370460#post3370460](http://ubuntuforums.org/showthread.php?p=3370460#post3370460) but that fix doesnt work for me.  Initially once either dock is loaded it is above the bottom panel, but as soon as you click the bottom panel or another window gets focus the dock moves behind the panel. Im using 8.10. Does anyone have any advice?

---

### Post by cgul1 on 2010-01-14
searching for the same solution

---

### Post by howefield on 2010-01-15
Can't get my head around using a dock and a panel (in the same position).

I'm not questioning your choice, but am interested in why you run both ?

Couple of workarounds might be to enable the show/hide buttons on the panel, so it slides out of the way when you don't need it, but is easily accessible when you do. Or reposition the panel to the side of the monitor and use auto hide.

If you use compiz, there might be something you can do within the the Windows Management section, click on Window Rules and in the "Above" field type class=Awn then enable Window Rules"

---

### Post by bobpaul on 2010-05-02
> **howefield said:**
> Can't get my head around using a dock and a panel (in the same position).

I'm not questioning your choice, but am interested in why you run both ?

Docky doesn't support the notification area, the Gnome Main Menu (or MintMenu or MenuBar), nor does it support a ton of other Gnome Panel applets (such as Tomboy and Network Monitor).

Until the menu and notification area are supported, at a minimum, it's impossible to get rid of all gnome panels. And Gnome probably won't let you delete the last panel, regardless.

**Edit** "class=Gnome-panel" did it for me. I just keep the center of the panel empty so docky can expand and won't hid anything important.

---

### Post by joshjensen on 2010-05-02
I was looking for a solution for this. What I ended up doing is removing the bottom panel and adding my Window List to the top. I had a lot of open space and I enjoy docky down at the bottom.

You might want to try [Cairo-Dock]("https://help.ubuntu.com/community/CairoDock") because it allows you to position it whereever you want but I like the simplicity of Docky. 

Good luck in your endeavors,

Josh Jensen

---

### Post by bobpaul on 2010-05-02
Yeah, on ubuntu I have a top panel and docky at the bottom. I have "Menu bar" in my top panel and I use docky to replace the window list (Manage windows without launcher). Basically, what I'd otherwise use a bottom panel for.

But I run LinuxMint, an Ubuntu derivative, on another PC and the MintMenu doesn't work well from the top panel, so I really needed a bottom panel with Docky floating over it.

Does Cairo-Dock get covered by other windows (eg, if you maximize them)? I primarily use Docky to manage open windows, and if it gets hidden, that's no good. This was a problem with other "dock" apps I've tried in the past.

---

### Post by fabounet on 2010-05-03
yep Cairo-Dock can reserve its space on the screen (that is to say other windows won't overlap it), if it's what you want.

---

