---
title: "Help? Permission issues with game installation"
date: 2011-07-27
forum: Gaming &amp; Leisure
---

### Post by xDante on 2011-07-27
I have decided to download elite combat, as some of you may now you must download Wolfestein first, I downloaded wolfestein, I run the installation through the terminal, I follow the instructions fine up until I need to select a path to install the game at, I use a path such as home/user/documents/et but no matter what I choose it seems I don't have permission to acess my own computer, so how do I change the permissions? I had to download this game twice and I'm not giving up! :D

---

### Post by oldrocker99 on 2011-07-28
Hmmmm...try this:

sudo chown whatever:whatever /home/whatever

That might well work. (substitute "whatever" for your home directory's anme and your username (should be the same).

---

