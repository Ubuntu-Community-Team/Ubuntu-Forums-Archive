---
title: "Gnome freezing after login"
date: 2006-03-01
forum: Desktop Environments
---

### Post by eku on 2006-03-01
This thing popped up to existence today. I think.

At first, every gnome based program freezed, like Terminal etc. Opera, Konsole, and other non Gnome dependent programs worked well. No problem there.
So, I tought "maybe restarting X would help", and pressed ctrl + alt + backspace. Everythings working right to the moment after logging in. Or something.
I can give my login name and password, but after that it freezes. Only brown screen with working mouse cursor shows. And after about an hour, I got desktop's background image showing up. But not anything else. I can start programs using shortcut keys, but they're all freezed.

I installed Fluxbox and started it (by choosing it from the sessions), and it got up and running after several minutes, and it worked just fine. But it took abnormally long to load. Even longer than Gnome did, when it worked.

I don't remember what programs I've installed before I noticed this to happen. But, I installed quite a lot of 'em.

'Top' doesn't show any peaks or anything in cpu/mem usage.

Machine's spex:
Pentium3@520Mhz
128Mt sdram
NVIDIA's TNT2 gpu
Something else you need to know?

---

### Post by Ramses de Norre on 2006-03-01
The shell works? Then I guess it's a videocard driver issue.
Can you log into gnome with the driver set to vesa? 
To do so: 
```
ctrl+alt+F1
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo vi /etc/X11/xorg.conf
search the device section of your video card, press i, change the driver to vesa, press ESC, press shift+q, type wq!
ctrl+alt+F7
ctrl+alt+backspace
```

---

### Post by eku on 2006-03-02
Ok, got everything working after rebooting the whole system. So could it have been caused by some gnome program or something?

Shouldn't they close when X is shutted down?

---

