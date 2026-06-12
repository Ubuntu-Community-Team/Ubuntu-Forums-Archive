---
title: "Cool live background idea, is it possible?"
date: 2019-07-01
forum: Gaming &amp; Leisure
---

### Post by shadowstorm56 on 2019-07-01
So I have fish and they are happy and relaxing, I had a cool idea that idk if it's possible but it would be cool if it was. Is there a way to have a live desktop backround on ubuntu? Like an ip camera feed or somthing. Then I could have a live fish tank feed background! I know this is not gaming but it seems to fit leisure.

---

### Post by crip720 on 2019-07-01
Check out this google search, should be something you can use.  [https://www.google.com/search?client=opera&q=ubuntu+video+as+wallpaper&sourceid=opera&ie=UTF-8&oe=UTF-8](https://www.google.com/search?client=opera&q=ubuntu+video+as+wallpaper&sourceid=opera&ie=UTF-8&oe=UTF-8)    
Think VLC can maybe capture camera output.

---

### Post by CatKiller on 2019-07-01
It used to be done all the time. The phrase you'd be looking for is "drawing to the X root window." You'd need to research whether it's still possible with whichever window manager you're using.

The alternative is to draw a borderless window for your content above the desktop and below all the other windows. "undecorated" and "keep_below" are the hints to the window manager that would achieve that.

Conky can take either of those approaches if you wanted to see how another application handles it. It might be a fun project for you.

---

### Post by shadowstorm56 on 2019-07-01
Thanks lots :) I shall experiment.

---

### Post by again? on 2019-07-01
In quick test, komorebi works.
Deb file here [https://github.com/cheesecakeufo/komorebi/releases/tag/v2.1](https://github.com/cheesecakeufo/komorebi/releases/tag/v2.1)

Use Wallpaper Creator to add a video file to wallpapers.

The app installs to a MacOS location of /System/Applications
Should see in your Application menu > Settings
[LIST]
[*]Komorebi
[*]Wallpaper Creator
[/LIST]


**Note these sort of apps are usually resource hogs.

---

