---
title: "Default (preferred) applications"
date: 2006-02-01
forum: Desktop Environments
---

### Post by chookie on 2006-02-01
Hello, I have a problem setting my default music player... this is what I am trying to do:

My multimedia-keyboard and its exta keys are working very good. I had no problem setting it up with the Keyboard-shortcut preferences. However, when I press the 'media' key on my keyboard (='Launch music player') I get an error saying that Rhythmbox is not installed. Well yeah I removed that one, I like xmms way better. But where do I set xmms as my music player, so that my key is bound to it?

I found ways to set my preferred internet and email applications, my default dvd software and so on, but I cannot find anything about the default music player?

I hope someone knows the answer... 
Kevin

---

### Post by aysiu on 2006-02-01
I'm not 100% certain this'll work, but you can try modifying /etc/gnome/defaults.list

---

### Post by chookie on 2006-02-02
Sadly that's not it...

---

### Post by aysiu on 2006-02-02
I've searched all around these forums, and no one's offered a good solution to this, which seems silly, since not everyone uses Rhythmbox. I searched for every file that contains the word *rhythmbox* and the file I gave you is the most promising...

---

### Post by clawoo on 2006-02-08
Hi! I've had exatcly the same problem here, moved from rhythmbox to amarok and my "start media player" key was very fond of rhythmbox it seems. 

Quick and dirty (and it works): 
1. install xbindkeys and xbindkeys-config

```
sudo apt-get install xbindkeys
sudo apt-get install xbindkeys-config
```

2. create default xbindkeys config file (xbindkeys-config crashed for me, I guess this was the problem)

```
xbindkeys --defaults > /home/[username]/.xbindkeysrc
```

3. run xbindkeys-config, maybe remove the settings already there, define a new key and assign it to open your fave app.

Hope this helps someone!

I feel good to be part of the Ubuntu Family.

---

