---
title: "GTA install"
date: 2012-11-29
forum: Gaming &amp; Leisure
---

### Post by Beardedturtle on 2012-11-29
GTA San Andreas downloaded from steam and installed and now it is a black screen with white rectangles for menus and the mouse pointer is a white square. >_> any tips here ?

---

### Post by Dlambert on 2012-11-29
> You have to hit "Enter" to start the game.  

> **[SIZE=4]GTA refuses to open[/SIZE]**            [COLOR=#3c3c3c]Some times gta may fail to start even when you haven't touched (modded) anything. In this case delete the file **gta_sa.set** inside  the **Documents/GTA San Andreas User Files** directory and restart the app. You will have to reset your gta sa settings.[/COLOR]
       
      **[SIZE=4]CJ and peds are too dark[/SIZE]**
            [COLOR=#3c3c3c]If cj isn't light correctly and appears very dark try disabling glsl. You can disable it using the registry key: **HKEY_CURRENT_USER\Software\Wine\Direct3D\UseGLSL [B]>** "disabled"[/B] Or use winetricks/playonlinux[/COLOR]
       
**[SIZE=4]Slow Play[/SIZE]**            [COLOR=#3c3c3c]If you have problems with slow play, go to your winecfg and disable support for Vertex Shader and Pixel Shader[/COLOR]
       
**[SIZE=4]Controllers & Keyboards              [/SIZE]** 
            [COLOR=#3c3c3c]Joysticks and joypads will create a  conflict with the keyboard keys making the character (CJ)  uncontrollable. Disable all controllers before running the game to avoid  this issue.                    [/COLOR]
       
**[SIZE=4]Load a saved game not work[/SIZE]**            [COLOR=#3c3c3c]Try this: **winetricks d3dx9**[/COLOR]
       
**[SIZE=4]Intro videos not work[/SIZE]**            [COLOR=#3c3c3c]In some cases this fix can backfire, doing that your game does not start anymore.Make a backup of your **.****wine** folder or create new wineprefix for test before continuing. 
 [/COLOR]
      [COLOR=#3c3c3c]1) Install the ugly plugins for gstreamer (the name of package depends of your distribuition)
2) Install the quartz and devenum: **winetricks**** quartz**** devenum** 
3) Install ffdshow:** winetricks ****ffdshow** (during installation, check the box of MPEG1 and MPEG2) 
4) Test your game.[/COLOR]
      [COLOR=#3c3c3c]If you can not start your game[/COLOR][COLOR=#3c3c3c], restore the[/COLOR][COLOR=#3c3c3c] backup or back to original wineprefix[/COLOR]. [COLOR=#a5a5a5]#[/COLOR] [9127]("http://bugs.winehq.org/show_bug.cgi?id=9127")
       
**[SIZE=4]Fonts Issue[/SIZE]**            [COLOR=#3c3c3c]If you have issues with fonts, try (type in the terminal): [/COLOR]**winetricks allfonts**[COLOR=#3c3c3c][/COLOR] 

Try these. More system specs? Wine version?

---

### Post by Beardedturtle on 2012-11-29
> **Dlambert said:**
> Try these. More system specs? Wine version?

Wine version 1.4 set to Vista compat. the game loads but there is no graphics or text just squares and rectangles. same with xp compat mode.

---

