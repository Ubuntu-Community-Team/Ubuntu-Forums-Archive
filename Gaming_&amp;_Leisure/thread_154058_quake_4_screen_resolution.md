---
title: "quake 4 screen resolution"
date: 2006-04-02
forum: Gaming &amp; Leisure
---

### Post by Simian on 2006-04-02
I have just installed quake 4 and was really enjoying it. Then I foolishly set the screen resolution too high. Then the nest time i tried to load it it said, "Sys_Error: SDL_SetVideoMode failed: No video mode large enough for 1280x1024"

Please tell me that there is a way to launch quake 4 with 800x600

I would be eternally grateful if someone could help...:-D

---

### Post by Simian on 2006-04-02
it's ok i found the answer here:
 [http://www.ubuntuforums.org/showthread.php?t=102479&highlight=quake+resolution]("http://www.ubuntuforums.org/showthread.php?t=102479&highlight=quake+resolution")

thanks to drn8
> 
This worked for me:
 
 
Code:
```
quake4 +set r_mode 5 +set r_displayRefresh 60
```

 I got the info from [http://www.tweakguides.com/Quake4_7.html](http://www.tweakguides.com/Quake4_7.html) and [http://www.tweakguides.com/Quake4_8.html](http://www.tweakguides.com/Quake4_8.html) aparently by using the "+set" prefix(or whatever) you can set the cvars at startup like my example.
 
 
Quote:
 r_mode [-1,3,4,5,6,7,8] - This setting determines the resolution, as set in the in-game menus under Screen Size (See In-Game Settings section). The mode values are -1 = Custom (see r_customheight, r_customwidth commands), 3 = 640x480, 4 = 800x600, 5 = 1024x768, 6 = 1152x864, 7 =1280x1024 and 8 = 1600x1200.

---

