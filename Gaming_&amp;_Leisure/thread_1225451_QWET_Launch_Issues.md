---
title: "QWET Launch Issues"
date: 2009-07-28
forum: Gaming &amp; Leisure
---

### Post by Nandus1 on 2009-07-28
Hello All,
I have just installed QWET on an xubuntu environment.
I used the directions listed in the below listed link.
[http://gwos.org/doku.php/guides:32bit:etqw#enemy_territory_quake_wars](http://gwos.org/doku.php/guides:32bit:etqw#enemy_territory_quake_wars)
The install was very straight forward and appeared to go very smoothly.

I ran into a problem when I tried to configure the launcher.

"Launcher

Open the terminal and type;

Code:

sudo nano /usr/share/applications/etqw.desktop

Add the following;

Code:

[Desktop Entry]
Name=Quake Wars
Comment=Enemy Territory: Quake Wars pits the armies of Earth against the invading alien Strogg in an online strategic shooter.
Exec=/usr/local/games/etqw/etqw.x86
Icon=/usr/local/games/etqw/etqw_icon.png
Terminal=false
Type=Application
Categories=Application;Game;


Save (ctrl)+(o) and Exit (ctrl)+(x)

You can now launch Quake Wars by Applications &#8212;> Games &#8212;> Quakewars
Or by typing etqw in the terminal."

I was able to "(ctrl)+(o)" to save, but the terminal did not appear to respond when I hit "(ctrl)+(x)"

I am not sure I saved it properly, since it did not appear to respond when I attempted to complete the last step.

I attempted to launch the game by typing "qwet" in the terminal, but nothing happened. 
I got "bash: qwet: command not found"

Any ides? I am used to Gnome myself. Could the Xfce environment require a different set of commands even though it is based of Ubuntu?

Any help would be greatly appreciated and I would like to thank you all in advance for taking the time to read my post.

---

### Post by Nandus1 on 2009-07-28
Issue resolved.

Created launcher via the desktop.

Entered in code:
Name "ETQW"
Comment "Game" (You can type in whatever you want.)
Command "/usr/local/games/etqw/etqw.x86"

Runs well, no AA option though. Other people appear to have this issue as well. Sad, I am unable to see the game in all it's OpenGL glory.


I also have an audio issue I have to fix, but that is OS related.

---

### Post by rettichschnidi on 2009-07-29
You could just use this one: [http://liflg.org/?catid=6&gameid=85](http://liflg.org/?catid=6&gameid=85)

---

