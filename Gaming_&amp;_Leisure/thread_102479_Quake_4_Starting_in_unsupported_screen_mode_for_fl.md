---
title: "Quake 4: Starting in unsupported screen mode for flat panel (85Hz)"
date: 2005-12-12
forum: Gaming &amp; Leisure
---

### Post by tentimes on 2005-12-12
Hi,

I have setup X and screen modes are restricted to 1280x1024@75 Hz. Quake 4 is trying to start in some weird mode at 85Hz. I can find no config file for it in its local folders. MY LG FLatron 1717S only supports 1280x1024@75Hz I think. In any case I am happy for it to run at 60. Trouble is I can find no way of getting Quake 4 to start in anything but this (obviously CRT) funny timing, which is knocking my flatpanel out. I have used the howto guide and edited the refresh rates to reflect the panels abilities, but quake 4 (or openGL? not sure hwo this all works) is trying to startup in a resolution with 43.5somethingx85Hz. Obviusly being a flat panel 85Hz is too much.

I am new to Ubuntu - is this something to do with openGL? I am running the standard nvidia driver that comes with breezy, and can find no way of selecting the available opengl modes etc.

Been reading through forums these past couple of days but can't seem to get anything relevent :(

Thanks for any help you can give - sorry if I have missed something, but I am searching and reading as best I can through all that is already here. It's day 3 of my first ever go at Linux! :)

EDIT: SHould have put, NVidia driver seems fine and gears are running at about 4000 on average.

*** IMPORTANT: This is the Linux version! I'm not trying to run a windows version through WineX or something silly like that ***

---

### Post by tentimes on 2005-12-14
*bump* relly hoping I can get some help - thanks :)

---

### Post by tentimes on 2005-12-17
Was reading this again, tripped over and got a *bump* on my head...

---

### Post by drn8 on 2006-01-10
Man I have the same thing here, It is a massive pain, it seeems a "+set" startup command might be the answer, I have yet to find a list of such commands.


*edit*

I'm totally using opensuse 10.0 right now, but this is not really a distro issue.

---

### Post by drn8 on 2006-01-10
This worked for me:

```
quake4 +set r_mode 5 +set r_displayRefresh 60
```

I got the info from [http://www.tweakguides.com/Quake4_7.html](http://www.tweakguides.com/Quake4_7.html) and [http://www.tweakguides.com/Quake4_8.html](http://www.tweakguides.com/Quake4_8.html) aparently by using the "+set" prefix(or whatever) you can set the cvars at startup like my example.

> r_mode [-1,3,4,5,6,7,8] - This setting determines the resolution, as set in the in-game menus under Screen Size (See In-Game Settings section). The mode values are -1 = Custom (see r_customheight, r_customwidth commands), 3 = 640x480, 4 = 800x600, 5 = 1024x768, 6 = 1152x864, 7 =1280x1024 and 8 = 1600x1200. 

Looks like you want r_mode 7 for your setup. now I just need to fix the glitchy sound and graphics:

[[IMG]http://img242.imageshack.us/img242/5027/quake4messedscreen8wy.th.png[/IMG]](http://img242.imageshack.us/img242/5027/quake4messedscreen8wy.png)
(*middle* click on image for full size)

Freaking messed up.

---

