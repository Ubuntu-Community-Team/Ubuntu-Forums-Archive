---
title: "ATI + FGLRX + XGL + COMPIZ + Feisty = works"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by nepenthes on 2007-05-04
Hi all,
I'm not sure if this some interesting news for you, but for me it was quite a surprise. I belong to those ATI 200M people who had Beryl working nicely under Edgy and under Feisty it worked only by using an older version and even that one had some annoying issues.
Anyway I decided to go 2D for a while and wait what´s next from the Compiz/Beryl camp.

Yesterday I installed the ATI 8.36.5 driver and to my surprise compiz (under XGL) is working now. At first I actually started it through the Beryl Manager, but it seems also to work through that 'Enable Desktop Effects' button that never worked for me.

It runs stable, fast and smooth, I am pleasantly surprised. Or shouldn't I be? I always thought that compiz and XGL is a nono.

Anyway it makes waiting for Beryl to be integrated into Compiz easier. Hopefully this will anyway happen automatically through the updates.

Nepenthes

---

### Post by zasf on 2007-05-04
I also have XGL/fglrx/compiz working but as a session choice in gdm, so that I normally don't use it.

Xgl has made great improvements, I believe it is now quite stable, but I wonder if it is/will be actively developed since it seems that AIGLX is more popular, any news about that?

Matteo

---

### Post by kpolice on 2007-05-04
XGL is still being developed.

---

### Post by GreyFox on 2007-05-04
I too, got Beryl working on my ATI 200M card.  I lurvs it :D

I followed this guide: [http://ubuntu-se.org/smf/index.php?topic=8913.msg67326](http://ubuntu-se.org/smf/index.php?topic=8913.msg67326)

---

### Post by woland on 2007-05-04
I got it working too, with the same hardware (200M).

However, in some other post (quite old, from Feisty dev. forum), there is a statement that beryl from the universe repository doesn't work with xgl.

Which version of beryl did you use?

---

### Post by strumluff on 2007-05-04
> **woland said:**
> I got it working too, with the same hardware (200M).

However, in some other post (quite old, from Feisty dev. forum), there is a statement that beryl from the universe repository doesn't work with xgl.

Which version of beryl did you use?

Thats correct, you should use version 0.2.0, you can do it simply by forcing the version of the beryl packages to that version. You will have to ensure you don't update beryl when doing updates or you can just pin the beryl packages.

I have the same hardware running XGL and beryl and it is mostly alright with a few issues forcing me to refresh gnome-panel and nautilus sometimes. Anyway I would much prefer to see more work done on the proprietary drivers to support the composite extension so us ATI users can run beryl in AIGLX without the need for XGL.

---

### Post by woland on 2007-05-05
> Anyway I would much prefer to see more work done on the proprietary drivers to support the composite extension so us ATI users can run beryl in AIGLX without the need for XGL.

I would too, yet all I see, is them, making a Vista dedicated page on their website...

---

