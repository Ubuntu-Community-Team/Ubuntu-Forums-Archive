---
title: "Nexuiz: Dual Monitors. Unwanted Stretching to both."
date: 2012-02-15
forum: Gaming &amp; Leisure
---

### Post by mthomps on 2012-02-15
I am running Ubuntu 11.04 with xfce. Video card is nvidia gtx 260. Video mode is twinview. 

I launch Nexuiz through terminal and the game loads in full screen spanning both monitors. I would like to run the game full screen on one monitor keeping the other free for flash video. When I uncheck full screen in the gui in an attempt to resize the slider for resolution, it cannot be changed.

There is not much info in the man page. I have tried this command:

```
nexuiz +set vid_width 800 +set vid_height 600
```

and the game still spans both monitors, only decreasing the size of the game and leaving a large black space still spanning both screens.

---

### Post by mthomps on 2012-02-20
One bump in hopes that someone has any suggestions.

---

### Post by Pierrick584 on 2012-02-20
Sorry that i cant help much, but from my experience with nexuiz with 3 screen, the game open on one screen, but i have no mouse, i have to navigate though options with keyboard, no options fix it, if i get in game, the mouse is over sensitive (like i barely touch it and it make about a 1080 degree turn...)

---

### Post by HolgerB on 2012-02-22
From:
[https://wiki.archlinux.org/index.php/Nvidia](https://wiki.archlinux.org/index.php/Nvidia)

> 
** Gaming using Twinview**

 In case you want to play fullscreen games when using Twinview, you  will notice that games recognize the two screens as being one big  screen. While this is technically correct (the virtual X screen really  is the size of your screens combined), you probably do not want to play  on both screens at the same time.  
To correct this behavior for SDL, try: 
 export SDL_VIDEO_FULLSCREEN_HEAD=1  For OpenGL, add the appropiate Metamodes to your xorg.conf in section [COLOR=#222][FONT=monospace]Device[/FONT][/COLOR] and restart X: 
 Option "Metamodes" "1680x1050,1680x1050; 1280x1024,1280x1024; 1680x1050,NULL;  1280x1024,NULL;"  Another method that may either work alone or in conjunction with those mentioned above is [starting games in a separate X server]("https://wiki.archlinux.org/index.php/Gaming#Starting_games_in_a_separate_X_server"). 



---

### Post by alhera on 2012-02-23
To play games in full screen in twinview you can search to google for getting proper solution to this. Hopefully you'll get some good suggetions from search results.

---

### Post by HolgerB on 2012-02-23
If young padawan looks at my previous post, the solution should come to his mind :)

If one uses the search egine of his choice on the topic of dual-head gaming combined with Nvidia, he/she will find several results suggesting the same approach as I posted above as except from the archwiki.

Other possible solutions are deactivating one screen during gaming using xrandr or simply starting the game in a second xserver with a xorg.conf which has only one monitor configured.

IIRC NVidia even had a specific page covering this topic and showing examples with meta-modes. I run dual-head with a NVidia 9800GT and can post my xorg.conf if requested.

---

