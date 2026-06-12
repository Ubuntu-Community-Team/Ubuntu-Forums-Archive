---
title: "How to: Get AGS Linux to Work"
date: 2007-07-18
forum: Gaming &amp; Leisure
---

### Post by DeadSuperHero on 2007-07-18
Hey all,
I thought I'd make a useful post today.
Do you like playing games? Are you not particular, and is your game collection a bit lacking?
Well, I've got good news for you!
AGS (Adventure Game Studio) is a (currently Windows only) editor. The games can be played cross-platform, and binaries have been released for both Mac and...Ubuntu Linux!
There's over 900 games in the AGS library, so I'm going to walk you through some instructions, and you'll be able to play a majority of the AGS games. 
For starters, you're going to need a game. I'll just suggest whatever I last played. Ah...A Tale of Two Kingdoms, this will do nicely.

1. Download the .zip file at : [http://crystalshard.net/atotk.php?page=down](http://crystalshard.net/atotk.php?page=down)
2. Check on the Offical AGS Linux page, make sure you have all dependencies. ([http://drevil.warpcore.org/ags/](http://drevil.warpcore.org/ags/))

3. Extract the .zip file to somewhere easy to remember, such as /home/yourusername/Games/AGS/ATOTK
4. Download the latest ags engine, and the midi patch (Can be found on the offical AGS Linux page)

5. Type cd /home/yourusername/Games/AGS/ATOTK
6. Type tar -xjf /home/yourusername/whereyoudownloaded/ags-v2_72_920.tar.bz2 , then hit enter
7. tar -xjf /home/yourusername/whereyoudownloaded/midiptch.tar.bz2 , then hit enter again.
8. Type ./ags-setup, hit enter, then select "force Alternate letterbox resolution", then 640 x 480, then hit Save.
9. Type ./ags to play

However, after you do this once, you're not going to want to use this process a whole lot. Fear not! I've found a solution that lets you run the game simply by clicking on it.

Go to /home/yourusername/Games/AGS/ATOTK in whatever file browser you use
Right click on ags, choose "Open With Other Application", then "Use Custom Command"

For the custom command type "gnome-terminal" if you use regular Ubuntu with the GNOME desktop. If you use KDE, XFCE, or a different desktop environment, just use whatever your respective command for launching a terminal is.

Cheers,
Mr. Psychopath

P.S: I attached a few screenshots of the AGS Linux Engine in action.
Also, if you're getting no sounds, you need to go into ags-settings. Just open it with the custom command "gnome-terminal" (or it's equivalent), and you can tweak your settings, however "save and run" only saves the settings, it cannot yet run the game.
Many thanks to EvilTypeGuy for doing this. :guitar:

---

### Post by tartalo on 2008-03-21
You might also want to try Adventure Game Goddess which makes all this easier:
[http://feags.sourceforge.net](http://feags.sourceforge.net)

---

### Post by DeadSuperHero on 2008-03-22
Good to see you're still alive, Tartalo. =]

---

