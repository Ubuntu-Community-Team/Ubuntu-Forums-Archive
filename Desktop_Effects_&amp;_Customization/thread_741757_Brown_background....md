---
title: "Brown background..."
date: 2008-04-01
forum: Desktop Effects &amp; Customization
---

### Post by canthus13 on 2008-04-01
I've managed to customize nearly every aspect of Ubuntu to my specs, but I've got one annoyance left:  How do I change the brown background that shows between login and desktop load?  I've tried System>Preferences>Appearance, but color setting there doesn't seem to have an effect.

--Me

---

### Post by stalker145 on 2008-04-01
> **canthus13 said:**
> I've managed to customize nearly every aspect of Ubuntu to my specs, but I've got one annoyance left:  How do I change the brown background that shows between login and desktop load?  I've tried System>Preferences>Appearance, but color setting there doesn't seem to have an effect.

--Me

I'm not at my Ubuntu computer right now so this is going from memory... It *should* be right there where you change the login screen under preferences. If I recall correctly, there is a box where you can change the color and by default this box is brown.

---

### Post by HunterK on 2008-04-01
I actually had the same problem as you.  I heard its a bug in Gutsy.

Open the file /etc/gdm/PreSession/Default in a text editor with administrator privileges (e.g. sudo vim /etc/gdm/PreSession/Default) and search for the part that says

```
# Default value
if [ “x$BACKCOLOR” = “x” ]; then
BACKCOLOR=(some color in hex)
fi

```

and change it to:

```
# Default value
if [ “x$BACKCOLOR” = “x” ]; then
BACKCOLOR=”x”
fi
```

---

### Post by canthus13 on 2008-04-02
That worked... Thanks.

---

