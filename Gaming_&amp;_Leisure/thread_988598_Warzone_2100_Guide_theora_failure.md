---
title: "Warzone 2100 Guide theora failure"
date: 2008-11-20
forum: Gaming &amp; Leisure
---

### Post by chessboxing on 2008-11-20
Hi
I wanted to install Warzone 2100 on a clean Ubuntu 8.04.1 LTS 64-bit system. So this forum has a nice section with guides. I followed this [guide]("http://gaming.gwos.org/doku.php/guides:64bit:warzone_2100?do=backlink") (specified for 8.04). But at the "make" command is says this:
```
checking for THEORA... configure: error: Package requirements (theora >= 0.1) were not met:

No package 'theora' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables THEORA_CFLAGS
and THEORA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
theora is installed on my system at synaptics already, I noticed (1.0 beta3-1).
What is expected to be done now?

---

### Post by Perfect Storm on 2008-11-20
Also did you install its -dev package?

You know that you can install an ubuntu package instead of compiling?

---

### Post by chessboxing on 2008-11-22
> **Artificial Intelligence said:**
> Also did you install its -dev package?

You know that you can install an ubuntu package instead of compiling?

I don't think I specifically installed "its-dev" package. I wouldn't know how to get the idea to do so. Because the guide didn't mention it.
No I didn't know that there was a package already. That sounds great I'll give it a shot when I get on my system.
However I'd like to solve also this theora prob. hmmm

---

### Post by Perfect Storm on 2008-11-22
```
sudo apt-get install libtheora-dev
```

---

### Post by chessboxing on 2008-11-24
> **Artificial Intelligence said:**
> ```
sudo apt-get install libtheora-dev
```

when I do this via the synaptics it requires me to remove first libtheora0 (1.0beta3-1hardy). So I try...
But when I check this, it wants me to remove really important parts, like brasero, gnome-desktop, totem, plugin etc.... But How is this possible, because why delete all these programs when they do not necessarily depend on the theora codec? And because I want to delete theora I have to give up all the rest??? This is not acceptable to me. Or will it not remove these parts but just give up the cooperation with this theora plugin?
Give me knowledge :)

btw warzone 2100 works via synaptics, but How maybe to update with trunk version?

---

### Post by Perfect Storm on 2008-11-24
See if there's another -dev of it in synaptic. There's only one in 8.10

> btw warzone 2100 works via synaptics, but How maybe to update with trunk version?

You can run it as a seperate, but do that in you home directory instead.

---

### Post by chessboxing on 2008-11-24
> **Artificial Intelligence said:**
> See if there's another -dev of it in synaptic. There's only one in 8.10



You can run it as a seperate, but do that in you home directory instead.

ta I'll just play the repo version. As I don't want this issue to be the subject instead of playing the game. I'm not going off the road :)
however if someone else bumps into this situation, pls report!

---

### Post by ubuntu.daemon on 2008-12-15
how did you go about doing that? just like the whole compile process or what?  and did you have to unistall the version you had installed via ubuntu repository?

---

