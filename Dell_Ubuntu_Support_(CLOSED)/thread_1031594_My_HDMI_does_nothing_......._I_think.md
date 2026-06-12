---
title: "My HDMI does nothing ....... I think"
date: 2009-01-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bolex100 on 2009-01-05
Forgive me if I am expecting the wrong thing from my HDMI socket.  I unplugged the HDMI lead from my PS3 and plugged it into my laptop.  I set the TV to HDMI mode.  Played a DVD.  sat back :popcorn:.  I was expecting the TV to mirror the laptop's display and/or sound but I got nothing at all.

DO I need to enable something?

Dell inspiron 1525n
Ubuntu studio 8.01

---

### Post by ytsejam1138 on 2009-01-05
Most laptops have a key combination to toggle the screen from the laptop screen to an external monitor.  It's usually Fn+ one of the function keys.  Look at your function keys and one should have a picture (usually in blue) of an empty rectangle and a solid rectangle.  This is the toggle key for the display.

---

### Post by bolex100 on 2009-01-05
yep.  I have a CRT/LCD key (F8) but it doesn't make the HDMI work.  ctrl+F8 shrinks the view.
I notice that the TV does detect something though.  The TV only displays "HDMI Stereo" while it is plugged it to the laptop.

---

### Post by bolex100 on 2009-01-05
yep.  I have a CRT/LCD key ( F8 ) but it doesn't make the HDMI work.  ctrl+F8 shrinks the view.
I notice that the TV does detect something though.  The TV only displays "HDMI Stereo" while it is plugged it to the laptop.

---

### Post by damis648 on 2009-01-05
Don't double post, just please edit your previous post.

Anyway, you have to press Fn+F8. :popcorn:

---

### Post by jespdj on 2009-01-06
What video card do you have? If it's an nVidia and you're using the nVidia proprietary driver, try nvidia-settings. Install it if it isn't yet installed:
```
sudo apt-get install nvidia-settings
```
Then run it with the command:
```
nvidia-settings
```
This allows you to configure a lot of things, including the second screen. You might need to run it with administrator privileges so that it can write to your /etc/X11/xorg.conf configuration file:
```
gksudo nvidia-settings
```

---

### Post by bolex100 on 2009-01-07
>  Re: My HDMI does nothing ....... I think
Don't double post, just please edit your previous post.

Anyway, you have to press Fn+F8. 

Didn't realised that I have fired off the first one.  Anyway, Fn+F8 doesn't work.:(

---

