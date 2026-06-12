---
title: "Compiz just not working in 11.04 classic desktop"
date: 2011-07-08
forum: Desktop Environments
---

### Post by kelt65 on 2011-07-08
I have compiz installed, and ccsm. Currently the only window manager I can get to work is metacity.

KDE works fine with compiz.

If I even enable "desktop cube" in ccsm, my window manager dies and the proper one does not start up. Running ```
/usr/bin/compiz-decorator --replace 
```in a terminal also bombs out.

Unity seems to work fine as far as this is concerned, but I hate unity. It isn't even remotely ready to use in my opinion.

I see alot of other people posting about this with no solid answers.

I moved all the following out of the way from my old 10.10 $HOME, so this should essentially be a clean home dir. as far as compiz and GNOME are concerned:```

.        .config  .gnome2_private       .local         .thumbnails
..       .gconf   .gnome-color-chooser  .mozilla
.cache   .gconfd  .gstreamer-0.10       .mozilla-save
.compiz  .gnome2  .icons                .themes
```


Just for kicks, I created a brand new user and tried to enable compiz in classic desktop. Same thing.

What I have installed wrt to compiz:

```
tim@euclid:~$ dpkg --get-selections | grep compiz
compiz						install
compiz-core					install
compiz-fusion-plugins-extra			install
compiz-fusion-plugins-main			install
compiz-gnome					install
compiz-plugins					install
compiz-plugins-extra				install
compiz-plugins-main				install
compizconfig-backend-gconf			install
compizconfig-settings-manager			install
libcompizconfig0				install
python-compizconfig				install
```

---

### Post by wildmanne39 on 2011-07-08
Hi, first I think you should look at this link.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)
and you can use this guide to setup the cube and effects if that is your goal, it is for the cube and effects in natty but can be used for classic, you just would not have to do anything with unity plugin because it is not enabled in classic, or bother with disabling OpenGl.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by kelt65 on 2011-07-08
Actually, the problem seems to be that my nvidia driver is not enabled. I'm logging in to "Classic Desktop" not "Classic Desktop (no effects)"

If I reinstall and reboot I get the same thing. Why isn't the driver enabled? This has reprucussions beyond compiz since VLC uses the nvidia driver for acceleration ...

---

### Post by wildmanne39 on 2011-07-09
> **kelt65 said:**
> Actually, the problem seems to be that my nvidia driver is not enabled. I'm logging in to "Classic Desktop" not "Classic Desktop (no effects)"

If I reinstall and reboot I get the same thing. Why isn't the driver enabled? This has reprucussions beyond compiz since VLC uses the nvidia driver for acceleration ...Hi, that is just a bug it says it is not being used but it really is, mine is the same way, you can tell by the green dots.

---

### Post by Duncan Williams on 2011-07-09
fusion-icon
has a selector for window managers.
I can currently switch between
metacity
compiz
openbox
via this utility.
It's in software manager or synaptic.

---

### Post by charliewhizbeez on 2011-07-09
> **Duncan Williams said:**
> fusion-icon
has a selector for window managers.
I can currently switch between
metacity
compiz
openbox
via this utility.
It's in software manager or synaptic.

Yeah.

```
 sudo apt-get installe compiz-fusion-icon
```

Or you could change the default window manager to compiz.

```
gconftool-2 /desktop/gnome/session/required_components/windowmanager --type string --set compiz

```

---

### Post by kelt65 on 2011-07-11
Well I doubt "fusion-icon" would help since launching compiz-decorator manually does not.

My laptop, with an ATI chip, works fine in classic desktop with compiz. My desktop (nvidia), won't.

---

### Post by Duncan Williams on 2011-07-11
try it.
check all compiz entries in software manager.
plugins, etc.
[IMG]http://files.myopera.com/DuncanWilliams/usercss/fusion-icon.jpg[/IMG]

---

### Post by kelt65 on 2011-07-11
> **Duncan Williams said:**
> try it.
check all compiz entries in software manager.
plugins, etc.

Yes, have everything. Compiz works fine in both KDE and Unity. I just can't get the window manager to start in GNOME (classic desktop)

---

### Post by Duncan Williams on 2011-07-11
well the choice for me is in fusion-icon as per:
[IMG]http://files.myopera.com/DuncanWilliams/usercss/fusion-icon-2.png[/IMG]

---

### Post by Duncan Williams on 2011-07-11
just tested it out in ubuntu classic (11.04)
(which is available at start-up).
It works the same.

---

### Post by wildmanne39 on 2011-07-11
Hi, did you look at the link in post#2 I think it would be best to revert to the previous version of compiz and it will probably fix your compiz starting problem also.

---

