---
title: "Beryl not working on Feisty, after installing nvidia driver"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by Loman on 2007-05-22
I am kind of a noob, so forgive me if I sound stupid :)

I just got Feisty, and it's great. I installed it yesterday, and I used the restricted driver manager to get my graphics card working, then I installed beryl and it worked great.

 Then I tried to install the beta nvidia drivers (I disabled the restricted driver first), but it messed up my system so that X would not start. I am a noob, so just reinstalled ubuntu completely.

So then, I installed the beta driver first (it did the same thing as before, but I fixed it eventually), then I installed beryl. The Beryl icon is in the system tray, and I can open the settings manager, and the emerald theme manager, but the theme doesn't change. 

On the "Select Window Manager" menu when I right-click the beryl icon, it is set to "Metacity", and I can change it to "Compiz", but not to "Beryl". When I pick Beryl, the open windows flicker, then go back to normal, and the window manager is set back to metacity.

Does anyone know how I can get Beryl Working again?

My Specs:
3.33Ghz Celeron D
1.5GB RAM
Gigabyte 8I865G Motherboard
nVidia Geforce 7600GT

EDIT:
I finally got Beryl to work again. I just had to edit my xorg.conf to enable the composite option

```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

