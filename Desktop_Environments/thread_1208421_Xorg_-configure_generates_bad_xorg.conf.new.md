---
title: "Xorg -configure generates bad xorg.conf.new"
date: 2009-07-09
forum: Desktop Environments
---

### Post by Janhouse on 2009-07-09
I am using Ubuntu Jaunty on HP Compaq 6715b laptop with Radeon x1200.
X1200 is no longer supported by fglrx driver so I am using open source radeon driver.

Everything is allmost nice but sometimes screen gets teared (some random lines flashes/flickers on screen or something like that). It is annoying and I wanted to get rid of it.

So I went to #radeon irc channel and some nice people said that I have to add some lines to xorg.conf.

>  Okay, the option is for your xorg.conf, it's called EXAVSync.

The problem is that I don't have xorg.conf and if I generate one with
```
sudo X -configure
```
and try to run X with generated xorg.conf.new it doesn't start up Xorg.

Any ideas?
Maybe there is some temporary generated xorg.conf that is correct?

Generated xorg.conf.new: [http://paste.php.lv/47db3f343fde5e8be5363e3d9d4dd7bc/nonum](http://paste.php.lv/47db3f343fde5e8be5363e3d9d4dd7bc/nonum)
Xorg.0.log: [http://paste.php.lv/a69ea8699017e128fb531971e0b79728/nonum](http://paste.php.lv/a69ea8699017e128fb531971e0b79728/nonum)

---

