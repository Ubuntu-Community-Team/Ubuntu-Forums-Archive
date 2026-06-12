---
title: "Emerald Themer not applying themes"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by lhuser on 2007-05-21
Here's the new dilema: I run Ubuntu 7.04 and I got Emerald themes and theme manager to work. Now, all the nice themes aren't applying. There's no apply button anywhere and no matter how many clicks I do, it doesn't apply.

Did I miss something?

---

### Post by lhuser on 2007-05-21
If that helps, I'd tried loading the desktop effects, and that was a real no-no. The screen losts its borders, then went completely white. It was automatically reverted.

Does Emerald Theme manager require Desktop effects?

---

### Post by TimTheEnchanter on 2007-05-21
What worked for me was right-clicking the red diamond, then "Reload Window Decorator" or something to that effect.

---

### Post by Gus_T_Reer on 2007-05-21
That worked for me too. Select your theme and with the window still open reload window decorator.

---

### Post by lhuser on 2007-05-21
You're going to laugh, but how do I reload the window decorator?

Looking at it, I need to have ared Diamond on the taskbar. I don't. I use an onboard shared 8MB GPU.
EDIT: Oh crap. Beryl screwed up my login sttartup. Now, I need to remove it.

---

### Post by Ub1476 on 2007-05-21
Nono. you don't need to have beryl in the panel to get it to work with the themes:p Just do this: Right click on panel, add to panel. In utilities: add "run application..".

Now click on the "run application.." (a wheel or something) icon on your panel and write:

```
emerald --replace
```

That should reload emerald, and your new theme will be applied:)

If Beryl screws up your desktop here's code to uninstall:

```
sudo aptitude remove xserver-xgl beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
```

NOTE: That uninstall XGL too. Just remove xserver-xgl if you dont want to do that;)

---

### Post by lhuser on 2007-05-21
I have tried emerald --replace, but what it did is nothing else but just sitting there. I'll reinstal Beryl, and I personally don't feel like XGL. An onboard 8MB isn't the best for it.

---

### Post by lhuser on 2007-05-21
Nope. Running the command makes it just to sit there, as if nothing happened. I did remove beryl-manager, but it seems that I have the Beryl settings now. I'll try reinstalling beryl-manager now.

UPDATE: Beryl manager still doesn't work, even though it's in the menu now.

This is what it does:

I click on Beryl manager. It logs me out and runs in terminal. It then brings me to the login window. I log in. It did nothing. It's like as if it crashed. Does Emeral require a 3D GPU or something higher than 8MB to run?

Maybe my SIS drivers aren't set correctly.

---

### Post by lhuser on 2007-05-21
Wee bit more update. I have look in System monitor. This is what I find:

Emerald is sleeping. Nothing is working.

In terminal, when I type for fun, emerald --reload, this is what it give me:
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"


I'm getting closer. Is it a problem with my drivers?

---

### Post by lhuser on 2007-05-21
Okay, I have found my problem. When I opened Cedega, it did the same thing as Beryl Manager.

My card is for a first, too low in RAM, and is not 3D. Not suprising to me.

I don't think I can put a better card other than an FX 5500.

---

### Post by BatsotO on 2007-05-24
have you set the window decorator to standard beryl decorator (emerald)?

---

