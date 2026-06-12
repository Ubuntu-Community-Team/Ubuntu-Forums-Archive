---
title: "Minecraft full screen not working!"
date: 2015-04-12
forum: Gaming &amp; Leisure
---

### Post by Eyeballs on 2015-04-12
I have a Toshiba 32 bit laptop running Ubuntu 14.04 LTS.
I had minecraft running, and it was working fine. I then went into the minecraft settings in-game and went Settings > Video Settings > Full Screen. I then pressed on. Minecraft then ran, but fullscreen and invisible. Nothing else I had running worked, including Chromium and Files. I had to press and hold the off button, because nothing was responding. Now whenever I run minecraft, I see the launcher, and press play. I then see the launcher close. Then, I see the Mojang screen. After that, minecraft becomes invisible, but sounds still work. I want to find out how to turn full screen off.[RIGHT]
Thanks! From Eyeballs!
[/RIGHT]

---

### Post by R33D3M33R on 2015-04-12
In your home folder there is a hidden folder called minecraft. You can access it by typing:

```
~/.minecraft/
```

in your file manager or access it from minecraft launcher. In this folder there is a file called **options.txt**. Open it with text editor, find the line:

```
fullscreen:true
```

and change it to:

```
fullscreen:false
```

---

