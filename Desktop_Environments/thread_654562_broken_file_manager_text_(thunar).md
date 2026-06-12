---
title: "broken file manager text (thunar)"
date: 2007-12-31
forum: Desktop Environments
---

### Post by camb416 on 2007-12-31
Hi all

my thunar is effed up. The font size is bigger than everything else. 

[IMG]http://farm3.static.flickr.com/2221/2151866018_b489baa42b.jpg[/IMG]
[link to hi-res]("http://www.flickr.com/photo_zoom.gne?id=2151866018&size=o")

When I run

```
sudo thunar
```

...it comes up fine... its just when I run it under my account that its messed up.

I've tried messing with the themes manager, and the font will change, but its always a bunch of sizes larger than everything else.

Anyone have ideas!?! Something to do with GTK maybe? :confused:

I'm on xubuntu 7.10.

thanks in advance

-C

---

### Post by mali2297 on 2007-12-31
Since it works with sudo, the problem is in your personal configurations. Remove the contents of ~/.config/Thunar and ~/.cache/Thunar by running this in the terminal:
```

rm -vi ~/.config/Thunar/* ~/.cache/Thunar/*

```
If you have some settings in Thunar that you want to keep, you can instead rename the files.

---

### Post by camb416 on 2007-12-31
thanks alot mali.

I did try that, and it didn't seem to fix it. Neither did reinstalling thunar.

what worked was reinstalling any package that had anything to do with thunar, plus whatever installed GTK packages i have on here plus icewm.

although maybe im just nuts.

again, thanks kindly

---

