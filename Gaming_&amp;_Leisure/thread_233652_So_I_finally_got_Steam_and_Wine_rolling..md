---
title: "So I finally got Steam and Wine rolling."
date: 2006-08-10
forum: Gaming &amp; Leisure
---

### Post by Roasted on 2006-08-10
But...

[IMG]http://i2.photobucket.com/albums/y36/Roasted/blanksteam.png[/IMG]

How does one self fix such an issue?

---

### Post by tribaal on 2006-08-10
Whow impressive bug...

- trib'

---

### Post by Stickittotheman on 2006-08-10
You need to download the tahoma font and put it in your fonts folder.

---

### Post by MikeEnIke on 2006-08-11
I have the same problem. I downloaded the msttcorefonts package and it installed succesfully, so how do I get it to show?

---

### Post by bjweeks on 2006-08-11
You have to put the font in your windows font folder.

---

### Post by th3t1nm4n on 2006-08-11
You need to put it in "~/.wine/drive_c/windows/fonts/", if ~/.wine doesn't exhist then open a terminal and type "winecfg" to have wine make the directory for your user. If you are browsing files in Nautilus, remember that .wine would be hidden because of starting with ".", so press Ctrl+H to be able to see it in "/home/xxx/" (same thing as "~/")

```
wget http://neonpulse.net/ubuntu/steam/tahoma.ttf
mv tahoma.ttf ~/.wine/drive_c/windows/fonts/
```

(again, if ~/.wine doesn't exhist, just run "winecfg")

Also read this thread: [http://ubuntuforums.org/showthread.php?t=233260]("http://ubuntuforums.org/showthread.php?t=233260")

There's a 2nd page too with most of the answers on it, don't miss that! :p

---

