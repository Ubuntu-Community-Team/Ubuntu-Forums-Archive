---
title: "how to beryl on ati 9700pro Feisty?"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by Gargamella on 2007-04-25
I installed beryl, beryl-manager, emerald, emerald manager and I followed also this how to:

[http://www.thebags.it/linux-pages/berylxgl-su-ubuntu-edgy-eft-con-ati-card/](http://www.thebags.it/linux-pages/berylxgl-su-ubuntu-edgy-eft-con-ati-card/)


but this seems not to work and leaves me with metacity...

I used to follow this other howto, but link seems broken:

[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)


any ideas?

---

### Post by ovidiub on 2007-04-25
> **Gargamella said:**
> I installed beryl, beryl-manager, emerald, emerald manager and I followed also this how to:

[http://www.thebags.it/linux-pages/berylxgl-su-ubuntu-edgy-eft-con-ati-card/](http://www.thebags.it/linux-pages/berylxgl-su-ubuntu-edgy-eft-con-ati-card/)


but this seems not to work and leaves me with metacity...

I used to follow this other howto, but link seems broken:

[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)


any ideas?

Try this one [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)
Worked for me.

---

### Post by Gargamella on 2007-04-26
now the broken link works, but i'll try the how-to you passed me...thank you for replying...anyway can you tell me if you have the same video card?

I need to know if that is possible with ati radeon 9700 r300 pro

---

### Post by wingedpig on 2007-04-26
Those are instructions for Edgy. Fiesty makes installing Beryl MUCH easier. I had it working perfectly on my laptop w/ M Radeon9700 about 5 minutes after installing Ubuntu from disc.

From a fresh install I just:
```
sudo apt-get update
sudo apt-get install beryl beryl-manager emerald emerald-themes
```

Then just launch Beryl manager from the System Tools menu and make sure it's turned on the right window manager.

So far, it only breaks if I install the restricted Ati drivers, which I assume needs some degree of manual configuration before it can be activated (which I won't bother with atm since OGL games run fine under the default drivers). This is where I think you went wrong in following your linked instructions. If you just leave on the default ati drivers instead of getting fglrx first, I'm sure Beryl will work as I've described.

Then you can back up xorg.conf and keep experimenting with getting fglrx working.

EDIT: Ok, here's what I figured out: Beryl is failing on your system because you're using AIGLX (you can check by typing "beryl" in terminal) and fglrx which doesn't support compositing. So if you're running AIGLX, you'll need to use the default open-source radeon drivers, whereas if you use fglrx, you need to install and run XGL.

---

