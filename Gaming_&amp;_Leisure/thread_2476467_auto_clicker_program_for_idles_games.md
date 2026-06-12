---
title: "auto clicker program for idles games"
date: 2022-06-27
forum: Gaming &amp; Leisure
---

### Post by vctor98 on 2022-06-27
Hi everyone,

[B]Is there auto clicker software that works in Ubuntu Linux ??
[/B]
I searched in google and I found [auto clicker]("https://maxautoclicker.blogspot.com/p/auto-clicker.html") for windows and [auto clicker for android]("https://maxautoclicker.blogspot.com/2022/06/auto-clicker-android-apk.html").
This auto clicker program is useful in idles games or clicking games and that helps of repeated clicks tasks.

---

### Post by TheFu on 2022-06-27
You can move the mouse a few pixels using a few different X/Windows tools.  xdotool with a 14 minute sleep loop?  There are lots of X/Windows automation tools  cnee/xnee is another. These have been around for 20+ years.

I don't know how to accomplish the same thing with Wayland.  Maybe ydotool?  But ydotool can only be run as root, which isn't good.

If you want to automate webapps, there's an addon for chromium/firefox called selenium-IDE. This is a bit heavier and only works inside a single browser window (it cannot grab data to be saved in other programs).

---

