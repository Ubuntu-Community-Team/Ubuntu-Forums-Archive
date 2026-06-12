---
title: "TENNIS for Ubuntu Linux"
date: 2007-04-15
forum: Gaming &amp; Leisure
---

### Post by jorgerosa on 2007-04-15
Hi, im looking for a tennis game for Linux, at the moment i found nothing.
Can you help me guys? By the way other (good) sports games? (Only freeware or open-source, please).

---

### Post by MonkeyBoy on 2007-04-15
[http://freetennis.sourceforge.net/](http://freetennis.sourceforge.net/)

This looks like it might be what you want.

---

### Post by jorgerosa on 2007-04-15
Thanks MonkeyBoy. Just one issue "you must compile it"... :icon_frown:  ....

---

### Post by MonkeyBoy on 2007-04-15
I just did that.  If you read the INSTALL.txt file in the directory it shows a list of dependancies.  You need to go through the list and on the command line type:

```
sudo apt-get install NAME OF DEPENDANCY
```

Most of them you will find you already have.  Then go to the directory in the command line:

```
cd freetennis-0.4.8
```

Assuming you put it in your home directory.  Then just type ```
make
``` and wait while it does it's stuff.

Once that is done launch the game with ```
./freetennis -newbie

```

It is a wierd style of game but looks quite good.  It's a shame that it looks a bit abandoned.

---

### Post by jorgerosa on 2007-04-15
NICE! Thx again. With Monkeys so friendly who needs humans? You are the man!... *Sorry...* The Monkey!

---

