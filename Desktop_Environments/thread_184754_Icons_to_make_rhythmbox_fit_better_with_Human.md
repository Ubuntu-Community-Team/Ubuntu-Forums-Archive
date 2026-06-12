---
title: "Icons to make rhythmbox fit better with Human"
date: 2006-05-30
forum: Desktop Environments
---

### Post by Laterix on 2006-05-30
Hi,

EDIT: Read second post for install instructions.

I made these 3 icons to make Rhythmbox fit better with Human icon theme. Unfortunately I can't figure out how I can make Rhythmbox to use them. I have tried everything, but old icons just stay there. This is driving me insane.

*Click on image to get clear version*
[IMG]http://users.utu.fi/ljtaim/pics/3icons.png[/IMG]

Well, anyway here are the icons I made. Perhaps someone knows how to use them and will share that information with us. :)

---

### Post by medgno on 2006-05-30
Nice icons! You might want to contact the art team to see if you can get them included :-)

Now as to installing them, this is what I did...
1. Copy stock_music-library.png, stock_repeat.png, and stock_shuffle.png into the folder /usr/share/icons/Human/24x24/actions/
2. In a terminal run the commands
```

cd /usr/share/icons/
sudo gtk-update-icon-cache Human

```
This will rebuild the icon cache so that programs looking for the icons will find them in the cache.
3. You might need to restart rhythmbox to see the new icons, but maybe not. Hopefully this will work.

---

### Post by Laterix on 2006-05-30
[QUOTE=medgno]
Now as to installing them, this is what I did...
[/QUOTE]
Thanks but that didn't help in my case. :(

---

### Post by ipguru99 on 2006-05-30
not meaning to butt in on the thread.. but you got rhythmbox to work?  I upgraded to dapper and lost it.  I can listen in vlc and beep (among others)... but I loved rhythmbox (I dig the icons)... any clue on what i lost?.. or what is needed to keep it going?

---

### Post by ipguru99 on 2006-05-30
nevermind... read, boy read... I found it... gstreamer went from 0.8 to .10... sorry...

---

### Post by Laterix on 2006-05-31
Now it works!

I needed to use --force paramater with cache update for some reason.
```

sudo gtk-update-icon-cache --force Human

```

---

