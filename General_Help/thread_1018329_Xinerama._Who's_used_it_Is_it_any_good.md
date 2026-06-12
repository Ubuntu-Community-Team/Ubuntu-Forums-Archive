---
title: "Xinerama. Who's used it? Is it any good?"
date: 2008-12-22
forum: General Help
---

### Post by Roasted on 2008-12-22
I'm running a 19" LCD and 24" LCD. I'm trying to figure out if there's any way I can have separate wallpapers on each of my monitors. I'm using TwinView on a 9600GT 512mb 256bit Nvidia graphics card.

I've read Xinerama is a good alternative, but I've read some conflicting information that it's slower than TwinView. I'm just curious if any users have used any of these and what their experience is.

---

### Post by jpkotta on 2008-12-22
TwinView is generally better on NVidia.  Also, it looks like Xinerama to most window managers, so they know there are multiple monitors.  Unforunately, Xinerama doesn't do well with monitors with different resolutions.  

Try nitrogen for the wallpaper.

---

### Post by Roasted on 2008-12-22
Yeah, I have different resolutions so a requirement for me would be something that plays nicely with that...

What is this nitrogen you speak of?

---

### Post by jpkotta on 2008-12-22
Generally it's a problem of the window manager not playing nicely with the different screens, not the X server.  I've never had to deal with it, but see this: [http://ubuntuforums.org/showthread.php?t=985862](http://ubuntuforums.org/showthread.php?t=985862)

```
aptitude show nitrogen
```

---

