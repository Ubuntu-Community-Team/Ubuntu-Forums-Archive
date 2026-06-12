---
title: "[SOLVED] No Fonts:/// in Hardy Heron"
date: 2008-04-29
forum: Desktop Environments
---

### Post by Kevbert on 2008-04-29
I've recently upgraded from Gutsy to Hardy.  In Gutsy it was possible to drag and drop new fonts into Fonts:/// It doesn't seem to exist in Hardy.
How do I install additional fonts ?  I already have the msttcorefonts installed.:confused:

---

### Post by shearn89 on 2008-04-29
copy the font into ~/.fonts, then open a terminal and do
```

sudo fc-cache -fv

```

---

### Post by Kevbert on 2008-04-30
Unfortunately I dont seem to have a ~/.fonts directory, only a ~/.fontconfig directory.:(

---

### Post by shearn89 on 2008-04-30
you can make it - it will automatically get searched when you do fc-cache -fv.

---

### Post by sujoy on 2008-04-30
alternatively you can coppy the font files to a custom directory in /usr/share/fonts

make a directory there and put your fonts in there, after that while still inside the directory do 

sudo mkfontdir
sudo mkfontscale
sudo fc-cache -fv

---

### Post by Kevbert on 2008-04-30
> **shearn89 said:**
> you can make it - it will automatically get searched when you do fc-cache -fv.

Thanks for that - all is fine in the land of fonts...

---

### Post by Simon Bridge on 2008-05-14
> **Kevbert said:**
> Thanks for that - all is fine in the land of fonts...

Only - it used to be possible for a user to add their favorite fonts to their own account without bothering the administrator... OK, I know most of us are our *own* sysadmins. But. But but but... Ubuntu *does* get deployed where the user is not the sysadmin.

Surely this is something that should be possible as a normal user? Or did I miss something?

---

### Post by Awalton on 2008-05-14
> **Simon Bridge said:**
> Only - it used to be possible for a user to add their favorite fonts to their own account without bothering the administrator... OK, I know most of us are our *own* sysadmins. But. But but but... Ubuntu *does* get deployed where the user is not the sysadmin.

Surely this is something that should be possible as a normal user? Or did I miss something?

Just put them in ~/.fonts and rerun fc-cache. That's all the fonts:// backend used to do. We didn't feel the need to recode fonts and themes because they're not real backends anyways, they'll never support the kinds of operations that other backends support, and they're very narrowly defined to only working with a certain subset of files. (We should probably close the bug I filed on this WONTFIX, but.. *shrug*)

It would be better for GNOME and its users if we coded a new font utility that did the above and allowed for installing fonts system-wide with PolicyKit, but this hasn't been done yet. I may do it for GNOME 2.24 if I can find time (or someone pays me, ping Shuttleworth ;)), as it's a frequent frustration of mine too. (And yes, I'm a developer, yes I love GUIs, and no, that is not weird).

---

### Post by Simon Bridge on 2008-05-14
> **Awalton said:**
> Just put them in ~/.fonts and rerun fc-cache.Yeah - just found out and came back here to fill everyone in.

It seems almost everybody (else) talking about this is sticking the "sudo" in front. Users could be excused for thinking that it was *required*.

Thanks for the great reply though...

---------------------------------------------
There is always someone new, so this bears repeating:

It is tempting to copy over all your Win and OSX fonts from that other partition so you can use them under gnuLinux. After all, you paid for them, right?

Well... no. You *rented* them. When you rented them, you agreed to some restrictions. So you should read your licenses. It is unlikely that you have been granted the right to use those fonts outside that particular install of that particular OS.

Yes yes I know - it seems *everybody* is ignoring these restrictions. However, when you break a rule, it is a good idea to know you are doing it. (Especially as you clicked something saying you read the contract: ignorance won't get you off.)

(The are MS Fonts in repos - these are the old Web fonts which have their own restrictions.)

Even with those ttf fonts you download there can be unexpected restrictions. Usually they are "free for personal use" or "non commercial". These are fine to use provided you understand that these terms usually restrict you from *sharing* your font-packages. (They do not give you distribution rights).

Worth thinking about before you zip a few dozen fonts to hand around your friends.

The odds are overwhelmingly against *you* being sued... unless you end up doing something significant and attracting attention. Maybe your enterprise gets sold for a cool bill? *Then* someone notices that you wrote your hardcopy documentation with a restricted font... then it is discovered you've been doing this lots since you were a teenager...

---

### Post by Ichido on 2008-08-30
[QUOTE=Awalton;4960971]Just put them in ~/.fonts and rerun fc-cache. That's all the fonts:// backend used to do. 

I tried this and still no ttfs in OpenOffice.:confused:
I'm using Ubuntu 8.04.1 on a Dell 1525 Laptop.

---

