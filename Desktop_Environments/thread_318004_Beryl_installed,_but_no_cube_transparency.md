---
title: "Beryl installed, but no cube transparency"
date: 2006-12-13
forum: Desktop Environments
---

### Post by evanvlane on 2006-12-13
I finished installing Beryl on my 6.06 build last night, and love it so far. The only thing I can't figure out is how to activate cube transparency. 

I tried looking in the Beryl Manager-> Desktop Cube under Numeric Values, among other things, but all it has is Acceleration Speed and Timestep.

Any suggestions? My video card is a Radeon 9100IGP, and I'm not sure if it's just that the ATI cards don't support it (although I can't see why-- I know my card doesn't support the water effects, but the other transparencies work fine), or if I'm missing a plugin / package, or if I need to upgrade beryl (beryl 0.1.1 currently).

Any help would be great!


Evan.

---

### Post by mannheim on 2006-12-13
I think you need version 0.1.3 for the transparent cube (but I may have forgotten already).

---

### Post by evanvlane on 2006-12-13
Cool. Do you know where I can find the most recent package? ```
sudo apt-get install beryl
``` gave me this 0.1.1...


Evan.

---

### Post by xopher on 2006-12-13
You could probably use Treviños SVN repository -- might cause breakage 'cause of the bleeding edge software though. (Just a warning, it should work just fine)

[http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/)

---

### Post by evanvlane on 2006-12-13
Okay, I added the repositiory and key, did the
```

sudo apt-get update
sudo apt-get dist-upgrade
```

route.

But I'm not sure what I'm trying to get-- SVN and Beryl 0.1.something...

After adding his repository what should I do?


Evan.

---

