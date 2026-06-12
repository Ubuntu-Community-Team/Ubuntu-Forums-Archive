---
title: "amarok-xine issues loading MP3 files"
date: 2006-08-15
forum: Desktop Environments
---

### Post by phlexy on 2006-08-15
Sorry if I posted in the incorrect place, I'm kind've in a hurry but I'll try and explain as much as I can :)

I recently downloaded the amarok beta, and it wouldn't allow me to add MP3 files to amarok (see attatchment). I then uninstalled it, and reverted back to the older (stable) version of amarok but it still won't let me add MP3's, so I presume the issue isn't with what version I'm using. I have no idea why exactly it's doing this, as when I first installed amarok with ubuntu (yonks ago) it'd add (including the ones I'm trying to add now) any MP3 fine. 

Anyone have any idea how to fix this? :D

---

### Post by JerMe on 2006-08-15
try:

```
sudo apt-get install libxine-extracodecs
```

I had an issue where I removed KDE from my Ubuntu/GNOME installation, which ended up taking more than I bargained for.  I reinstalled amarok, but amarok wouldn't play mp3s.  I think installing libxine-extracodecs did the trick.

---

### Post by phlexy on 2006-08-15
hehe, nope it seems I already have them installed :p thanks for the effort though!

---

### Post by JerMe on 2006-08-15
Bah.  Can Rhythmbox or Totem play mp3s on your system? (checking for proper mp3 codecs)

---

### Post by phlexy on 2006-08-15
Rhythmbox can play but not Totem.

---

### Post by JerMe on 2006-08-15
Try nuking the amarok config file. Close amarok, then issue
```
sudo rm ~/.kde/share/config/amarokrc
```

and try again.

---

### Post by djSeverin on 2006-08-15
I would also suggest making sure libmad0 is installed AND you have the xine engine plugin selected (Settings -> Configure Amarok -> Engines). If you need to change the engine, make sure you exit and restart Amarok.

---

### Post by phlexy on 2006-08-15
Uh, okay. I tried installing libmad0 and I get this:
```
Reading package lists... Done
Building dependency tree... Done
libmad0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Then I try sudo apt-get upgrade
And I get ```
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  totem
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Any idea why totem's refusing to update itself and if the fact that it's not has anything to do with why my mp3's aren't playing :D?

---

### Post by Kelnoky on 2006-08-15
I have the same problem with amarok. Every codec is installed, every program plays mp3s perfectly, only amarok won't.

Try running amarok with sudo. For some reason it works for me then. Any idea how I can fix that (kinda annoying to start it with sudo every time, and its not very safe at that).

---

### Post by phlexy on 2006-08-15
Opening it with sudo seems to fix the problem to, but I noticed I had to do the whole first-time-startup thing, so maybe the config is what's the matter?

---

### Post by JerMe on 2006-08-15
If it were the config file, deleting the amarokrc and reopening amarok would have solved it (unless you didn't try that yet)

---

### Post by phlexy on 2006-08-16
ARRRRRRGH!@ I just completely whiped everything amarok, and reinstalled it but it's still not fixed. Running MP3's through sudo amarok works fine though -_- 

Any ideas?

---

### Post by SimonTheMime on 2006-08-18
Same problem. Help us :(

For me too it only works as root.

Edit: Nevermind, only the "welcome" ogg file works.. none of the mp3s do however, root or not.

---

### Post by carllfo on 2006-08-19
Have you tried > sudo adduser user group
Replace user with your username and group with audio.

Didn't work for me (different problem) but might work for you guys.

---

