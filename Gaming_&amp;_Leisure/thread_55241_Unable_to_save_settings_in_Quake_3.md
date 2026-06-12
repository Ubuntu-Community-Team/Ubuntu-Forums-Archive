---
title: "Unable to save settings in Quake 3"
date: 2005-08-08
forum: Gaming &amp; Leisure
---

### Post by neowhale on 2005-08-08
I have followed the instructions [here](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=30) to properly install quake 3. The game runs fine on my laptop, but for some reason, everytime I start the game, I need to reconfigure all my settings (e.g. : video, controls, model). I installed at /usr/local/games/quake3 . The readme wrote not to play the using root account. 
Anyone has similiar problem like me ?

---

### Post by peter07 on 2005-08-08
[QUOTE=neowhale]I have followed the instructions [here](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=30) to properly install quake 3. The game runs fine on my laptop, but for some reason, everytime I start the game, I need to reconfigure all my settings (e.g. : video, controls, model). I installed at /usr/local/games/quake3 . The readme wrote not to play the using root account. 
Anyone has similiar problem like me ?[/QUOTE]

Yes. I had similar problem. I've installed ET using sudo command. This was my misteake. You should reinstall Quake using your standard account in your home directory. This should help.

EDIT:

Since that time I don't believe readmes :)

---

### Post by fng on 2005-08-08
How i did it.

- Downloaded the latest Pointrelease from id software.
- Ran the installer using sudo
  When the installer asks for 2 paths enter /usr/share/games/quake3 in the first text box. (Not sure if it needs quake3 in the end.)
  Enter /usr/games in the 2nd textbox
- You need pak0.pk3 from a previous installation or from the cd
- Open up a terminal 

```
 sudo cp /path/to/pak0.pk3 /user/share/games/quake3/baseq3 
quake3
```

This should work!

Personally i like having everything in one place.
Since i'm the only user using this box, i moved almost everything to my home dir,

```

cd ~
mkdir quake3
mkdir quake3/baseq3
mkdir quake3/pb
ln -s quake3 .q3a
sudo mv /usr/share/games/quake3/baseq3 ~/quake3/baseq3/
sudo mv /usr/share/games/quake3/pb ~/quake3/pb/
sudo chown -R fng:fng ~/quake3

```

Now all config files, maps, demos, mods, screenshots etc are in this 1 directory
Maybe this is an old habbit from quaking in the windows days :/

---

### Post by neowhale on 2005-08-08
ok, i found out the problem already. Its because I don't have permission to write the q3config.cfg file.
The file is hidden, located at ~/.q3a/baseq3/q3config.cfg . I just chown it to myself. Thanks for the help guys.

---

