---
title: "How do you set a terminal as wallpaper?"
date: 2007-05-16
forum: Desktop Effects &amp; Customization
---

### Post by pseudolobster on 2007-05-16
Hi there,

I'd like to know how you can go about setting a terminal running an output of dmesg (I seem to recall this being referred to as the root console or something /dev/pty0 or whatever it may be).. as the desktop wallpaper (or overlaid thereupon).

I've seen it done before in screenshots etc, and I think there was even an option in some version of redhat I tried in the late 90's... and it would really fit the theme I'm going for, not to mention informative for all the finicky driver things that have been going on lately.

Thanks!

(edit: I'm fairly competent, I just haven't used linux since kernel 2.2 was the latest thing... I guess I'd like just to know how to disable gnome's wallpaper and to set a terminal to use the space.. I seem to recall doing this with xf86, fwm95 and xterm, but I'd like to know if there's a more up-to-date approach.)

---

### Post by earobinson on 2007-05-16
in the gnome-terminal you can click edit->profile then click the effects tab and you can change it there

---

### Post by pseudolobster on 2007-05-16
Thanks, I tried there...

it looks like from there I can choose a wallpaper for that terminal, or transparency-effect...

but what I'm trying to do is have the contents of dmesg display to my desktop wallpaper... as in instead of wallpaper, I have a terminal that displays a constantly updated log of kernel messages.

---

### Post by nicepants on 2007-05-16
root-tail might be what you're looking for, i haven't checked but i assume it's in one of the default repositories.

---

### Post by earobinson on 2007-05-16
oops sorry I must have miss read your post. what your looking for is this ([http://ubuntuforums.org/showthread.php?t=36811](http://ubuntuforums.org/showthread.php?t=36811)) no?

---

### Post by pseudolobster on 2007-05-17
Thanks! That was more or less exactly what I was looking for...

I'll have to fiddle with devilspie, but I guess I'm on the right track...

As for root-tail... I think if gnome / nautilus weren't using that space, I could use root-tail on /var/log/kern.log.... but as for now, nothing happens.

Otherwise, doesn't the kernel output those messages to a console device, like /dev/tty0 or something? Would I just be able to set Eterm (or whatever) to use that console?

Thanks for the info guys!

---

### Post by 23meg on 2007-05-17
Here's an alternative if you don't want to fiddle with Devil's Pie:

[http://ubuntuforums.org/showthread.php?t=81727](http://ubuntuforums.org/showthread.php?t=81727)

---

