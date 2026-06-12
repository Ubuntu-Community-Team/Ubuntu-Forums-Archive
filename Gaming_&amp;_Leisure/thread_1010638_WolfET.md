---
title: "Wolf:ET"
date: 2008-12-14
forum: Gaming &amp; Leisure
---

### Post by Nemix on 2008-12-14
i couldn't seem to get 2.55 working. I got 2.60 installed but the full screen doesn't seem to work right, it opens in a window and the lower bottom is off the screen. Ive tried resizing the resolution and such but doesn't make a difference, its my first game i got for Linux all my others are on the windows boot.

another question is i need to change some files in the game, so i can patch it and add my own .cfg files to customize the game settings. When i try doing it i get this message: 
You do not have the right permissions to extract archives in the folder "file:///usr/local/games/enemy-territory"

how would i get around this?

---

### Post by Perfect Storm on 2008-12-14
Usually you don't go into where the game is installed (hopefully you didn't launch the game from the installer window - if it was an option).

Check your home directory - make sure you can see hidden files and see if you can find wolfETs folder - it contains a .cfg

---

### Post by Nemix on 2008-12-14
thanks for the reply.

i didn't start the game from the installer i followed a guide.

i need to replace two files in the game:
et.x86
etded.x86
with another two and that will patch the game.
And then i need to put a file into one of the Mod files within the game.

i dont know if i need to change a setting so i can do things manually, but i cant find any files for the game besides under /usr/local/games 
and it seems to block me from doing anything in that area.

do i need to use the terminal? im still getting use to how Linux works :p

---

### Post by Perfect Storm on 2008-12-14
You do this then, place the two files on your Desktop

```
cd ~/Desktop
sudo mv et.x86 etded.x86 /usr/local/games/<name of wolfET directory>
```

---

### Post by Nemix on 2008-12-14
wow fast response.

Thanks that worked perfectly:KS:KS

just need to see how i can sort out the screen thing now =D

---

### Post by Perfect Storm on 2008-12-14
Regarding your other question/problem. See if disabling compiz have any effect;

Gnome Desktop;
```
metacity --replace
```

KDE Desktop;
```
kwin --replace
```


to turn it back on;
```
compiz --replace
```

---

### Post by Nemix on 2008-12-14
same thing happened after i tried that.

is it possible to resize the game window? because its set to full screen but, its still in a window not full screen. 
Oh and is there a way to get out of a game and use the cursor on the desktop?

Edit:
ok lol, was trying few things and screwed it up....now i need to uninstall the game and reinstall, i some how dragged the game window off the screen and now when i start it i get a black screen.
So if someone would be so kind as telling me how to uninstall that would be great!

sorry for your troubles =S
Linux is weird when u just come from windows all the things you knew have like gone out the window. =P

---

### Post by Perfect Storm on 2008-12-14
> is it possible to resize the game window? because its set to full screen but, its still in a window not full screen.

disable compiz should solve this problem.


Uinstall WolfET
```
cd /usr/local/games
sudo rm -rf <name of WolfET folder>
```

should do it. There might be a file or two in /usr/local/bin but if you're going to re-install it simple overwrite these files.


Note; just be cautious when using rm commands, they can do great harm if used wrong.

---

### Post by Nemix on 2008-12-14
wow i i kinda messed up real bad...the game didnt work once i reinstalled just came up with a blank screen and i had to ctrl alt backspace. so i decided to try and reinstall ubuntu (bad idea..)
did it all and now i cant use my mouse or keyboard at all, worked while i was installing but after it just doesnt work. 

i could just quite and try and get rid of ubuntu but i really like it and want to sort all this stuff i kind did bad:lolflag:

---

