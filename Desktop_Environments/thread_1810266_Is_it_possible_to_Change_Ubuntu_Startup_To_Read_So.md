---
title: "Is it possible to Change Ubuntu Startup To Read Something Else??"
date: 2011-07-22
forum: Desktop Environments
---

### Post by PoetGuy on 2011-07-22
Hi,

I've been customizing my desktop, trying to go from the very start to the very end :) 

At the very beginning of startup we all know it reads UBUNTU along with ubuntu's logo. The same goes for the very end of shutdown.

My question is could this be changed to read something else, example instead of "UBUNTU" to read "POETGUY" ??

Thanks in advance!

I'm on Ubuntu 10.04 LTS btw...

---

### Post by Krytarik on 2011-07-22
Therefore, you need to modify "/lib/plymouth/themes/ubuntu-logo/ubuntu_logo.png" or possibly "ubuntu_logo16.png". Of course, back them up before.

Thereafter, run:
```
sudo update-initramfs -u
```That's all!

---

### Post by PoetGuy on 2011-07-22
> **Krytarik said:**
> Therefore, you need to modify "/lib/plymouth/themes/ubuntu-logo/ubuntu_logo.png" or possibly "ubuntu_logo16.png". Of course, back them up before.

Thereafter, run:
```
sudo update-initramfs
```That's all!

Excellent! Ok Krytarik that's been a major pointer, atleast now i know it's an image and not some sort of text editing. I did find the ubuntu_logo16.png , and replaced it. I later rand sudo update-initramfs -u
but now both at shutdown and restart all I get are purple screens with no image. What could I have possibly done wrong?

---

### Post by Krytarik on 2011-07-22
Sorry for the missing option in the command, I haven't used it since a while and didn't fully look it up before.

Regarding the image not showing up, has the new image the same dimensions and permissions!?

---

### Post by PoetGuy on 2011-07-22
> **Krytarik said:**
> Sorry for the missing option in the command, I haven't used it since a while and didn't fully look it up before.

Regarding the image not showing up, has the new image the same dimensions and permissions!?



Thank You a LOT Krytarick! It was the dimensions, I had just replaced it with another. So I simply edited the original with my name on it, and viola, works like a charm! Appreciate all your time.

Cheers!

---

### Post by roshgorg on 2012-05-28
Is it possible to remove the progress bar dots, and instead replace it with a faded Ubuntu logo, colouring upto full ?

---

