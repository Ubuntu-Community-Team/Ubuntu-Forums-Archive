---
title: "[SOLVED] Compiz Fusion repositories"
date: 2007-08-13
forum: Desktop Effects &amp; Customization
---

### Post by petit.padavoine on 2007-08-13
I'm totally mystified by the repositories used in the how-to in this forum and in the [ubuntu wiki](https://help.ubuntu.com/community/CompositeManager/CompizFusion):
```
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu] feisty main restricted universe multiverse
deb-src http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
```

I'm using the tuxfamily.org repositories and I have all the most recent plugins except for the paper aeroplane animations.

When I saw that the how-to used other repositories , I removed all my compiz goodies (sudo apt-get --purge remove compiz* libcompizconfig*), changed repositories, and reinstalled everything, expecting to get something even more up-to-date.

However, I found out that many plugins were now missing (such as the oh-so beautiful Cover Flow window switcher). In addition, the update manager kept popping up saying compiz-core needed to be updated (regardless of the fact that there WAS no update to compiz-core).

So, to cut a long story short, what's the deal with these repositories? In my experience, they're less up-to-date, they're buggy (ie they think there's an update when there isn't one), and they have nothing more than the tuxfamily.org ones...

---

### Post by pingpongboss on 2007-08-13
the tuxfamily.org repo is your best bet for the most up-to-date fusion packages. Trevino does a good job of updating regularly. I heard he's recently on vacation, and that's why it hasn't been updated in like a week.

---

### Post by petit.padavoine on 2007-08-13
Yeah I know. I'm just asking how come the official wiki and the how-to in this forum use another one which [cough cough] isn't **quite** as good.

---

