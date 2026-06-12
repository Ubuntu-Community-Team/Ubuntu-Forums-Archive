---
title: "Samsung Writemaster SH-S223 not burning or ripping"
date: 2008-12-22
forum: General Help
---

### Post by joehte on 2008-12-22
Hi,

I have a sata version of this Samsung Writemaster, and I'm not able to write DVDs or rip CDs to mp3s using it. Nor play audio CDs. Data CDs/DVDs seem to be readable.

When ripping, the ripper seems to work ok. But the resulting files are way too big, like it just copied the raw data. I can open the CD and see as many tracks as there should be. But for some reason they are shown with the extension .wav. I seem to remember that's not how it's supposed to be.

When I tried burning a DVD with brasero, it just got stuck to 0% and nothing happened.

Quite annoying... anyone have these Samsung drives working with Ubuntu or any idea how to solve this problem?

---

### Post by joehte on 2008-12-24
Bump.

Anyone have any information on this? The Samsung drives are quite affordable and fast according to tests so I'd assume there's many people with these drives.

---

### Post by joehte on 2008-12-25
Update:

I manage to now play audio CDs from the drive. This started working after I put the SATA interface to AHCI mode from BIOS.

Burning or ripping still doesn't work.

---

### Post by joehte on 2008-12-26
Another update:

I got ripping of mp3s from CDs to work. It doesn't work with the default "Audio CD extractor" (Sound Juicer). But it does work with ripperX. Install it using:

```
sudo apt-get install ripperx
```

It's not quite as polished as Sound Juicer, but is easy enough and works.

Still to solve the DVD/CD burning issue.

---

