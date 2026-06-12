---
title: "Two related questions: Wallpaper-tray problems and compiz-fusion questions"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by Yoshiman007 on 2007-12-02
Hello, I am a maturing user of Ubuntu with 5 or so stable installs under my belt and I come here with two questions. The first is specific to my laptops configuration and wallpaper-tray.

   I've had this problem for about a month now, with no solution in sight. On random session starts, my wallpaper-tray icon, usually a tiny thumbnail of my current wall which i can click or right click for options. This icon appears to have disappeared, but in fact, the space where it used to be is empty and one pixel in the top left area of where the thumbnail used to be remains. The color of this pixel seems to be determined by the overall color of the wallpaper that is up. However, clicking on this pixel does nothing and i can no longer switch my wallpaper whenever i want to. The following attached picture shows my problem.

   The second question I have is about Compiz-Fusion and having different wallpapers on each side. I have seen quite a few threads about this with no particular solution stated. I am aware that i have to give up my desktop icons for some of these fixes, and that's fine by me. My real problem is weather i can configure wallpaper-tray to change all of the walls on the cube or one at a time, or in any combination. My ideal situation is having a different wallpaper on each side of the cube and have the ability to have all of them change randomly, possibly just on command or at an interval.

Thanks in advance for any help on either front ! :) Sorry for the long explanation...

---

### Post by lmellor on 2007-12-04
I'm not sure if this will help with the multiple desktop scenario as I only use one (I have 2 configured but I've nto found a use for number 2 as of yet).  I had a play with wallpaper tray for a while and eventually ditched it in favour of desktop drapes (do a synaptic search for drapes), this app will change the wallpaper for you over a set period of time (kinda like how macosx does), it may be possible to push it further but I can't really be of any more help than that.

Hope this gets you at least some of the way there, I've recently had a headache solved on these forums and so I'm just trying to give a little back (this is a community after all).

---

### Post by Rinzwind on 2007-12-04
> **Yoshiman007 said:**
> <..>
   The second question I have is about Compiz-Fusion and having different wallpapers on each side. I have seen quite a few threads about this with no particular solution stated. I am aware that i have to give up my desktop icons for some of these fixes, and that's fine by me. My real problem is weather i can configure wallpaper-tray to change all of the walls on the cube or one at a time, or in any combination. My ideal situation is having a different wallpaper on each side of the cube and have the ability to have all of them change randomly, possibly just on command or at an interval.

Thanks in advance for any help on either front ! :) Sorry for the long explanation...

This is the command needed to change the 4 images on the cube:
- 1st you need to disable nautilus desktop:

gconftool-2 --type bool --list-type=bool --set /apps/nautilus/preferences/show_desktop false

- This string changes the desktop wallpapers to 4 different images and thus also the cube:

gconftool-2 --type list --list-type=string --set /apps/compiz/plugins/cube/screen0/options/backgrounds [/files/Pictures/xxxHolic_01.jpg,/files/Pictures/xxxHolic_02.jpg,/files/Pictures/xxxHolic_03.jpg,/files/Pictures/xxxHolic_04.jpg]

change  /files/Pictures/xxxHolic_01.jpg and so on to whatever you need.

---

