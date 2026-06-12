---
title: "gnome --&gt;too user friendly ;)"
date: 2006-01-31
forum: Desktop Environments
---

### Post by ashrack on 2006-01-31
After resuming from hibernation I must execute the below code, else the sound doesn't work.
```
sudo /etc/init.d/alsa force-reload
```

But when I do, I get this, which sometimes doesn't dissappear for more than a minute and its across all desktop
[ATTACH]5738[/ATTACH]
How to get rid of this so it wouldn't even be shown???

and also the following:
[ATTACH]5740[/ATTACH]
how would I set that it would automaticly reload??

---

### Post by ashrack on 2006-02-01
bump

---

### Post by mark_g on 2006-02-01
Possibly there's no easy solution for this problem. Hibernation is a very difficult proces. My pc's doesn't always restore correctly from it either, so best is to just disable it.

---

### Post by ashrack on 2006-02-02
MARK_G
I fail to see your point, since hibernation works 100% 4 me. 
Its just those GNOME DIALOGs that I want to get rid of when I restart sound card

---

### Post by darth_vector on 2006-02-02
if it was working 100% you wouldnt be having problems with your sound.

i would follow mark's advice.

---

### Post by ashrack on 2006-02-02
Am not having any particular sound problems. On resume from hibernation all that I have to do is restart the sound server which is done automaticly via hibernate.conf script and the sound works without problems afterwards.
It's just those annoying GNOME dialogs that are a pain in the arse and I wanna get rid off

ps. Hibernation is a MUST.

---

### Post by Garyu on 2006-02-02
I know too little to solve your problem, but my guess is you would benefit from making a script that executes your alsa reload and then reloads the volume control (so you don't have to get that dialog) and then does something to make your system realize it isn't a new soundcard, just a reaload, so you won't have to deal with all of those pop ups. How to do such a script is way beyond me, but you should be able to figure it out if you spend enough time with gnome manuals.

BTW, I just read a post here about a guy who suspected his entire harddrive crashed because of using hibernation. Now, I realize you think it is important, but is it worth all of this hassle on top of the fact that your entire system is at risk? If I were you I would listen to those guys saying it may not work as great as you think it is... :-k

---

### Post by ashrack on 2006-02-05
so no easy way I guess?

---

