---
title: "[SOLVED] Bottom Gray Bar"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by cartisdm on 2008-01-04
After looking at the recent posts in Community Cafe with everyone's desktops I was blown away.  I had been happy with mine (simple, yet smooth) but now I really would like to do some tweaks.

If you look at my screenshot how do I remove the gray bar at the bottom of my desktop?  The little tabs that show you which windows you have open are displayed in there and I'd like to have them either show up along the top or not at all (if possible).

Also you can see in the screenshot the browser that's open, what widget/toolbar is that guy using?

---

### Post by Borbus on 2008-01-04
The dock is avant-application-switcher, I believe. There is a guide to install it on this forum.

---

### Post by cartisdm on 2008-01-04
Sweet, I'm installing that dock right now.  As for the gray bar though...any luck?

---

### Post by cartisdm on 2008-01-04
Yea......my bad.  If I had actually put some thought into it before I posted I could have just right clicked on the bar and all the properties are there.

My bad, it was late lol.  I'll put some screenshots up in the community cafe of my desktop when it's complete

---

### Post by rainwalker on 2008-01-04
The dock is called Avant Window Navigator (not avant-application-switcher)

And to remove the panel you just right-click and choose to delete the panel

---

### Post by cartisdm on 2008-01-04
Ok, this one turned out to be more tricky than I thought.  Now I would like to remove the TOP bar (look at my screen shot).  I no longer need what's on it (Applications, Places, System) because I added that on my dock (the ubuntu symbol).  It's not letting me remove it though.

Also, how can I add the Force Quit icon to my AWN dock?

---

### Post by rainwalker on 2008-01-04
I'm not sure how to remove the top bar, but there's probably a way. I'm guessing it's hidden somewhere in gconf

I'll let you know if I find anything

---

### Post by cartisdm on 2008-01-04
> **rainwalker said:**
> I'm not sure how to remove the top bar, but there's probably a way. I'm guessing it's hidden somewhere in gconf

I'll let you know if I find anything


You were right.  I found it and using these settings the bar is finally gone!

**gconf** /apps/panel/toplevels and set these values:
auto_hide: yes
auto_hide_size: 1
expand: no
hide_delay: 1
monitor: 3
unhide_delay: 10000
x: 10000
y: 10000

---

### Post by rainwalker on 2008-01-04
Cool, have fun with AWN :)

---

