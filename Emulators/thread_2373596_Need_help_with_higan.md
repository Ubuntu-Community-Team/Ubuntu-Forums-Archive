---
title: "Need help with higan"
date: 2017-10-07
forum: Emulators
---

### Post by carega on 2017-10-07
Hello all,

So I recently switched to amd64 architecture on a fresh install of ubuntu 16.04. Therefore I can't use ZSNES nor GENS to play snes or sega games. I found higan but can't make it work in any way. Every time I load a ROM it shows the following message:

> Error: missing required file:

/home/gorremu/.local/share/higan/Super Famicom.sys/manifest.bml

I don't really understand what this is about. I know higan works very differently from other emulators, however I don't know if this is a file I should have or higan should be creating or what. The manual does not say much about this except the logic behind Manifests. I also don't know if this has anything to do with the game format (Icarus supposedly supports .zip) or what.

Can anyone please help me?

---

### Post by kostkon on 2017-10-07
You can still install zsnes, i.e.:
```
sudo apt-get install zsnes
```

Gens [looks like it will require a bit more effort]("https://gist.github.com/elundmark/10538373").

---

### Post by carega on 2017-10-08
As I'm using amd64 architecture I'd rather not install any of them, I think it would be a real pain to make them work and plus I have to install a lot of other things don't I?

---

### Post by kostkon on 2017-10-09
> **carega said:**
> As I'm using amd64 architecture I'd rather not install any of them, I think it would be a real pain to make them work and plus I have to install a lot of other things don't I?
Zsnes from the repos works fine, no extra steps needed.

---

### Post by carega on 2017-10-09
Ok I'll give it a shot. But how do I get higan to work anyway?

---

