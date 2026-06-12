---
title: "Kde icons?"
date: 2006-03-06
forum: Desktop Environments
---

### Post by kubuntu2k6 on 2006-03-06
How do you change the icons for the applications shown in the pager and taskbar?

Changing icontheme has no effect on these icons, so would like to know where they are located to change them manually.

The default ones (wherever they come from) doesn't look good which is kinda sad when the rest of the kde looks nice.

---

### Post by Jucato on 2006-03-06
Changes to icons will take effect on the taskbar/system tray when you restart kicker. try to type this (either in a terminal or in a Run command, Alt+F2)
```
dcop kicker kicker restart
```
That should work. If not, try to log out and log in again.

---

### Post by kubuntu2k6 on 2006-03-06
yea using that command, log in and out etc some of the icons did change.. but for some apps the "default" icons are still used... firefox, xchat etc... these icons have to exist somewhere right...

---

### Post by Jucato on 2006-03-06
Icon themes do not usually cover all available apps for linux (as that would almost be impossible if not extremely difficult to do). What happens when you change icon themes is that only those apps that have icons included in that theme would be change. For example, not all icon themes have separate icons for Firefox or for amaroK.

Just for info:
- Icons that you install as your user (exists only as far as your user is concerned) is found in /home/username/.kde/share/icons
- Icons that are installed by the system/root (present no matter what user you use) is found in /usr/share/icons
- The default KDE icon theme is called Crystal SVG. Sure it isn't that pretty. It will change, though, in KDE 4. The icon theme will become Oxygen.

Hope this helps :D

---

### Post by ComplexNumber on 2006-03-06
>  - Icons that are installed by the system/root (present no matter what user you use) is found in /usr/share/icons thats only for gnome. kde system-wide icons are found in /usr/share/apps/icons


>  - The default KDE icon theme is called Crystal SVG. Sure it isn't that pretty. the default crystal theme for kde is one of the most nauseating and offputting aspects of kde IMO. i'm rather looking forward to the new oxygen set. although its not that pretty either (too glaring for my tastes), it suits kde better.

---

### Post by Jucato on 2006-03-06
[QUOTE=ComplexNumber]thats only for gnome. kde icons are found in /usr/share/apps/icons[/QUOTE]

I am absolutely certain that my system icons are in /usr/share/icons. In fact, I don't have a /usr/share/apps/icons directory. I am also pretty sure I did nothing to change the directories in my system. :D

---

### Post by ComplexNumber on 2006-03-06
[quote=Fenyx]I am absolutely certain that my system icons are in /usr/share/icons. In fact, I don't have a /usr/share/apps/icons directory. I am also pretty sure I did nothing to change the directories in my system. :D[/quote] that seems rather odd. so do your gtk and kde icons live in the same directory then? :confused:. because if you installed gnome, thats what would happen.

---

### Post by Jucato on 2006-03-06
come to think of it... I don't know where my GTK icons are. Let me search around a bit. But their not in the /usr/share/icons directory. They don't go anywhere near my KDE icons. Btw, this is a pure Kubuntu install, not an Ubuntu+KDE install (if that matters at all).

---

### Post by dresnu on 2006-03-06
I don't have a /usr/share/apps/icons directory too. Like Fenyx said themes installed as root reside in /usr/share/icons. Don't know about gnome themes though.

---

### Post by ComplexNumber on 2006-03-06
> Btw, this is a pure Kubuntu install, not an Ubuntu+KDE install (if that matters at all). yeah, i was thinking about that. because ubuntu started off as a gnome distro, kubuntu just seems like a tweaked ubuntu. 
on almost all distros, the kde icons go in /usr/share/apps/icons(/opt/kde3/share/apps/icons on suse) to differentiate themselves from where the gnome icons are always stored (ie /usr/share/icons (or /opt/gnome/share/icons on suse)). this is because, apart from kubuntu and ubuntu, kde and gnome often live side by side and many kde and gnome themes/icons share the same name. this is something to be avoided.
so because kubuntu is intended to be a kde only distro, perhaps they go in the traditional location (ie /usr/share/icons). don't know if that makes sense. i imagine that that would cause quite a few problems if gnome and kde do live side by side on kubuntu/ubuntu for people experimenting with different DE's. maybe its something mr shuttleworth hasn't considered.

---

### Post by Jucato on 2006-03-06
Yeah, I'm searching for those GNOME icons, too. I don't have them, I think. I have a /usr/share/icons/gnome folder, but only contains OpenOffice.org icons (which is not being used, wierd...). I have GIMP installed, but the icon being used is from the theme that I'm using (Glaze). Bah! I'll just check it out tomorrow when I wake up. Need to sleep. g'night!!! (12 midnight waaay over here :D)

---

### Post by kubuntu2k6 on 2006-03-06
gave up on finding those (kde) icons.. they just don't want to be found... good thing one can turn pager/taskbar icons off.

icons are shattered all over the drive, but that would be no prob if you could choose between them... running kubuntu too, maybe for customizability im using the wrong de/wm stuff.. 

didn't like the oxygen icon preview.. but their website layout is very cool :)

---

### Post by ComplexNumber on 2006-03-06
**kubuntu2k6**
have you tried the hicolor icons? they are often a fallback for icons that aren't in crystal.

---

### Post by kubuntu2k6 on 2006-03-06
[QUOTE=ComplexNumber]**kubuntu2k6**
have you tried the hicolor icons? they are often a fallback for icons that aren't in crystal.[/QUOTE]

yep, hicolor, lowcolor, grayscale, you name it.. well.. obviosly missed something but hey you get some you lose some.. who needs em anyway... icons? where we're going, we don't need icons... :cool:

---

### Post by Jucato on 2006-03-06
btw, what specific icons are you looking for? Firefox and X-chat icons can be found in /usr/share/icons/crystalsvg. You have to remember, however, that there are different sizes of icons, depending on where they are used (16x16, 22x22, 32x32, etc). System Tray icons are 16x16 or 22x22 so you would find them in the /usr/share/icons/crystalsvg/16x16 or /usr/share/icons/crystalsvg/16x16 folder. When a specific icon theme doesn't have custom icons for some apps, the system looks into the /usr/share/icons/default.kde folder, which is just a link to the crystalsvg theme, or to any other folder that has a corresponding icon for that app (sometimes the apps come with their own icons in their own folders in /usr/share/apps)

---

### Post by ComplexNumber on 2006-03-06
[quote=Fenyx]btw, what specific icons are you looking for? Firefox and X-chat icons can be found in /usr/share/icons/crystalsvg. You have to remember, however, that there are different sizes of icons, depending on where they are used (16x16, 22x22, 32x32, etc). System Tray icons are 16x16 or 22x22 so you would find them in the /usr/share/icons/crystalsvg/16x16 or /usr/share/icons/crystalsvg/16x16 folder. When a specific icon theme doesn't have custom icons for some apps, the system looks into the /usr/share/icons/default.kde folder, which is just a link to the crystalsvg theme, or to any other folder that has a corresponding icon for that app (sometimes the apps come with their own icons in their own folders in /usr/share/apps)[/quote]
some icons are are svg's. in kde, they usually have to be buiilt using a set of png icons and a script. inkscape also needs to be installed (i guess it requires something from inkscape). svg support in kde is very bare at the moment whereas gnome has full support for them.

---

### Post by kubuntu2k6 on 2006-03-07
[QUOTE=Fenyx]btw, what specific icons are you looking for? Firefox and X-chat icons can be found in /usr/share/icons/crystalsvg. You have to remember, however, that there are different sizes of icons, depending on where they are used (16x16, 22x22, 32x32, etc). System Tray icons are 16x16 or 22x22 so you would find them in the /usr/share/icons/crystalsvg/16x16 or /usr/share/icons/crystalsvg/16x16 folder. When a specific icon theme doesn't have custom icons for some apps, the system looks into the /usr/share/icons/default.kde folder, which is just a link to the crystalsvg theme, or to any other folder that has a corresponding icon for that app (sometimes the apps come with their own icons in their own folders in /usr/share/apps)[/QUOTE]

yes.. it's true what you're saying for systray icons that if i want to change for example the adept_notifier icons they can be found in /usr/share/icons/crystalsvg/22x22/actions/ or the other one, but for the kmixdocked icons i have to go to /usr/share/apps/kmix/pics...

...but wanted to change the icons in the taskbar and the pager, so tried something like for i in 128x128 16x16 22x22 32x32 48x48 64x64;do cp /some/icon.png $i/apps/xchat.png;done in the default.kde dir.. this did change the icon in the menu which is fine, but the icons in the taskbar/pager stays the same (same for firefox.. the firefox icon in the menu is blue but the one in the taskbar is the original red and very low res, for example :) )

so figured these icons have to be located somewhere else, but never found them. being new on kde still think i've missed the obvious, but it doesn't matter really... even though i'd like to be able to customize every visual element of the desktop.

---

### Post by Jucato on 2006-03-07
Ok, I'll do a little experiment of my own and update you if I'm successful. :D

EDIT: oh crap... unsuccessful... for now. maybe I'll try again in a few days or so. It just seems weird that there are Icon themes (nuvola for example) that change icons also for the system tray and the taskbar. I'll just investigate it when I'm free. :D

---

### Post by Rovenhot on 2006-03-07
I fiddled with my settings perhaps too much and toasted many of my icons, which include some of the K Menu icons, the icons that are animated when apps are starting, and icons used by built-in apps (Konquerer back/forward buttons, e.g.).  The change happened after playing with themes.  Very confused.

Idea:  Could someone who hasn't messed with their settings too much archive (tgz, zip, whatever) their /usr/share/icons folder and send it to me (*email address removed*)?  Maybe I can restore them...

EDIT: Gah. Nevermind. I just switched computers and installed Ubuntu+Kde afresh.

---

