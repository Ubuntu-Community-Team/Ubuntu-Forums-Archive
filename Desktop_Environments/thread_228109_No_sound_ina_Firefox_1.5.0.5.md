---
title: "No sound ina Firefox 1.5.0.5"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Zmija on 2006-08-02
When I'm watching the film on youtube or google, there's no sound?

How Can I enable it?

EDIT: and, yes, everythiing is working fine! XMMS & All other player have sound! My speakers ARE Turned ON... :)

---

### Post by ironfistchamp on 2006-08-02
Sometimes I have this problem. Usually after using another media app like amarok or xmms. You could try shutting down firefox, opening a terminal, typing

```

killall esd

```

and starting firefox again. That fixes it for me and I have suggested this to other people and it works for them. I hear it is something to do with the fact that Flash uses OSS. 

Hope this helps

Ironfistchamp

---

### Post by gborzi on 2006-08-02
Install alsa-oss > sudo apt-get install alsa-oss then edit /etc/firefox/firefoxrc with your preferred editor and change
> FIREFOX_DSP="none" to > FIREFOX_DSP="aoss"
That's all.

---

### Post by gborzi on 2006-08-02
Sorry, double post.

---

### Post by ironfistchamp on 2006-08-03
I tried the alsa-oss thing but I still have to do killall esd sometimes. Shame.

---

### Post by gborzi on 2006-08-03
> **ironfistchamp said:**
> I tried the alsa-oss thing but I still have to do killall esd sometimes. Shame.
Perhaps this Howto can be helpful: [http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

---

### Post by ironfistchamp on 2006-08-03
Thanks lets hope it works.

---

### Post by Zmija on 2006-08-03
Yep it's working....


THNX To All...=D>

---

