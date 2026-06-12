---
title: "Problem with Balazar3_3d"
date: 2010-07-20
forum: Gaming &amp; Leisure
---

### Post by SuperTeece on 2010-07-20
I installed Balazar3 and it ran with no problem until I increase the resolution and turned on full screen. Now when trying to open I get:

```
* Balazar 3 * Balazar 3 lives in /usr/share/games
* Balazar 3 * (Psyco not found; if you are using an x86 processor, installing psyco can speed up Balazar 3)
* Soya * Using Software Surface.
Video mode set failed : No video mode large enough for 1280x1024
Exception RuntimeError: RuntimeError('Video mode set failed : No video mode large enough for 1280x1024',) in '_soya.init_video' ignored
* Soya 3D * Warning : glGetString returns NULL!
Segmentation fault

```

I've tried complete removal of all three packages: python-soya, balazar3-3d, and balazar3-common. Restarted, installed again, same issue.

Any ideas?

---

### Post by lkjoel on 2010-07-20
Read the output.
That should tell you to install psyco.
```
sudo apt-get update
sudo apt-get ugprade
sudo apt-get dist-upgrade
sudo apt-get install psyco python-soya balazar3-3d balazar3-common
```
And please give me the output of: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by SuperTeece on 2010-07-21
> **lkjoel said:**
> Read the output.
That should tell you to install psyco.
```
sudo apt-get update
sudo apt-get ugprade
sudo apt-get dist-upgrade
sudo apt-get install psyco python-soya balazar3-3d balazar3-common
```
And please give me the output of: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

It worked fine without psyco before, this is something I did. What I'm looking for is, somewhere there is a config file being preserved when I uninstall the app... any idea where it is so I can delete it and get a fresh start?

---

### Post by lkjoel on 2010-07-22
> **SuperTeece said:**
> It worked fine without psyco before, this is something I did. What I'm looking for is, somewhere there is a config file being preserved when I uninstall the app... any idea where it is so I can delete it and get a fresh start?
The idea of psyco is to make the 3d graphics run better.
To remove the config files, the code is:
```
sudo apt-get purge *yourpackage*
```

---

