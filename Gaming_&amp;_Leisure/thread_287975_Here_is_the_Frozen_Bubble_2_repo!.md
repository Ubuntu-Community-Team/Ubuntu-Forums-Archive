---
title: "Here is the Frozen Bubble 2 repo!"
date: 2006-10-29
forum: Gaming &amp; Leisure
---

### Post by plb on 2006-10-29
deb [http://thomas.enix.org/pub/debian/packages](http://thomas.enix.org/pub/debian/packages) edgy main

apt-get update && apt-get install frozen-bubble 

Enjoy ;]

This comes from frozen bubble homepage and works perfectly for me.

---

### Post by picpak on 2006-10-29
It complains about missing pubkeys, but it works good.

*edit* Just tried it. It looks kind of ugly IMO. Bring back the old 2D penguins!

---

### Post by plb on 2006-10-29
We need more ubuntu players on their...multiplayer is pretty fun :)

---

### Post by zgerrz on 2006-10-29
Here are the commands to receive the public key:
```

gpg --keyserver pgpkeys.mit.edu --recv-key 98D3F7A7
gpg -a --export 98D3F7A7 | sudo apt-key add -
```

---

### Post by Swoop on 2006-10-30
Thanks .. works great ! :D

Now how do i get it localized to test other languages of fb 2 ?

---

### Post by juraj on 2006-10-30
I haven't found high quality SFX in any of these reps, and you get them in the tarball on frozen-bubble.org.

BTW why doesn't checkinstall work after make-ing frozen bubble? It pops up a ton of messages that some files are missing. Can anyone look into that?
tia

---

