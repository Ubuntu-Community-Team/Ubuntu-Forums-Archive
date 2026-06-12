---
title: "Digiband"
date: 2007-09-17
forum: Game Specific Discussions
---

### Post by Perfect Storm on 2007-09-17
**UGA's News Discussion of DigiBand.**

Discuss here. All discussions fall under the general rules of the UGA Code.
No swearing, profanity, nudity or other such subversive images or communications.
No Personal Attacks. Spamming of any kind will not be tolerated.

---

### Post by Luksion Knight on 2007-09-17
i cant get it to work, it tells me it cant find libavformat.so.50

---

### Post by Perfect Storm on 2007-09-18
have you enable medieubuntu in your sourcelist?

If you have try this;

```
sudo ln -s /usr/lib/libavformat.so /usr/lib/libavformat.so.50
```

---

### Post by Luksion Knight on 2007-09-18
how do i do that?

---

### Post by Luksion Knight on 2007-09-18
actually i checked synaptic, and i do have it enabled, is this game 64-bit compatible?

---

### Post by Perfect Storm on 2007-09-18
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Here, you can setup a complete repo; [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by Perfect Storm on 2007-09-18
> **Luksion Knight said:**
> actually i checked synaptic, and i do have it enabled, is this game 64-bit compatible?

Not what  I know of.

---

### Post by kopinux on 2007-11-05
how do you install digiband on ubuntu gutsy?
does it still have the FFMPEG issue now that we have gutsy?

---

### Post by chibiskuld on 2008-05-30
Ubuntu has a seperate package you have to make sure to apt get before compiling.  I'll update the documentation soon about it, but you'll need to apt-get ffmpeg and libavformat.

---

### Post by D.Sync on 2008-06-02
I had followed your guide [here]("http://gaming.gwos.org/doku.php/guides:32bit:digiband") and unfortunately I encountered the following error:

---

### Post by Perfect Storm on 2008-06-02
32-bit guide is unmaintained at this moment - we're looking for someone to maintain it. As all the UGA staff have moved to 64-bit.

But try install the -dev of libmad, then "make clean" and try the guide again.

---

### Post by D.Sync on 2008-06-02
Problem still exists even after reinstallating those -dev.

---

### Post by D.Sync on 2008-06-02
FYI, the error code occur when I enter the following line:

make -f Makefile.linux

---

### Post by Perfect Storm on 2008-06-02
I'll check the guide when I get time and see what it come up with :)

---

### Post by D.Sync on 2008-06-02
Thanks. Hopefully got solution soon.

---

