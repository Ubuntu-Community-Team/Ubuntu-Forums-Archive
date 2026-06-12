---
title: "Adding models in Openarena"
date: 2007-08-14
forum: Gaming &amp; Leisure
---

### Post by CapitanYochua on 2007-08-14
How can you add extra models into OpenArena. I found a site with .zip files for it. Not sure how to add them in the game though.

---

### Post by DoktorSeven on 2007-08-14
Zip files should contain a pk3 file, this goes in /home/[your username]/.openarena/baseoa/

(note the dot before openarena)

---

### Post by CapitanYochua on 2007-08-14
Yeah. I kept unzipping until I got the pk3 file and put it in baseoa. I got on the game and when you player, model, but didn't see the character I added.

---

### Post by DoktorSeven on 2007-08-14
It works fine here; did you scroll all through the player models (all the way left and right)?

---

### Post by CapitanYochua on 2007-08-14
yEah. What site did you use to get the new models. maybe something is just wrong with the one i'm trying.

---

### Post by DoktorSeven on 2007-08-14
First one I found was [this one from ioquake3](http://ioquake3.org/?page=models).

---

### Post by CapitanYochua on 2007-08-14
That's exactly where I found mine. I downloaded it. extracted it. Until I got the pk3. And put it in the baseoa... I'll take a screen shot.
[http://s197.photobucket.com/albums/aa83/capitanyochua/?action=view&current=Screen.png](http://s197.photobucket.com/albums/aa83/capitanyochua/?action=view&current=Screen.png)
I uploaded the screenshot into photobucket.

---

### Post by DoktorSeven on 2007-08-14
```

~/.openarena/baseoa$ ls | grep mario
md3-mario.pk3

```

[Screenshot](http://doktorseven.miskie.net/images/mario.jpg)

Not sure what the problem is here.  I have the latest version of OpenArena (0.7), so if you have 0.6 maybe it's not able to use them, though I don't see why not.

---

### Post by CapitanYochua on 2007-08-14
I have the newest one too. I did commands and got the same thing. But it didn't work.

---

### Post by Orichalcon on 2009-08-27
well i had a similar problem with Kubuntu.....actually when i put the models in baseoa (i think you shouldn't unzip it...just put it zipped in there....) in sigle player it went all fine but a little catch that all bots used my custom model too....and in multiplayer i couldn't see my friends custom models neither they could see mine...even if we all had the custom models in baseoa.....strange?? somebody knows the solution??

---

