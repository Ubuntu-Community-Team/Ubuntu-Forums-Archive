---
title: "KDE apps taking over gnome"
date: 2008-08-18
forum: Desktop Environments
---

### Post by spacedoggy on 2008-08-18
i use gnome desktop and a few kde apps, amarok, ktorrent k3b, the really good ones...

i was compiling amarok and installed a load of prereqs for it, including kde packages, now when i'm runnig kde apps like ktorrent and go to open a folder, it opens them in konquer instead of nautilus when i open a avi file it opens in Noatun instead of VLC, considering noatun is a sound player, this sucks bigstyle. 

How do I stop unwanted KDE apps cannibalising my gnome environment?

---

### Post by cdtech on 2008-08-18
**Sorry, I just re read your post, I don't think this is a fix for your situation. You could try it though, you can always copy your backed up file to the original state.**

I understand your pain. I was flooded with KDE apts using my default GNOME desktop so this is what I did:

If you use the Gnome desktop (like I do) try this:

**Make a backup:**
```
mkdir ~/.desktopbackup
cp -R /usr/share/applications/ ~/.desktopbackup
```

On a command line type:
```
for i in /usr/share/applications/kde/*; do echo "OnlyShowIn=KDE;" | sudo tee -a $i; done
```

You could also do the same if you use KDE by changing it to:
```
for i in /usr/share/applications/*; do echo "OnlyShowIn=GNOME;" | sudo tee -a $i; done
```

Hope this helps.........

---

