---
title: "Emerald and AWN questions"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by infamous16 on 2007-10-30
So I got AWN and Emerald to try out the new osx theme...and I have a few questions.

Emerald-
I have the emerald theme manager but when I try to apply a theme nothing happens...I double click, and nothing happens. I tried downloading a new theme and the same thing happend. I imported it, and double clicked. (nothing happend, lol.)

AWN-
I cant seem to get firefox or any other applett/launcher to work with AWN besides the ones that came with it. I drag and drop on the bar, on the awn manager screen, anywhere....and nothing happens, lol.

Thanks for the help, hopefully I can get this to fully work, lol.

---

### Post by Zorael on 2007-10-30
The theme manager doesn't load emerald when started, you have to run 'emerald --replace' to have it replace your current running window decorator. Just make a shortcut/launcher, or add it to Sessions if you want it started upon logging in.

Can't help you with AWN though.

---

### Post by infamous16 on 2007-10-30
lol now there isn't any window borders!

Thanks for the advice it worked while terminal was open!

---

### Post by Zorael on 2007-10-30
Add an ampersand (&) after any command to make it run in the background.

```
$ emerald --replace &
```

---

### Post by infamous16 on 2007-10-30
Thanks, but the window borders still go away. 

I'll try restarting, maybe?

---

### Post by Zorael on 2007-10-30
Oh, okay, I misinterpreted.

You need to add some stuff to your /etc/X11/xorg.conf, should help.

In the "Screen" section:
```
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    DefaultDepth    24
```

At least that's for Nvidia cards, may or may not work with yours (if of other manufacturer). YMMV.

---

### Post by infamous16 on 2007-10-30
thanks it worked after I restarted!

---

### Post by k0rfain on 2007-10-30
you do know there are gtk mac themes right?

---

### Post by It_Was_Luck on 2007-10-30
Check out Mac4Lin's amazing Leopard Transformation Pack if you want anything "Mac" related.

[http://ubuntuforums.org/showthread.php?t=555373](http://ubuntuforums.org/showthread.php?t=555373)

---

### Post by infamous16 on 2007-10-30
I was using that and thats why I wanted to set up emerald.

But, I got it to work and its all good now! Thanks.

---

