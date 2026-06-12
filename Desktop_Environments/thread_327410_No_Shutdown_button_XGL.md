---
title: "No Shutdown button XGL"
date: 2006-12-29
forum: Desktop Environments
---

### Post by ZERO_SHIFT on 2006-12-29
After installing a XGL session, I no longer have a shutdown button.

What should I do?

Thanks in advance

---

### Post by ZERO_SHIFT on 2006-12-29
I set ubuntu up so that when I press the laptop shutdown button, it automatically shuts down, rather than ask what to do.

System>Preferences>Power Management>General

However I would really like to have the shutdown option available in the menu.

Try it! Better than logging out and then shutting down.;)

---

### Post by tombott on 2007-01-24
ZERO_SHIFT that's exactly what I have done, but it would be nice to have the option there along with restart.

I also use the following commands

```
sudo shutdown now
```

```
sudo shutdown now -r
```

The first one shuts down the laptop / PC the second restarts.

Tom.

---

### Post by Peti29 on 2007-01-24
I read [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL") that:

> Note: If your shutdown/restart buttons disappear when you are in Xgl you can add these lines to your startxgl.sh script:

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"

```
making it look like this:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```


I never tried it so I'm not sure if it works (I just log off before I shutdown).
What does that two lines do anyway? Anyone to explain?

---

### Post by Lunar_Lamp on 2007-01-24
This does work. Just to let you know, I tried it and it works just great.

---

### Post by tombott on 2007-01-24
Excellent stuff Peti29 that's worked a treat, many thanks!

Tom

---

### Post by lilredfoxie on 2007-01-31
I tried that on my computer, and i'm still missing the shutdown buttons when i use XGL and Beryl.

---

### Post by Loonux on 2007-02-11
> **lilredfoxie said:**
> I tried that on my computer, and i'm still missing the shutdown buttons when i use XGL and Beryl.
Yep, added those lines to mine and im still missing the buttons (kubuntu for me though)
is there another way?

---

### Post by Sunflower1970 on 2007-02-12
Nothing to see here...nevermind. Found my answer :oops:

*whistles and slinks off*

---

### Post by vincentvee on 2007-11-11
it worked for me....dunno what those two lines do but they do the right thing
> **Peti29 said:**
> I read [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL") that:



I never tried it so I'm not sure if it works (I just log off before I shutdown).
What does that two lines do anyway? Anyone to explain?

---

### Post by woozyking on 2008-04-12
Sorry to rise up this topic again, but I can't find where this file startxgl.sh  is  :(

---

