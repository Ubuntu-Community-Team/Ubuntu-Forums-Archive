---
title: "No sound in Pysol with Hardy Heron 8.04"
date: 2008-05-05
forum: Gaming &amp; Leisure
---

### Post by chas2007 on 2008-05-05
I've tried the following line from a terminal window:

```
sudo cp /usr/lib/python2.5/site-packages/pysolsoundserver.so /usr/share/games/pysol/
```

It worked in Gutsy (using "python2.4" instead) but it doesn't seem to work for Hardy.  Any suggestions?

:confused:

---

### Post by chas2007 on 2008-05-16
I've had no luck getting this to work.  I have discovered that there is a new and improved Pysol, called PysolFC (Fan Club):

[http://pysolfc.sourceforge.net/]("http://pysolfc.sourceforge.net/")

This new version is even better than the older one, it has LOTS more games.  It has an easy to install download for Windows.  But the Linux download has been difficult.  I get numerous error messages about files not being read correctly, etc.

Is there any chance that PysolFC can be added to the Ubuntu repositories?

---

### Post by binarycortex on 2008-07-02
I had the same problem, until I installed the windows version under wine. Now it works and has sound. Please add Pysol Fan Club edition to the repositories.

Ian

---

### Post by Sef on 2008-07-02
I got sound with Pysol this way:

```
sudo apt-get install pysol-sound-server pysol-sounds
```

---

### Post by chas2007 on 2008-10-08
> **binarycortex said:**
> I had the same problem, until I installed the windows version under wine. Now it works and has sound. Please add Pysol Fan Club edition to the repositories.

Ian

I also got Pysol Fan Club edition, windows version, to run under wine.  But at the end of each game, the program freezes, and has to be restarted.  Also, the motion of the graphics is a bit stiff and jerky.

The Fan Club edition is such an improvement over the old Pysol, it has more games and better options.  I'd really like to see the Linux version available in the repositories.

I live in hope...

---

