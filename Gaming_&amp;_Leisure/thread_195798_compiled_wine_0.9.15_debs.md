---
title: "compiled wine 0.9.15 debs"
date: 2006-06-13
forum: Gaming &amp; Leisure
---

### Post by LordRaiden on 2006-06-13
I compiled wine 0.9.15 debs a week ago, and its working great. DirectX support has been taken to a new level. The only thing that I can't seem to get working is the ALSA driver in winecfg. However, I am content using OSS drivers.   I wanted to post the debs (wine and wine-dev) up somewhere so the rest of the community could crack a shot at it, but I don't know where. Any suggestions?

---

### Post by eqisow on 2006-06-13
Well, the Wine 0.9.15 are actually already available in a repository.

```
deb http://wine.budgetdedicated.com/apt dapper main
```

I've also already made a version of Wine 0.9.15 with the World of Warcraft patch available on the Ubuntu wiki.

[https://wiki.ubuntu.com/Wine]("https://wiki.ubuntu.com/Wine")

It was a good thought, but it's pretty much already taken care of. :)

---

### Post by LordRaiden on 2006-06-13
For some reason, I can't download it. I have to download the source then compile. It says something about the file being referenced but not existing.

---

### Post by eqisow on 2006-06-13
You can't download it from the wiki or from the repository?

Edit: I can download from the wiki fine, I just tried it.

---

### Post by LordRaiden on 2006-06-13
I can't download the deb from the repository. I followed all the WineHQ instructions at their site.

There is no real point for me, unless the repository has ALSA drivers.

---

### Post by eqisow on 2006-06-13
I just installed wine-dev (from the repository) just fine. Perhaps you'd like to post your exact error message along with what you doing? Of course, like you said, there may be no point for you. But it'd also be nice not to have to compile again when 0.9.16 comes out.

---

### Post by flapane on 2006-06-13
i have the .14 (amd64), How can I use this new deb to update my 0.9.14 ? 
p.s I don't want to lost my wine settings

---

### Post by eqisow on 2006-06-13
I take it you installed Wine in a chroot? Or are you running i386 Ubuntu on your amd64 processor? Either way, you can just install the new version on top of the old one and keep all of you're settings.

---

### Post by flapane on 2006-06-13
no I am not using a chroot, I simply used --force-all to install it into my ubuntu amd64 distro

---

### Post by LordRaiden on 2006-06-14
Yeah it works. I deleted my old /etc/apt/preferences and it works. ALSA driver is still a pain though (killed Warcraft III TFT during a game of DOTA).

---

