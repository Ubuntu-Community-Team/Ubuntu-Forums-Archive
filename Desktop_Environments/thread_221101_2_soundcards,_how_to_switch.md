---
title: "2 soundcards, how to switch?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by mrbrdo on 2006-07-22
Hello

I have an USB soundcard and an integrated soundcard in my notebook. When i have the USB soundcard plugged in, i want it to use that one, and when it's not, i want it to use the integrated one. Any way to do this (or using a switch script)? Currently if i have the USB soundcard plugged in at boot, it usually uses it (but not always - no idea why), but i don't know how to switch to it when i plug it in after boot.

Thanks

---

### Post by BigDave708 on 2006-07-22
> **mrbrdo said:**
> Hello

I have an USB soundcard and an integrated soundcard in my notebook. When i have the USB soundcard plugged in, i want it to use that one, and when it's not, i want it to use the integrated one. Any way to do this (or using a switch script)? Currently if i have the USB soundcard plugged in at boot, it usually uses it (but not always - no idea why), but i don't know how to switch to it when i plug it in after boot.

Thanks

On-board sound can usually be disabled in BIOS. Plugging in the USB sound card after Ubuntu has booted probably won't work because a device like that usually isn't hot-swappable.

---

### Post by erikpiper on 2006-07-22
Go to system > preferences > sound. Change the default sound card. Should work instantly.

---

