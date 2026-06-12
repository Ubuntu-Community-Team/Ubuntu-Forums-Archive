---
title: "No Compiz and No Unity in Ubuntu 11.04"
date: 2011-05-16
forum: Desktop Environments
---

### Post by xbobby_bobx on 2011-05-16
Hey guys :( I'm having some serious problem here, last night I installed Ubuntu 11.04 (fresh new install) on my laptop, and I was shocked with the fact that I can't use Unity. After logging in the screen goes black with a mouse pointer, and I can't do anything, I restarted into Ubuntu Classic tried to log in, it freezes on the wallpaper with no icons or anything just the mouse pointer loading forever, my graphic card is ATI Radeon x1200 used to work perfect on Ubuntu 10.10, what should I do to fix this problem? PLEASE HELP!! :'(

---

### Post by Krytarik on 2011-05-16
Try upgrading the video driver through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos.
Notice that this would upgrade a lot of other packages as well.
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```If you need/want to remove those PPA and downgrade the concerning packages again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```Greetings.

---

### Post by xbobby_bobx on 2011-05-17
Thank you for the quick reply, I did what you said and it worked like charm, but after few tweeks on compiz it went back again :/ I know I have to remove them and do it all over again ( I used compiz --replace)which I think it messed the thing up, but is there anyway I can save these new drivers? Thanks. :)

Note: I really need this since my Windows 7 doesn't support my graphic card :(

---

### Post by Krytarik on 2011-05-17
- What exactly did you change then in CompizConfig Settings Manager, if you are referring to that?

- "compiz --replace" doesn't modify the settings.

- No need to reinstall the driver, since the issue seems to be with Compiz, apparently specifically with its settings. You can't get any better driver than the open source "radeon" anyway, you can only switch between those from the official repos of Natty and those from Xorg-Edgers' PPA.

---

### Post by xbobby_bobx on 2011-05-17
Nononono Compiz worked after what I did what you said, but I did few things to tweek Compiz then it happened what happened so I'm gonna try to reinstall them and leave the drivers and Compiz alone :P do you have any other advice I can take? :)

---

### Post by Krytarik on 2011-05-17
There we are again. See my previous post.

---

### Post by xbobby_bobx on 2011-05-17
I did read your post, but here is the thing, drivers on Ubuntu 11.04 are strongly unstable, and they missed a lot of plugins for the old Graphic Cards, that's why when I restarted my machine (Applying the Compiz) the driver got reset on the old one, so what I'm gonna do is update the driver then back it up again. I just checked and it went back on the old settings. I don't know why it's not saving the settings. :/

---

### Post by Krytarik on 2011-05-17
You are mixing up the video driver, which keeps installed/running even if you mess up Compiz completely, and Compiz' settings, which may get reset if you try to change certain things --namely trying to enable the Cube--, or you might have issues to save its settings at all as you described it.

So, I repeat my earlier question:
> **Krytarik said:**
> - What exactly did you change then in  CompizConfig Settings Manager, if you are referring to that?

---

### Post by xbobby_bobx on 2011-05-17
I only Applied the OpenGL, then logged off went on Unity then restarted and happened what happened.

---

### Post by Krytarik on 2011-05-17
> **xbobby_bobx said:**
> I only Applied the OpenGL
So, what exactly did you change there?
Or are you meaning that you just enabled it?

And after that, both session options, "Ubuntu" and "Ubuntu Classic", don't work, meaning you either have a black screen with only the mouse or your wallpaper with a rotating mouse pointer, like you described in your OP? Even right-clicking doesn't work then?

---

### Post by xbobby_bobx on 2011-05-17
I just enabled it. And after that both of the other sessions doesn't work freezes as what I claimed before, and yes the right click doesn't work, actually nothing work, I can just move the pointer, that's all other than that I can't do anything. And if I want to shut it down I need to hold the power button, but yeah this the problem.

---

### Post by Krytarik on 2011-05-18
Maybe you really shouldn't enable the "OpenGL" plugin then.

Log  in to "Ubuntu Classic (No effects)" and disable it in both profiles of  CCSM, "Unity" and "Default". To choose them, click at the lower left at  "Preferences".

---

### Post by xbobby_bobx on 2011-05-18
I removed Compiz and going to install it all over again.

---

### Post by xbobby_bobx on 2011-05-18
Now I'm having a problem with my theme, it changes after 15 seconds to the clear look theme but the windows still have the Ambiance theme, I don't know what's wrong with 11.04 it's really bothering

---

### Post by Krytarik on 2011-05-18
> **xbobby_bobx said:**
> Now I'm having a problem with my theme, it changes after 15 seconds to the clear look theme but the windows still have the Ambiance theme
You are experiencing this bug:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

It has been around since Maverick 10.10, although it's exact behaviour changed a bit in Natty 11.04.

Recent threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Here is another, most recent, workaround that may work:
[http://ubuntuforums.org/showthread.php?p=10800526#post10800526](http://ubuntuforums.org/showthread.php?p=10800526#post10800526)

---

### Post by xbobby_bobx on 2011-05-18
I fixed it but I have a strong feeling it's coming back again, oh and by the way I removed Compiz and I'm going to install it tomorrow, I have a question though. How do I apply the Ubuntu default effects? I used to go to the appearance menu and apply it from there, how do I do it in 11.04? :/

---

### Post by Krytarik on 2011-05-18
To reset Compiz' setting to the defaults:
"CompizConfig Settings Manager -> Preferences (lower left) -> Profile -> Reset to defaults"

However, there are no presets anymore, apparently, as you know them from the "Visual Effects" tab in previous releases, like "Normal" and "Extra".

---

### Post by xbobby_bobx on 2011-05-19
I tried it didn't work, and now compiz doesn't work at all, unless if I use compiz --replace, then once I close the terminal it goes back to the default :/

---

### Post by Krytarik on 2011-05-19
Please see this guide to check for Compiz/Unity support and how to force them to run at login:
[http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

Post the results of these checks.

---

### Post by xbobby_bobx on 2011-05-19
No need to, after several tries, I found out that 11.04 is not worth it, it will just get me a headache so I removed it, went back to 10.10, I think Ubuntu is done by now, I'm switching to Windows. :(

---

