---
title: "RuneScape stuck on logging in."
date: 2012-10-07
forum: Gaming &amp; Leisure
---

### Post by Zomgrick on 2012-10-07
I'm trying to play RuneScape on Ubuntu, So I've installed icedtea7 which is the browser plugin for java if I'm right. After installing it I was able to get to the login screen but as soon as I try to log in it gets stuck at Loading - please wait. It will not go further than that. Is there anybody who had the same problem and knows how to fix this? Or is there anybody that can give me tips in general. That would be much appreciated.

---

### Post by Zomgrick on 2012-10-08
Noone has an idea?

---

### Post by HikariKnight on 2012-10-09
That is often caused by the jagexcache getting corrupt(most likely from a slight connection hiccup) so you will have to delete the jagexcache folder located in your home folder, or just open the terminal and type in
```
rm -rf ~/jagexcache
```

the next time the game starts it will redownload the cache which should be fine.

also as a note for the future it would be easier and much faster to just post in the linux thread in the official runescape tech support forums, quite a few linux users there that know the game and the issues you can get and are willing to help :)

---

### Post by LiamOS on 2012-10-09
Hopefully the previous post fixed it, but you could also try it in Chromium(Runescape crashed Firefox in 12.04 when I used to play), or using the Jagex applet.

---

### Post by Zomgrick on 2012-10-10
I will test these things as soon as I get home. Thanks for responding :)

---

