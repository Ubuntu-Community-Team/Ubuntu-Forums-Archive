---
title: "Amarok crashes after flash starts playing in Firefox..."
date: 2008-07-04
forum: Desktop Environments
---

### Post by Toupee on 2008-07-04
I think.

Amarok usually plays music fine when I boot up, but after I've played some Youtube videos or something (where the sound doesn't work half the time, anyway, unless maybe I use Flash BEFORE amarok?) Amarok just crashes when I play a track.  I have to kill amarokapp before loading it up again, but it'll just do that til I restart. I can navigate the program until I try to play a song, it's only when I play a song does it completely freeze up.

I guess I should do a little rebooting and investigative work, do some experiments with a control.  But anybody know what would fix such a conflict?

---

### Post by clarkburbidge on 2008-07-31
I can confirm this!

Amarok freezes when I start to play a song after perviously starting a flash video in firefox.

It also works the other way around...

If I've got Amarok playing and try to view some flash video the video plays for a few seconds and then crashes.

I'd love to help nip this on in the bud. Anyone wanna walk me through the modprob and grep business?

---

### Post by tuxxy on 2008-07-31
Are you both running GNOME, I had issues when I installed KDE apps too in GNOME.  I solved it by removing all KDE files and now my system is a lot more stable.

---

### Post by clarkburbidge on 2008-07-31
Wow, now it seems to work!

I did this between now and then...

```
sudo apt-get install libflashsupport
```

on this recommendation

[http://ubuntuforums.org/showthread.php?t=695207](http://ubuntuforums.org/showthread.php?t=695207)

---

### Post by clarkburbidge on 2008-07-31
I am in Gnome on Hardy, and yes, Amarok is a KDE app, but now it seems to be happy.

I was looking at [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/68187](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/68187), after doing the above apt-get, and going to do some tests to see if it was Firefox tab related, and now it's fixed.

---

### Post by Lanky Juggler on 2008-08-02
Hey! This totally solved my problem, too.  I was having the same issues.  Thanks a bunch!

---

### Post by marikka on 2008-08-03
I had the same problem and this solved it! One symptom was also that the mplayer plugin in ff3 showed the first video I tried to see, but not those after that. I'm not sure if this fixes that, though.

---

### Post by machimocho on 2008-08-06
> **clarkburbidge said:**
> Wow, now it seems to work!

I did this between now and then...

```
sudo apt-get install libflashsupport
```

on this recommendation

[http://ubuntuforums.org/showthread.php?t=695207](http://ubuntuforums.org/showthread.php?t=695207)

this code solved the problem for me :)

---

