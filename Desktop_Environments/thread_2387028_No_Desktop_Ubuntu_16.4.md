---
title: "No Desktop Ubuntu 16.4?"
date: 2018-03-13
forum: Desktop Environments
---

### Post by Nathan_Veysey on 2018-03-13
Hello, 

I booted up the other day and have a no desktop problem, Ive checked around and no solutions seem to work. The best that will happen is firing up unity and I can drag the terminal around.


[LIST]
[*]Tried this, no change [https://askubuntu.com/questions/760356/ubuntu-16-04-unity-no-desktop-just-background-wallpaper/761882](https://askubuntu.com/questions/760356/ubuntu-16-04-unity-no-desktop-just-background-wallpaper/761882)
[*]Tried this, no change [https://ubuntuforums.org/showthread.php?t=2002750](https://ubuntuforums.org/showthread.php?t=2002750)
[/LIST]

The error on # unity is
[B]compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: switcher
compiz (core) - Info: Starting plugin: switcher
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct

[/B]and stalls at this point, no prompt given back (not sure if its meant to)[B]

Changes to the system - [/B]I can't confirm but I think I ran the updater last week.  Which may be related. The only other change is Ive added some NAS' to the network which I doubt would effect it but just in case theres a weird network discovery going on. I havn't configured these against the ubuntu machine yet - so unlikely. I'd like to get this fixed but don't know enough about the issue to resolve it, clearly some part of the UI isn't firing up properly. 
Any help would be appreciated. 

Thanks

---

### Post by Nathan_Veysey on 2018-03-13
I ran this, it didn't work - however on restart it did launch back into life. 

sudo apt-get purge gnome-session-flashback

rm -r ~/.cache/compizconfig-1

unity-tweak-tool --reset-unity

shutdown -r now

---

### Post by cruzer001 on 2018-03-13
Removing the whole ~/.cache may work for you.  Here's the latest:

[https://ubuntuforums.org/showthread.php?t=2386528](https://ubuntuforums.org/showthread.php?t=2386528)

---

### Post by jack.edgewood on 2018-03-15
I got this problem, too. After a weekly update, dash and menu are no longer visible. Keyboard shortcuts (eg windows button or backlight adjustment buttons) are not working either.

---

### Post by vanadium on 2018-03-15
Try the answers here: [https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears) Do not let you turn down by "This answer applies to older versions of Ubuntu.": it fully applies to Unity on 16.04, not to (the default desktop on) Ubuntu 17.10.

---

### Post by jack.edgewood on 2018-03-15
@vanadium

Okay, i will try it. (btw. just to make sure: im running 16.04.04 LTS; i did sudo apt-get update && upgrade -y there seems to be no fix for my problem in the repositories)

##

I did not work. I followed the steps and the checkbox at "Unity Plugin" was already set. As i unchecked and rechecked it i got "unresolved conflicts" -> ignored and checkbox still set. Back to terminal and reboot. Still no dash no menu. :(

If i try to 

unity --reset 

compizconfig - Error: Unable to find interface type 3 on 0x10065b0
[... ]
unity-panel-service stop/waiting
 unity-panel-service start/running process 2798 
start: Job failed to start

---

### Post by pf49 on 2018-03-15
I had the same problem last week, logged in and I could see my desktop icons and wallpaper but had no launcher or dash. I tried the first solution from here and it worked: [https://itsfoss.com/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-12-10-quick-tip/](https://itsfoss.com/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-12-10-quick-tip/).

Yesterday when I logged in the problem had returned, desktop icons but no launcher or dash. The solution I had tried before didn't work. I tried every single fix I could find, with no results. I was getting things like:

```
Reinstallation of ubuntu-desktop is not possible it cannot be downloaded
```

and 

```
Cannot autolaunch D-Bus without X11 $DISPLAY
```

and 

```
unity7 pre-start process terminated with status 143
```

and 

```
unity-panel-service Job failed to start
```

in response to various commands I entered. I tried the various things with /.cache and /.config but was getting messages that the directories or files couldn't be found, so those solutions were no use. 

I finally installed the GNOME desktop environment and tried that. Going into GNOME (Default) I initially got an *error* clock recovery reached maximum voltage. Subsequent attempts to boot into GNOME (Default) showed the exact same problem as Unity - I could see the wallpaper (no icons) and that was it. Booting into GNOME (Classic), however, worked, and I was able to limp along until today.

About half an hour ago I logged in with Unity again. This time my wallpaper and icons were gone and all I saw was the default purplish Ubuntu wallpaper. I opened up a terminal (Ctrl+Alt+F1) and typed:

```
sudo apt-get update
sudo apt-get upgrade
```

I installed the updates and rebooted. Now I can log into Unity. My dash and launcher (which I have placed on the bottom of the screen) both work. The launcher has had the Amazon button added back in to it and the button icons look like GNOME, not Unity. The wallpaper and desktop icons are gone. The top bar looks more like some sort of GNOME bar and the programs I had running up there (my-weather-indicator and psensor) are no longer there. 

It's not a perfect fix, but I can limp along until I can do a clean install of 18.04 next month. The fusion of GNOME and Unity elements is confusing, makes me wonder if 16.04 is being transitioned to some sort of GNOME look-alike and some of us got caught in the transition.

---

### Post by jack.edgewood on 2018-03-15
Okay, i got it working again. This did the trick for me:

> 
rm -rf ~/.compiz-1 ~/.config/compiz-1
sudo shutdown now

reboot PC


This will delete all of your customization of Dash... :sad: 

But at least Dash and Menu are back! Btw. this bug seems to be unfixed for 7 years, 3 month now.
[URL="https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444"]
[/URL][https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

[https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444](https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444)

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1212987](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1212987)

---

