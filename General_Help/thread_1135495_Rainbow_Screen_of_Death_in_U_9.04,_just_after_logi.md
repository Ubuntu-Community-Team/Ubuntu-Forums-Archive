---
title: "Rainbow Screen of Death in U 9.04, just after login"
date: 2009-04-24
forum: General Help
---

### Post by theresonant on 2009-04-24
Hey all.
I've just upgraded from 8.10 to 9.04, and after everything finished, I waited for the restart. After that, I typed in my password and waited to see the desktop. Soon after that, I got a screen with lots of coloured lines and the mouse cursor. After a second, it brings me back to the login screen (X crash?).

I cannot login to a GNOME session, not even a failsafe one. I can only blame Compiz, because right now I'm in an Enlightenment 16 desktop on my laptop and things work. Luckily I kept E16... Anyway, I opened the Appearance settings for GNOME and disabled all visual effects. After that I rebooted, hoping to get a plain GNOME + Metacity desktop, but it got to the same screen. I also tried with three kernel images (I have more than one, I pick them at boot with GRUB), and this error happens too with the kernel that Intrepid installed. It's probably because the video drivers aren't good for my laptop in Jaunty. Still, why isn't Metacity starting normally? Or is there another way to disable Compiz? Well, except removing it...

My laptop is a HP 530, with an Intel 945GM Express. I can work with E16, but I'm not very used to it and I'll have to learn a new desktop environment if I'd be stuck with it. It's okay, but I don't have the time just now... :P

Any help, pls?

P.S.: Did a "sudo dexconf" to clean up xorg.conf, but no change.

---

### Post by theresonant on 2009-04-24
Great... Now I discovered that sound doesn't work either. I am still in E16, does this have anything to do with loading drivers? Apparently, neither video drivers nor audio ones are being loaded, or devices recognized. This isn't good.

---

### Post by BramWillemsen on 2009-04-24
i had the same problem. bars with different colours and a mouse cursor that moved and looked normally. The desktop didnt load. I did control + alt + delete and clicked the restart option. It didn't happen again. Guess it's some kind of bug but i am not sure what triggered it since i just booted normally.

---

### Post by theresonant on 2009-04-24
Hey... thanks for replying.

Unfortunately, my error is kinda worse, the mouse freezes and then I'm suddenly taken back to the login screen. Can't load anything else but E16. 

I also tried to remove xserver-xorg-video-intel, my video driver. I could enter GNOME this way (in Metacity obviously), but resolution is crap. Can I just get an older Intel driver? 

Otherwise, dunno... Can I revert to Intrepid?

---

### Post by BramWillemsen on 2009-04-24
its sad to hear a reboot won't fix your problem. I'm not really a technical user yet so i'm afraid i can't help you further than giving you this bump.

---

### Post by theresonant on 2009-04-24
Anyway, fixed it *somehow*.

I left the current version of the video driver as it is, and uninstalled Compiz. I've also set Metacity to be the default windows manager. It doesn't crash anymore. 

At least I got back to my normal desktop and work again. I really miss the effects, I customised them quite a lot.

Just in case somebody is wondering, it took me some time to find out, this is how to set your default window manager in Ubuntu:

sudo update-alternatives --config x-window-manager

It will give you some options, from 1 to N, listing your available window managers, you just pick one and you're good to go :)

---

