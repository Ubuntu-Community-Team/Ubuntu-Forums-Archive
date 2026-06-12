---
title: "How to install 'Show Desktop' plugin for 11.04?"
date: 2011-07-22
forum: Desktop Environments
---

### Post by Cobuntu on 2011-07-22
I have a Fujitsu T730 and I just love 11.04 with Unity. One of the two things missing so far is a 'Show Desktop' button that works (there is a crude workaround I tried and dismissed: [http://askubuntu.com/questions/29969/is-there-a-unity-equivalent-of-the-gnome-panel-show-desktop-applet](http://askubuntu.com/questions/29969/is-there-a-unity-equivalent-of-the-gnome-panel-show-desktop-applet)). 
If I understood correctly there is a Compiz plug-in under development here: [https://launchpad.net/compiz-showdesktop-plugin](https://launchpad.net/compiz-showdesktop-plugin)
Can anyone tell me how to install that?

---

### Post by Prabh_Chandhar on 2011-07-26
Simple sir.. install docky.
sudo apt-get install docky.
after installing in its preferences you can add an applet called show desktop.. Its the simplest way!! :popcorn:

---

### Post by walt.smith1960 on 2011-07-26
I installed 'gnome-panel' using Synaptic and added it to startup.  You can run 'gnome-panel' from terminal to try it. ' Show desktop' icon is in the lower left corner and I can install panel applets if i choose.  One of my big complaints about Unity was the inability to quickly and easily switch between windows and applications.  Gnome-panel fixes that for me.

---

### Post by mc4man on 2011-07-26
> **Cobuntu said:**
>  
If I understood correctly there is a Compiz plug-in under development here: [https://launchpad.net/compiz-showdesktop-plugin](https://launchpad.net/compiz-showdesktop-plugin)
Can anyone tell me how to install that?

Gave it a little try on 11.10, should be the same on natty
It takes the place of super+d but instead of min all it moves the windows in directions

Some of the directions do impact the unity launcher and panel
The down has this interesting though probably unintended effect of a ghostly window list, where the windows can be partially interacted on

Some of the window bars   can be clicked on, -   the close,min,restore buttons are active - only the close will produce what you want.

The build is easy, don't know the build deps they were already installed (cmake, this wouldn't hurt
 sudo apt-get build-dep compiz-plugins-main

Then download the tar archive from link, extract and open it up. 
Inside there is a CMakeLists.txt, open it.
Paste this line in a the very top, save
```
cmake_minimum_required(VERSION 2.8)

```
Ex.
> cmake_minimum_required(VERSION 2.8)
find_package (Compiz REQUIRED)

include (CompizPlugin)

compiz_plugin (showdesktop PLUGINDEPS composite opengl)



Then create a folder right there named build and cd to it in a terminal - 
```
 cmake ..
```
If it configures successfully follow with this or use checkinstall instead of the 'make install' if desired
```
make && sudo make install
```

To uninstall from the make install don't alter or remove your source folder, when or if, - cd to source folder and  run  - 
```
sudo make uninstall
```

At what state the dev is, where it's headed if anywhere and if it has any side effects don;t know..

---

### Post by Cobuntu on 2011-09-02
Thanx guys, also I am afraid I am still stuck with my problem.
@[Prabh_Chandhar]("http://ubuntuforums.org/member.php?u=1130308"): works perfectly, but I do not wanna have an aditional panel and Docky is not a good enough over all replacement for me. At least this is how I felt after trying it for several days.
@walt.smith1960: I tried this in 11.10 but it did not work there. I will try it again with a later or final 11.10 release.
@mc4man: When I read your post I realized that this was already installed. You can access it via Ubuntu Tweak/Desktop/Compiz Settings. Damn, I hopped this was a totally different plugin that provides a button. It does work fine but I cannot trigger this in tablet mode.

---

