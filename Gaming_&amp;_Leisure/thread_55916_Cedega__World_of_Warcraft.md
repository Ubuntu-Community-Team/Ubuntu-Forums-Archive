---
title: "Cedega / World of Warcraft"
date: 2005-08-10
forum: Gaming &amp; Leisure
---

### Post by SaCeR- on 2005-08-10
I have just changed my dis of linux from Fedora to Ubuntu.. And Ubuntu its just as good, if not better.. but i have one problem when im gaming World of Warcraft... Im using cedega and its working fine.. but i have one little problem.. i can't right click on anyone.. i can use the right click mouse to move myself, but to click on the mailbox or a NPC i can't... anyone who knows whats wrong or how i can fix it?

Another this, is that i have No sound at all in World of warcraft.. anyone knows about that?

---

### Post by Caboose on 2005-08-10
make a script to launch the game

```
export WINEPRELOADER_SETVALEGACY="no"
cd ~/.transgaming/c_drive/Program\ Files/World\ of\ Warcraft/
killall -9 esd
cedega WoW.exe
```
Fix it up to match your locations. That should fix everything.

Save as WoW.sh and run it

```
sh ./WoW.sh
```

---

### Post by Dolphin on 2005-08-10
You should check out [http://transgaming.org/forum/viewforum.php?f=51&sid=090c6141b46f3fe07e8383251c55b653](http://transgaming.org/forum/viewforum.php?f=51&sid=090c6141b46f3fe07e8383251c55b653)

Most WoW + Cedega/P2P issues and fixes can be found there.

---

### Post by plasmatonic on 2005-08-10
With the most recent patch, ATI users are experiencing difficulties that have no thorough workaround... that is, the targetting problem. Some of the solutions I've read are to use the tab key to target or to click on the overhead displays that can be toggled on/off with the "v" key.

Other than that, there is no other solution anymore for ATI users AFAIK  :mad:

---

### Post by Caboose on 2005-08-11
[QUOTE=plasmatonic]With the most recent patch, ATI users are experiencing difficulties that have no thorough workaround... that is, the targetting problem. Some of the solutions I've read are to use the tab key to target or to click on the overhead displays that can be toggled on/off with the "v" key.

Other than that, there is no other solution anymore for ATI users AFAIK  :mad:[/QUOTE]
You know, other than the one I posted?

I have a Radeon 9800 XT with the 8.14.13 drivers and it works ace with the fix I posted.

---

### Post by SaCeR on 2005-08-11
[QUOTE=Caboose]make a script to launch the game

```
export WINEPRELOADER_SETVALEGACY="no"
cd ~/.transgaming/c_drive/Program\ Files/World\ of\ Warcraft/
killall -9 esd
cedega WoW.exe
```
Fix it up to match your locations. That should fix everything.

Save as WoW.sh and run it

```
sh ./WoW.sh
```[/QUOTE]

Ohh thx alot Caboose, Its great.. it worked =] thx alot

---

