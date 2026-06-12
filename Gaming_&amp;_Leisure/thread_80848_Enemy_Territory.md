---
title: "Enemy Territory"
date: 2005-10-23
forum: Gaming &amp; Leisure
---

### Post by anaoum on 2005-10-23
hello,

for some reason whenever i goto connect to a server in Enemy Territory, my network connection all ways fails. I have to go and reconfigure it. Does anyone know whats wrong?

thanks

---

### Post by MattiasJow on 2005-10-23
myself i have to start it as admin to get it to work, "sudo et", I would like to know how to fix this without being root.

---

### Post by Zeroedout on 2005-10-23
The reason I have to switch to root is because i installed it in /usr/local/games and ocourse i can't write in that directry, unless I am root. The reason it appears the connection failed is becuase the game is able to transfer the data (it's gettin maps and or designs and shit), but it has no idea it can't write to the directry, and jus does nothing till the connection times out. To remedy this, i'm guessing you guys did the same thing is me and installed it to that directry, so reinstall it in ~/et/ so in your home directry you can do all you please. If it is already installed in your home directry, then i'm way off.

---

### Post by Curufir on 2005-10-23
WolfET doesn't write **_anything_** into the install directory while you're playing.

All configuration files and downloaded maps/mods/etc go into ~/.etwolf

The problem here is that if you use sudo then the HOME environment variable is still set to /home/<your user>

When you install WolfET the usual method is to get root access (su or sudo) and run the installer. **_However_** the installer provides an option to run the game after it has been installed. Seems harmless enough, but you're still running the installer as root with the HOME directory as your own. So you end up writing a set of WolfET profiles in your user's directory that have root permissions. Same thing will happen any time you try running the game with sudo or su (su - would be fine). End result is that you have a crazy mix of user and root owned files in ~/.etwolf and need to be root to play the game.

Delete the whole ~/.etwolf directory using root (If you have lots of maps then do chown -R <username>:<username> ~/.etwolf), then go back to being your plain user and start the game with /usr/local/bin/et or wherever you installed it.

---

### Post by mike998 on 2005-10-23
[QUOTE=Curufir]... do chown -R <username>:<username> ~/.etwolf), then go back to being your plain user and start the game with /usr/local/bin/et or wherever you installed it....[/QUOTE]

This step of performing a chown -R <username><username> ~/.etwolf is something you should perform with most loki type installs but only if you have launched the game as the sudo'd user when you install the game.  If you choose to wait and then launch the game without being sudo'd then you should be okay.

---

