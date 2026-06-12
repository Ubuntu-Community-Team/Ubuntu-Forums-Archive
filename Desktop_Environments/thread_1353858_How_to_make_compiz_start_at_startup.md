---
title: "How to make compiz start at startup"
date: 2009-12-13
forum: Desktop Environments
---

### Post by themoodude on 2009-12-13
Hi,

I've installed compizconfig settings manager; and applied several effects to my liking, however each time i start Ubuntu- metacity seems to run things. I can get compiz going with compiz --replace, but is there a way to have compiz running from login? On a previous install of ubuntu it seemed to take control automatically, but this time it hasn't.

Any help would be great,
Cheers,
Dean

---

### Post by rafalcieslak on 2009-12-13
Try rigth-clicking on desktop, choose 'Change background', in 'effects' tab choose maximum level of effects (you will loose your effects configuration though). 
Or in 'gnome-session-properties' application add an entry for compiz (however I am unsure if it won't affect the boot time, I don't know if it won't load metacity and THEN compiz)

---

### Post by stinkeye on 2009-12-13
If your using fusion-icon in startup applications change the command to
```
fusion-icon -n
```
Fusion-icon will try to load compiz and can cause problems.
The -n option will load fusion-icon without loading a window manager.

---

### Post by haribol707 on 2009-12-13
I have 9.04 / GNOME on my laptop (GE Force 8400M) and desktop (Quadro FX 500/ 600) systems. On both the systems I installed Nvidia proprietary drivers from the Hardware Drivers application (basically Ubuntu recommended versions). Here is the interesting thing with Compiz on both

1. Laptop: No problems. First time I enabled Extra Visual Effects from System->Preferences->Appearances -> Visual Effects, the settings took effect and I was able to play around with Compiz (ccsm) and it would start automatically on login/restart. 

2. Desktop: I had problems similar to yours. I can force start Compiz with "compiz --replace", however, it does not start on system reboot. Neither am I able to enable Visual Effects from Appearance menu. I thought the problem might be with the gfx driver and tried using latest one available from nvidia.com. No luck. Then, I added 'compiz --replace' to startup script. But, everytime it loads with default settings. Your previous compiz custom settings wont be loaded. How useful is tht? Finally, I installed fusion-icon and I am able to start/stop compiz WM through that. You can add fusion-icon to startup with "<PATH>/python <PATH>/fusion-icon --no-start". Compiz starting problem or no problem I would recommend fusion-icon anyways. You can switch b/w different WM using this tool. <Cool!!> It is still not the end of my problems though ;) Even with fusion-icon, I need to start compiz twice for it to load and work properly. First time I select it, the system fails with an error dialog (cant recollect wht it said". And, another advantage I forgot to mention, with fusion-icon, you dont have to worry about lost settings :) (which also points to some missing option/something when I manually start compiz with compiz --replace). 

My 2c, install fusion-icon, put it on startup applications list and :popcorn:

I am curious to know which gfx card you have.

---

### Post by haribol707 on 2009-12-14
I just found a related thread which was last updated yesterday and someone seems to have a working solution for the problem. Do check it out if you already havent. I plan on testing it sometime tomorrow.

---

### Post by themoodude on 2009-12-14
Thanks for the replies guys, very much appreciate them. I've ended up at first just adding compiz --replace to startup, but now I've installed both emerald and the compiz-fusion tray icon, so I'm loading compiz with fusion-icon at startup, and playing around with emerald themes as and when.

Thanks again for your help!

---

