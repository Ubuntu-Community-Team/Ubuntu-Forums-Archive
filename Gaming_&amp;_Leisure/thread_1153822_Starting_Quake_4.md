---
title: "Starting Quake 4"
date: 2009-05-09
forum: Gaming &amp; Leisure
---

### Post by sharathpaps on 2009-05-09
Everytime I need to play Quake 4, I have to fire up the Terminal and do this :

```
cd quake4 && sudo ./quake4
```

I have to enter my password everytime.

How can I create a launcher that will run Quake 4 when I double-click it?

Is it ok to use sudo to get quake to start everytime?

Thanks...

By the way I'm using Intrepid Ibex 8.10

---

### Post by Perfect Storm on 2009-05-09
Properly because you shouldn't have ran Quake 4 with sudo in the first place - which created permission problem + security issue = bad.

Never run a game or application via sudo or root, only a few apps needs you to going into sudo (like add/remove, synaptic, etc).
I don't have quake 4 myself, so I suggest deleting the game completly (also the the hidden files in your $user/home) and install the game in your home directory with using sudo. 
If you want to install it globally - DON'T launch the game with sudo.

---

### Post by sharathpaps on 2009-05-09
Thanks for the info AI, I'll remove the game. I knew I was messing up when the whole package was being installed. But this is my first time running a game like Quake 4 on Ubuntu and it is a learning experience. Removing the game is gonna hurt cause I'm way into the game. I don't think I have the patience to start all over again. So, goodbye Quake 4. :-)

Thanks again...

---

### Post by u235sentinel on 2009-05-11
> **sharathpaps said:**
> Thanks for the info AI, I'll remove the game. I knew I was messing up when the whole package was being installed. But this is my first time running a game like Quake 4 on Ubuntu and it is a learning experience. Removing the game is gonna hurt cause I'm way into the game. I don't think I have the patience to start all over again. So, goodbye Quake 4. :-)

Thanks again...

You could always save your save game directory.  then of course you could always change permissions so you actually own the files instead of root.

I installed it as root making the same mistake myself.  Launching as myself a bunch of stuff broke.  So I installed it in my home directory under a games directory.  I own all the files so it's good to go.

---

### Post by caravel on 2009-05-12
Quake4 is easy enough to install - though I've had problems myself in the past.  Just run the installer as root, _do not_ uncheck any of the options except perhaps Punkbuster.  It will ask you to select the game version for your language.  Hit enter there and it should just install.  Leave the paths as they are.  They should be "/usr/local/games/quake4" and "/usr/local/bin".  (The links are created in "/user/local/bin", so that when you run the game you can simply type "quake4" as a normal user in the terminal and it will run without having to cd to the path first.)

Once it's installed I think it asks you if you want to "start now".  _Don't_.  You just have to copy the .pak4 from your CDs/DVD *without* overwriting any existing .pak4 files that the installer provided.

When that's done close any terminal windows, open a new non root terminal and do "quake4".  It should then start up ok.  You don't have to change permissions for the files in "/usr/local/games/quake4".

The game will probably start up in spanish.  Exit and change to another language as follows:

```
gedit ~/.quake4/q4base/Quake4Config.cfg
```

Find "spanish" and change to e.g. "english".

If the textures are ugly despite you changing the options etc then try the following:

```
gedit ~/.quake4/q4base/Quake4Config.cfg
```

Then use the following guide to choose the best setting for your graphics card: [http://ucguides.savagehelp.com/Quake4/FPSConfigs.htm](http://ucguides.savagehelp.com/Quake4/FPSConfigs.htm)

Ignore the bit about the "autoexec.cfg", make the changes to "Quake4Config.cfg". (remember that the guide is for windows users).

For your current installation you may get it working without reinstalling.  Just try:

```
sudo chown -R you:you ~/.quake4
```

Then try running it from a non root terminal:

```
quake4
```

Where "you" is your username.

---

### Post by PaulReaver on 2009-05-15
after you'ge got your permissions sorted out paste this into a empty document.

[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=quake4
Icon=/usr/local/games/quake4/quake4.png
Icon[en_GB]=/usr/local/games/quake4/quake4.png
Name=Quake 4
Name[en_GB]=Quake 4
Terminal=false



and save it as 
"quake4.desktop"

---

