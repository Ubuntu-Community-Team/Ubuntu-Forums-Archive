---
title: "I'm beginning to dislike AWN! Help!!!"
date: 2008-02-22
forum: Desktop Effects &amp; Customization
---

### Post by argraff on 2008-02-22
Okay, I have AWN and awn-curves, and all was happy (relatively) until this morning. I did an update to it, and now I cannot open the preferences. If I right-click on the bar, then preferences, I get a little popup that says

Logout command:
gnome-session-save --kill
Ok   Cancel

It's no longer in my preferences list either - what's up with this?

---

### Post by mD3m4r415 on 2008-02-22
i think there is a way to edit the pref's through System>Prefrences>AWN....... or go to Applications>Accesories(or maybe Utilities)> AWN Manager.......I am away from my Ubuntu Box so i cant be for sure     hope that helps

---

### Post by kbless7 on 2008-02-22
```
awn-manager
```

---

### Post by argraff on 2008-02-22
> **kbless7 said:**
> ```
awn-manager
```

Not found. Maybe that's the problem??? Can I just say sudo apt-get install awn-manager?

---

### Post by argraff on 2008-02-22
> **mD3m4r415 said:**
> i think there is a way to edit the pref's through System>Prefrences>AWN....... or go to Applications>Accesories(or maybe Utilities)> AWN Manager.......I am away from my Ubuntu Box so i cant be for sure     hope that helps

Apps > Accessories > AWN just opens yet another bar and the Pref > AWN is what is suddenly missing.

Thanks for all your help, guys - I'll post back if I figure it out.

---

### Post by 1337455 10534 on 2008-02-22
have you tried that? edit: using apt to install it
Last time I tried the trunk, it slowed my computer to a crawl... that was a while back, but I have bad memories, so perhaps you should try the stable? It works, very well, but there aren't any real plugins for it.

---

### Post by argraff on 2008-02-22
Just did that - it took me backwards (broken packages, we suggest this fix y/n?) and then I realized how useless it is without applets, so I found instructions, did that, and am back at EXACTLY THE SAME PLACE. 

Computers are fun, right? ](*,)

---

### Post by reacocard on 2008-02-23
awn-manager has been moved out to it's own package, to get it back, do 

```
sudo apt-get install awn-manager-bzr
```

---

### Post by argraff on 2008-02-23
Did that, and lost avant-window-manager. Tried to reinstall that, and it said I needed libavant0 (?). Tried to install that, and it had to uninstall awn-manager-bzr.

:confused:

I've uninstalled it all (I think). I'll try again later. In the meantime, I'd love for an explanation of what each piece is so I understand what they do and how they interact. Is there somewhere that I can read about it?

Many thanks - it looks cool, but I might be too dumb to install it! :)

---

### Post by fracturedmorals on 2008-02-23
> **argraff said:**
> Did that, and lost avant-window-manager. Tried to reinstall that, and it said I needed libavant0 (?). Tried to install that, and it had to uninstall awn-manager-bzr.

:confused:

I've uninstalled it all (I think). I'll try again later. In the meantime, I'd love for an explanation of what each piece is so I understand what they do and how they interact. Is there somewhere that I can read about it?

Many thanks - it looks cool, but I might be too dumb to install it! :)

For some reason the latest update broke the settings manager. I don't really know what to tell you except maybe to go to one of the older versions for the time being and watch for updates to the bzr version.......

---

### Post by banelos on 2008-02-23
I too couldn't open awn-manager today after the update, but after installing awn-manager-bzr from the repository all was fine again.

Hope you get yours fixed mate, else try a complete reinstall of it.

---

### Post by argraff on 2008-02-25
Thanks everyone - I think I'm going to wait a bit and do it fresh later. Gotta get back to that "work" thing...

---

### Post by Nikolaiownz on 2008-03-01
> **reacocard said:**
> awn-manager has been moved out to it's own package, to get it back, do 

```
sudo apt-get install awn-manager-bzr
```


yeah worked for me! :)

---

