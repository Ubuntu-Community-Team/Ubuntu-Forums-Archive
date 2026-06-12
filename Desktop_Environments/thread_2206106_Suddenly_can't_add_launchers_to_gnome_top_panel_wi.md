---
title: "Suddenly can't add launchers to gnome top panel with ALT-right-click"
date: 2014-02-17
forum: Desktop Environments
---

### Post by desconocido on 2014-02-17
I have a new computer which has the amd64 version of Ubuntu 12.04.3 installed. (Also has unity and unity2d removed and gnome-shell installed - I use Gnome Classic.)

I eventually found that I could put more launchers in the gnome top panel by holding down ALT and right-clicking in the top panel.

Because of other problems, I have re-installed this Ubuntu, and because of advice received, I let Upgrade Manager upgrade the system.
It upgraded 282 packages.

Somewhere along the line I have lost the ability to ALT-right-click in the gnome top panel.

I can still get them there in by dragging the icon of an executable from nautilus into the panel. And I can remove them by going to /home/bob/.config/gnome-panel/launchers
Removing the file in that folder, followed by 'killall gnome-panel' removes icon from top gnome panel.

However I can't move the launchers anymore. Any idea how I can get ALT-right-click-ability back?

---

### Post by ibjsb4 on 2014-02-17
Try

Ctrl + Alt + R-click

---

### Post by desconocido on 2014-02-17
> **ibjsb4 said:**
> Try

Ctrl + Alt + R-clickThanks, but doesn't work.

---

### Post by ibjsb4 on 2014-02-17
??

[http://ubuntuforums.org/showthread.php?t=1968949&p=11888709#post11888709](http://ubuntuforums.org/showthread.php?t=1968949&p=11888709#post11888709)

Are you running compiz or metacity?

```
if [ $(pgrep -c metacity) -gt 0 ]; then
  echo "metacity is running"
elif [ $(pgrep -c compiz) -gt 0 ]; then
  echo "compiz is running"
fi
```

---

### Post by Frogs Hair on 2014-02-17
I have to use windows/super key + Alt + RC to get panel access  in the gnome fall-back session.

---

### Post by desconocido on 2014-02-17
> **ibjsb4 said:**
> Compiz or Metacity?
Compiz

---

### Post by desconocido on 2014-02-17
> **Frogs Hair said:**
> I have to use windows/super key + Alt + RC to get panel access  in the gnome fall-back session.
Yes!! I wonder if it's documented anywhere.

---

### Post by ibjsb4 on 2014-02-17
Super key I think is for compiz only.

With most people only one combination of keys will work.  On my box, both Ctrl/Alt/rc and just Alt/rc works (with metacity).

---

### Post by Frogs Hair on 2014-02-17
I have had to use to use Super + Alt + RC since 12.04 on both computers whether logged into no effects or not ?? 

```
wmctrl -m
Name: Metacity

```

---

### Post by desconocido on 2014-03-06
> **ibjsb4 said:**
> Super key I think is for compiz only.

With most people only one combination of keys will work.  On my box, both Ctrl/Alt/rc and just Alt/rc works (with metacity).

Well, I've re-installed Ubuntu again and this time I have installed gnome-panel instead of gnome-shell or gnome-fallback.

Now
SUPER-ALT-rightclick works
ALT-rightclick works
CTRL-ALT-rightclick fails

!

---

