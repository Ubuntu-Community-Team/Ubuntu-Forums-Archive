---
title: "[SOLVED] Ascii Sector"
date: 2008-12-19
forum: Gaming &amp; Leisure
---

### Post by plinydogg on 2008-12-19
Can anyone get this game to work?

[http://www.asciisector.net/](http://www.asciisector.net/)

I'm not having any luck. Nothing happens when I click on the main file.

---

### Post by netyire on 2008-12-19
Wing Commander in ASCII ? :-)

> [FONT=Arial,Helvetica][SIZE=3]just download the free game by clicking the link at the top

Looks like you'll have to download a game client to run it though, it's ~2mb file accessible through the download tab, or just paste the following in your browser:

[http://www.asciisector.net/download/](http://www.asciisector.net/download/)

Interesting project, reminds me of the old retro games of the past. Thanks for the heads up! :popcorn:
[/SIZE][/FONT]

---

### Post by plinydogg on 2008-12-19
Thanks for the response netyire! I should have been clearer earlier. I was able to download the game itself it's just that it's an archive and when I unzipped it and attempted to run the game, nothing happened! 

It looks like a cool project though. If you can get it working (1) let me know how :) and (2) let me know how it is!

---

### Post by DirtDawg on 2008-12-20
> **plinydogg said:**
> Can anyone get this game to work?

[http://www.asciisector.net/](http://www.asciisector.net/)

I'm not having any luck. Nothing happens when I click on the main file.

There's a readme file included. You need to install sdl-1.2 (I think "libsdl1.2debian" in the repository) and sdl-mixer:
```
sudo apt-get install libsdl1.2debian libsdl-mixer1.2
```

---

### Post by plinydogg on 2008-12-20
Thanks for the info! But I get "libsdl1.2debian is already the newest version" and "couldn't find package libsdl-mixer"...maybe getdeb.net can make a package with everything in it?

---

### Post by DirtDawg on 2008-12-20
> **plinydogg said:**
> Thanks for the info! But I get "libsdl1.2debian is already the newest version" and "couldn't find package libsdl-mixer"...maybe getdeb.net can make a package with everything in it?

Sdl mixer should be in your repository. Maybe I typoed. Did you remember to add the '1.2' to the end so it reads like: ```
sudo apt-get install libsdl-mixer**1.2**
```?

---

### Post by plinydogg on 2008-12-20
Hey! That did it! Thanks a million! I'm looking forward to exploring this ascii game. They may be old fashioned, but they can be a lot of fun (case in point: DoomRL, Angband, etc.). Thanks!

---

### Post by plinydogg on 2008-12-20
Oddly, while the game works great now (thanks again!), when I create a menu item for it and click on it it doesn't work. Weird, but not that big of a deal.

---

### Post by Christian Knudsen on 2008-12-20
I think that may be because the game looks for its resources in the current "working directory". If you make a menu item or shortcut, it won't be able to find these resources and won't start. Is there any way to set the "working directory" like you do for shortcuts in Windows?

---

### Post by plinydogg on 2008-12-20
Good question! I'm not sure...

---

### Post by DirtDawg on 2008-12-20
> **Christian Knudsen said:**
> I think that may be because the game looks for its resources in the current "working directory". If you make a menu item or shortcut, it won't be able to find these resources and won't start. Is there any way to set the "working directory" like you do for shortcuts in Windows?

That's what I was thinking too. Strange problem. I did come up with a solution, though.

First, make a small script called 'asciisecRun' with Gedit. You can put this anywhere, but I put it in the extracted asciisec folder to prevent clutter:
```
gedit ~/localapps/asciisec/asciisecRun
```
Then add two lines like these, save and close (of course, change the path to match wherever you keep your asciisec binary). FYI, the '~' is shorthand for your home folder:
```
cd ~/localapps/asciisec/
./asciisec
```
Now make the script executable:
```
chmod +x ~/localapps/asciisec/asciisecRun
```
Then in your menu editor under the 'command' option, choose your script, or add it manually. I'm sure there's a more graceful solution out there, but this one worked for me. If anyone knows a simpler way to do this, I'd love to hear it.

---

### Post by plinydogg on 2008-12-22
Works flawlessly! Thanks!

---

### Post by trlkly on 2008-12-24
I don't know if its quite simpler, but you could also edit the  .desktop file (or create one).

It's a text file in the following format:

```
[Desktop Entry]
Version=0
Encoding=UTF-8
Name=
Exec=
Type=
StartupWMClass=
Path=
Icon=
GenericName[en_US]=
```

The attributes are pretty self-evident. You even can set the icon to any image in the filesystem. Just remember to set the Name attribute, as Gnome (and probably KDE) will ignore the filename.

---

