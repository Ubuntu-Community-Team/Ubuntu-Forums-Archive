---
title: "Warsow shortcut???"
date: 2006-06-17
forum: Gaming &amp; Leisure
---

### Post by jISh on 2006-06-17
How do I make a shortcut to Warsow on my desktop? Doing right click -> make link does not work, the game won't load, also right clicking on desktop and going to create launcher does not work. For these two options, a small window just pops up and then goes away. I'm pretty sure it's because the game is not being run in it's own folder.

I tried making a shell script but then nothing happens at all..
Help? :O

---

### Post by seth0x2b on 2006-06-17
Assuming that the warsow executable is in ~/warsow/, create a launcher, and use
```

sh -c "cd ~/warsow/ && ./warsow"

``` as it's command.

Cheers

P.S. A small search on the forum wouldn't hurt

---

### Post by jISh on 2006-06-17
Thanks a lot, it worked.
I did try searching, though, and most threads ended with the person saying "that still didn't work", lol.

---

