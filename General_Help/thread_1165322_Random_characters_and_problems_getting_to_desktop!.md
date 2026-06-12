---
title: "Random characters and problems getting to desktop!"
date: 2009-05-20
forum: General Help
---

### Post by wallyxwest on 2009-05-20
Hi everybody,

So after a good bit of time and work I had my laptop running Ubuntu dual-boot with XP and had everything set up just right. Then one day I turn on the computer and this happens:

[IMG]http://i84.photobucket.com/albums/k18/WallyxWest/IMG_0653.jpg[/IMG]

[IMG]http://i84.photobucket.com/albums/k18/WallyxWest/IMG_0652.jpg[/IMG]

[IMG]http://i84.photobucket.com/albums/k18/WallyxWest/IMG_0651.jpg[/IMG]

[IMG]http://i84.photobucket.com/albums/k18/WallyxWest/IMG_0650.jpg[/IMG]

[IMG]http://i84.photobucket.com/albums/k18/WallyxWest/IMG_0649.jpg[/IMG]

[IMG]http://i84.photobucket.com/albums/k18/WallyxWest/IMG_0648.jpg[/IMG]

I did some googling and it sounded like some other people had similar problems and it cleared up for them after cleaning their fans and such (especially the gpu fan). So I took the entire thing apart and with some compressed air and tweezers cleaned the crap out of it (literally!). Put everything back together and it's no different. Not sure if it's the graphics card though because that Ubuntu loading screen comes up just fine (same thing for windows but I didn't want to bring that around these parts). After that screen though it just black. No desktop, no user sign in, no nothin'.

If anyone has any ideas on why this is happening and what I might be able to do to fix it I am all ears. This is a Dell Inspiron 9300 with a nVidia GeForce Go 6800. I am not super computer savvy (and am a total ubuntu noob) but I am good at following directions and am for the most part not a total idiot :D.

Thanks in advance!

---

### Post by gettinoriginal on 2009-05-20
During grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

I am only guessing, as I have never seen that problem, but it won't hurt anything either  ;)

---

### Post by wallyxwest on 2009-05-21
> **gettinoriginal said:**
> During grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

I am only guessing, as I have never seen that problem, but it won't hurt anything either  ;)

Thanks for the response! I will try that this weekend and tell you how it goes. *crosses fingers*

---

### Post by wallyxwest on 2009-06-03
So I tried what you said and I was able to finally boot into Ubuntu. Problem is it keeps freezing. On top of that I still can't boot into windows. I tried using a live CD (I had xubuntu ibex handy) and it got to the desktop and froze as well. Either way though I don't think it's the graphics card because the desktop environments both looked just fine. It's only during the initial start-up that the screens are funky.

I feel it could be the BIOS but it doesn't seem like anyone else has run into this problem with their dell inspiron 9300 ever... I might try going to the dell website and figuring out how to flash the BIOS and see what happens.

---

