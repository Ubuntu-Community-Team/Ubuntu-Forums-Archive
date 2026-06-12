---
title: "Assigning each workspace a separate wallpaper?"
date: 2010-12-24
forum: Desktop Environments
---

### Post by sirspazzolot on 2010-12-24
Is there compiz plugin or something for this? If not, maybe I'll make one when I'm a competent hacker. It seems like it could be a cool idea.

PS. Merry Christmas!

---

### Post by hhh on 2010-12-24
2 ways to do it, [Wallpapoz]("http://wallpapoz.akbarhome.com/"), which I've never used, or the Compiz wallpapers plugin (install compiz-plugins-extra), which you have to disable Nautilus drawing the desktop, which means you can't have icons on the desktop...
[http://my.opera.com/ubuntunerd1/blog/how-to-get-multiple-desktop-wallpapers-in-ubuntu-8-4-8-10](http://my.opera.com/ubuntunerd1/blog/how-to-get-multiple-desktop-wallpapers-in-ubuntu-8-4-8-10)

Here's an old screenshot of mine using Compiz Wallpapers and Expo...
[http://img713.imageshack.us/img713/8423/screenshot0831201001185.png](http://img713.imageshack.us/img713/8423/screenshot0831201001185.png)

---

### Post by stayahead on 2010-12-28
I notice a lot of people ask this question, and a solution appears not commonly known (at least from my research). You can actually do this in a standard Kubuntu 10.10 install with no 3rd party programs.

What you need to do is the following:
System Settings > Window Behaviour > Virtual Desktops > and tick the following option: "Different widgets for each desktop"

While wallpapers aren't mentioned in this option, a side effect appears to be that you can set each desktop to have a different  wallpaper from right clicking on each desktop and choosing "Desktop Settings".

---

### Post by abeam on 2011-01-27
> **stayahead said:**
> I notice a lot of people ask this question, and a solution appears not commonly known (at least from my research). You can actually do this in a standard Kubuntu 10.10 install with no 3rd party programs.

What you need to do is the following:
System Settings > Window Behaviour > Virtual Desktops > and tick the following option: "Different widgets for each desktop"

While wallpapers aren't mentioned in this option, a side effect appears to be that you can set each desktop to have a different  wallpaper from right clicking on each desktop and choosing "Desktop Settings".

Do you know how to do that in Ubuntu?

---

### Post by darnir on 2011-01-27
#1. Open CompizConfig Settings Manager [System>>Preferences>>CompizConfig Settings Manager]

#2. Now select “Wallpapers” under the “Utility” section.

#3. Under Backgrounds tab select different wallpapers of your choice for each workspaces.

#4. Now close CompizConfig Settings Manager and press Alt+f2 . Here type “gconf-editor” as in the screenshot. Go under: Apps>>Nautilus>>Preferences and uncheck the “show_desktop” option.

Additionally, press Ctrl+Alt+F1 and then Ctrl+Alt+F7, if you see the desktop not being rendered properly, like windows leaving a trail when you drag them and all.. 
I have to this on every system start..

---

### Post by steveneddy on 2011-01-28
When I work I like to use the desktop space as a work area to store files of different types until I am finished with the project then sore them away.

Not having the ability to have icons on the desktop wouldn't be worth simply having different wallpaper on each desktop.

my opinion only....

---

### Post by blocky on 2011-01-28
Is there a bug for this issue? I can't believe this feature hasn't been implemented.

---

### Post by W29 on 2011-02-15
> **darnir said:**
> #1. Open CompizConfig Settings Manager [System>>Preferences>>CompizConfig Settings Manager]

#2. Now select &#8220;Wallpapers&#8221; under the &#8220;Utility&#8221; section.

#3. Under Backgrounds tab select different wallpapers of your choice for each workspaces.

#4. Now close CompizConfig Settings Manager and press Alt+f2 . Here type &#8220;gconf-editor&#8221; as in the screenshot. Go under: Apps>>Nautilus>>Preferences and uncheck the &#8220;show_desktop&#8221; option.

Additionally, press Ctrl+Alt+F1 and then Ctrl+Alt+F7, if you see the desktop not being rendered properly, like windows leaving a trail when you drag them and all.. 
I have to this on every system start..

Doesn't work for me. There is no 'Wallpapers' under the 'Utility' section.
I had to go to 'Desktop Cube' > 'Appearance'. There, I could select the images that I want to use. But that doesn't work either.
I disabeled the 'show_desktop' in the gconf editor.

Ubuntu 10.10

Edit: Solved! I had to install the compiz-fusion-plugins-extra in the package manager. After that, the 'Wallpaper'-option appeared.
I had to restart though.
Edit: Now I have another problem. Everytime I login, the background is black. I have to ctrl+alt+F1 and ctrl+alt+F7 and then it is fine.

---

