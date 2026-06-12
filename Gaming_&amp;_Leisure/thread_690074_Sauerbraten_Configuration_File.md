---
title: "Sauerbraten Configuration File"
date: 2008-02-07
forum: Gaming &amp; Leisure
---

### Post by orngshusrthebest on 2008-02-07
I first installed the version of Sauerbraten available in the ubuntu repositories, and I created a config.cfg file, there was no config directory, so i put it in the data directory, where defaults.cfg is.  config.cfg had no impact on the actual set up of the game once started.  There were other problems too, so I decided to install the version from the debian unstable repos.  All of my problems except for configuration have been fixed.  When I make an adjustment from the in game menu, it saves the configuration. But I cannot change my name, or several other settings through the options in the game. What am I doing wrong?

---

### Post by daigidan on 2008-02-14
config.cfg should be automatically created by Sauer when you run it under $SAUER_DIR/config.cfg. Make sure your permissions are setup on the Sauer directory so that you can write new files to it, and so that config.cfg is writable by your user. The way I have it setup, the account I use to play Sauer is part of the video group, and the video group has full rights to anything under the Sauer directory. Let me know if you need more specific info on permissions.

Also, if you're looking to setup some config values that you can port to newer versions of Sauer, you should put them in $SAUER_DIR/autoexec.cfg. This file is not created automatically, so you will have to create it using a text editor. Then you can copy any pertinent values from config.cfg into it (like, "name yourname"). This way, if config.cfg gets corrupted you can just delete config.cfg without losing your customized configuration values. You can also copy autoexec.cfg to newer versions of Sauer as they are released. HTH!

---

### Post by soxs on 2008-03-30
I use the latest sauerbraten. I compiled it myself and in fact suaberaten does not dreate any .cfg file. It simply loses its memeory on restart, so I will have to do all that options again.
may you plx attach an example cfg, so I know how it should look like and I can create my own. Thx.

---

### Post by daigidan on 2008-03-30
What are the permissions on the directory where you installed Sauerbraten? You can find this out by opening a terminal and typing:

```
ls -l /path/to/sauerbraten_dir
```

The user that you use to run Sauerbraten needs write permissions to this directory. A quick and dirty way to fix permissions would be:

```
chmod -R 777 /path/to/sauerbraten_dir
```

Obviously you need to adust /path/to/sauerbraten_dir to match the path where you installed Sauer. ;]

A simple autoexec.cfg would contain:

```
name "yourname"
```

But you really should check your permissions first so that config.cfg gets created properly.

---

### Post by soxs on 2008-03-31
Config.cfg was finall found @ ~/.sauerbraten/.config.cfg  and it works pretty fine now. Don't know why, but it was not caused by permissions.
Plx simply attach your autoexec.cfg or give me some examples.

---

### Post by daigidan on 2008-03-31
Huh, weird.

Here's a snippet from my autoexec.cfg. I recommend setting options thru the GUI the way you like them and then just copying them from config.cfg into autoexec.cfg, but this should get you started:

```
name "yourname"
team "none"

bind M [ setmaster 1 ]
bind 6 [ say "sry" ]
bind G [ say "gg" ]
bind N [ say "np" ]

musicvol      0
showclientnum 1
ogro 1
shaderdetail 2
sensitivity 4
gui2d 1

```

---

### Post by soxs on 2008-03-31
thx a lot, this was what I needed

---

