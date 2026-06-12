---
title: "Xubuntu 12.04"
date: 2012-03-12
forum: Desktop Environments
---

### Post by Fragadelic on 2012-03-12
I just wanted to say that I think Xubuntu 12.04 is shaping up quite nicely.  I've remastered it with remastersys with the non pae kernel only as I have a bunch of PC's with cpu's that aren't pae capable and it works fine.

Xubuntu 12.04 is the closest I've seen any Ubuntu variant come out that almost suits my needs perfectly out of the box.  Keep up the great work!

---

### Post by GraeW on 2012-03-12
I downloaded the Xubuntu 12.04b1 iso and did a fresh install on my laptop, wiping the last of windoze. With very little work I was able to get everything migrated through dropbox and my external HD, and with only a minor problem with Conky everything came together well. Even as a beta, it's already well-polished and I look forward to the final release (and eventual upgrade to XFCE 4.10 to follow).

---

### Post by Fragadelic on 2012-03-12
I was a bit shocked to hear that only pae kernels will be included which will make a lot of older CPU's that still work fine, not work with *buntu 12.04 out of the box forcing folks to use the alternative install.

Other than the pae kernel issue it is going to be a great release.

---

### Post by Fragadelic on 2012-03-12
I thought I'd just post a bit of info regarding thunar and network gvfs cuasing very slow first time opening due to setting up the network.

If you edit /usr/share/gvfs/mounts/network.mount and change it from:
```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=true

```

to 

```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=false

```

it will make opening up thunar very quick again even for the first time.  If you want the smb browsing you just click on the network:/// link in thyunar and it will then do the browsing search which takes a bit.

---

### Post by Peripheral Visionary on 2012-03-13
I'm a newcomer to Linux, having inherited an old computer with Xubuntu Lucid on it. Just yesterday I dared to experiment with the Beta of 12.04 (daring for a novice I guess - or maybe just dumb, lol). So far it has been quick, gorgeous, and trouble free.

I was warned by the previous owner about something called PulseAudio, and told to completely remove it if I decided to upgrade. "That's the only way sound will work on this ol' thing," he said. I'm pleased to report that Xubuntu 12.04 works fine on this old machine despite having PulseAudio on it. Maybe that's something new for us old Dell users, I don't know.

But Xubuntu 12.04 has been outstanding so far. I'm completely delighted with it.

---

### Post by Max Blyss on 2012-03-14
Going to wait for the release, but I am very pumped about 12.04.

---

### Post by Rodney9 on 2012-03-14
> **Fragadelic said:**
> I thought I'd just post a bit of info regarding thunar and network gvfs cuasing very slow first time opening due to setting up the network.

If you edit /usr/share/gvfs/mounts/network.mount and change it from:
```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=true

```

to 

```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=false

```

it will make opening up thunar very quick again even for the first time.  If you want the smb browsing you just click on the network:/// link in thyunar and it will then do the browsing search which takes a bit.

Thank You, That certainly speeds up opening Thunar.

I think I will wait for at least the RC of Xubuntu 12.04 , looking forward to it.

Rodney

---

