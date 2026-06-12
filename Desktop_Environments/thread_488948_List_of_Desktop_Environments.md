---
title: "List of Desktop Environments?"
date: 2007-06-30
forum: Desktop Environments
---

### Post by lenninct on 2007-06-30
Can some one provide me with a list of desktop environments and links if possible.
thnx.

---

### Post by olejorgen on 2007-06-30
[http://en.wikipedia.org/wiki/Category:Free_desktop_environments](http://en.wikipedia.org/wiki/Category:Free_desktop_environments)

I don't think this is a complete list though

---

### Post by lenninct on 2007-06-30
thx....

---

### Post by RedSquirrel on 2007-07-03
For window managers...

[http://xwinman.org/](http://xwinman.org/)

---

### Post by Nythain on 2007-07-03
yay... a list of Desktop Environments that DOESNT list fluxbox as one :)

---

### Post by RedSquirrel on 2007-07-04
> **Nythain said:**
> yay... a list of Desktop Environments that DOESNT list fluxbox as one :)
Fluxbox is "only" a window manager. Who would want to bother with that? :)

---

### Post by Nythain on 2007-07-04
you dont know how many times i see people put fluxbox in the DE catagory, or explain it as a DE... so i was just happy to see a list that didnt :)

---

### Post by RedSquirrel on 2007-07-04
Yeah, me too. I've read a lot of posts where people were put off by the default (spartan) look of Fluxbox because they were misled to believe it came with desktop icons and really fancy panels etc.

---

### Post by OzzyFrank on 2007-07-06
How many can be installed into Ubuntu? And which ones? Cheers

---

### Post by RedSquirrel on 2007-07-06
Probably a lot of them. Ubuntu provides packages for an enormous amount of software.

Just do a search in Synaptic or using apt-cache.

I use Fluxbox pretty much all the time.

```
sudo apt-get install fluxbox
```followed by

```
sudo update-menus
```to build your Fluxbox menu.

After that, there will be an entry for Fluxbox in your 'Sessions' menu at the login screen.

Note: you can also compile your own software if for some reason a package doesn't exist in the Ubuntu repositories or if the package is too old for your taste. ;)

---

### Post by lenninct on 2007-07-06
thx for all the info

---

### Post by OzzyFrank on 2007-07-06
Hiya. Unfortunately, searching for desktop environments in Synaptic doesn't produce many results, so it's best to look around via Google (or keep asking in this forum), then do a seach in Synaptic for specific names.

As for Fluxbox, I have seen much mention in this forum that it is in fact a "window manager" not a "desktop environment". If you feel mischievious you can go to these threads and argue that it is a DE, hehe. Some are actually quite angry over this (the saying "get a life" comes to mind, unfortunately).

If you're thinking "But unlike Compiz and Beryl, Fluxbox you can log into like Gnome and KDE", I have to say I'm about as perplexed on that one. However, when Gnome went to hell due to a Compiz update, I used Fluxbox to troubleshoot (I could connect online there, but not in Gnome). As soon as I initiated Nautilus, my Gnome desktop (wallpaper and icons) appeared, but no panels, and the Fluxbox menu was gone, so it wasn't like a half-Fluxbox-half-Gnome, more like a Gnome with limited functionality. I thought that weird, so when I saw people going blue trying to get the rest of us to see the stark reality that Fluxbox is a WM not DE, I have to admit it all made more sense then.

My personal opinion: Fluxbox sucks big time. I know those who love it see even a vanilla Gnome as being too over the top, but the rest of us would see Fluxbox as being ridiculously minimalist. Not trying to start an argument here. Just saying an empty desktop with the only access to anything being a right-click menu isn't that inspiring for many. I will, however, say that I understand the minimalist approach more than those who spend much time and effort to get Beryl running, especially those who would uninstall a whole OS coz they can't get eye candy happening.

---

### Post by OzzyFrank on 2007-07-06
I suggest those who want other DEs check out **FVWM-Crystal**, a slim and fast-loading desktop that's big on transparencies. I installed it yesterday, and looks cool:

**[http://fvwm-crystal.org/](http://fvwm-crystal.org/) ** (just a paragraph of basic info I'll list below... for screenshots, go straight to **[http://fvwm-crystal.org/screenshots.html](http://fvwm-crystal.org/screenshots.html)**).

FVWM-Crystal aims to create an easy to use, eye-candy but also powerful desktop environment for Linux or other Unix-like operating systems. It uses following programs: FVWM as a window manager and "main core", ROX-Filer as file manager (manages icons on the desktop), xterm, aterm, mrxvt or urxvt as terminal emulators, MPD or XMMS as music players (there's built-in support for controlling these programs), and several other tools for different functions, like setting a wallpaper or making screen shots.

[IMG]http://fvwm-crystal.org/screenshots/wallpapers_thumb.jpg[/IMG][IMG]http://fvwm-crystal.org/screenshots/music_thumb.jpg[/IMG][IMG]http://fvwm-crystal.org/user-screenshots/nemo_thumb.jpg[/IMG]

PS: FVWM-Crystal can be installed through Synaptic.

---

### Post by RedSquirrel on 2007-07-06
> **OzzyFrank said:**
> As soon as I initiated Nautilus, my Gnome desktop (wallpaper and icons) appeared, but no panels, and the Fluxbox menu was gone, so it wasn't like a half-Fluxbox-half-Gnome, more like a Gnome with limited functionality. I thought that weird, so when I saw people going blue trying to get the rest of us to see the stark reality that Fluxbox is a WM not DE, I have to admit it all made more sense then.

My personal opinion: Fluxbox sucks big time. I know those who love it see even a vanilla Gnome as being too over the top, but the rest of us would see Fluxbox as being ridiculously minimalist. Not trying to start an argument here. Just saying an empty desktop with the only access to anything being a right-click menu isn't that inspiring for many. I will, however, say that I understand the minimalist approach more than those who spend much time and effort to get Beryl running, especially those who would uninstall a whole OS coz they can't get eye candy happening.

Fluxbox is very spartan when one first installs it because it is "only" a window manager.

It takes some time and effort to learn how to use it and how to configure it. Some people are just not up for that, and that's fine. In my experience, Fluxbox rewards careful study. It is an ideal working environment for me. While I prefer an uncluttered workspace, one can make Fluxbox as cluttered with eye candy as they want.

It is fortunate that we have so many choices for desktop environments and window managers.

By the way, your trouble with nautilus in Fluxbox is solved by running nautilus with the '--no-desktop' option. ;)

---

### Post by Nythain on 2007-07-07
i would just like to say that fluxbox at first might seem very "light" or minimalist and most run it that way... but once you learn your way around it, its very intricate... i have ultimate control over everything in fluxbox and i love it... on the topic of right clicking the menu, there is a key file that assigns hotkey shortcuts, and i believe one of the things you can set, is that menu (i could be wrong, i havent tried yet, but im pretty sure its RootMenu)

and yes, to each thier own, thats the joy of linux... a million options for a million users... from distros to desktops, window managers, and programs... so much better than the microsoft use Explorer or DIE approach of things

---

### Post by OzzyFrank on 2007-07-07
No offense meant to the Fluxbox enthusiasts, hehe. Just my personal opinion on first glance. But hey, it helped me get online and help fix Gnome, though like I said, at that point it was no longer Fluxbox but Gnome without panels after running Nautilus (which I find weird, as not like I ran Metacity or anything). But I've kept Fluxbox as it proved its worth, and since you say it has potential, I might look into that when I have some spare geeking time. FVWM-Crystal was a small download and was worth installing (and is a real desktop environment), though I've only had a quick look at that too. I'm happy with Gnome, but was really getting into Kubuntu Edgy when the drive died. Since installing Feisty I've found I've gone back to preferring Gnome, but now that I know I can install more than just KDE and Xfce into Ubuntu, I'll be happy to try others. Like I said, they are usually a small download and painless install, and I've found having other desktop environments as a backup is a wise thing. When Compiz started wreaking havoc on Gnome, I thought it would affect everything, but I was fortunately wrong, and happy to have installed Fluxbox 2 days earlier.

---

### Post by RedSquirrel on 2007-07-07
> **Nythain said:**
> on the topic of right clicking the menu, there is a key file that assigns hotkey shortcuts, and i believe one of the things you can set, is that menu (i could be wrong, i havent tried yet, but im pretty sure its RootMenu)

Yes that's correct. Here's what I use in my keys file:

```
Super_L :RootMenu
Super_R :RootMenu

```In addition to the right-click menu, one can use keyboard shorcuts (which are easy to setup) and other ways of launching applications. In other words, one is not limited to the right-click menu as the only way of accessing applications.





> **OzzyFrank said:**
> No offense meant to the Fluxbox enthusiasts, hehe. Just my personal opinion on first glance. But hey, it helped me get online and help fix Gnome, though like I said, at that point it was no longer Fluxbox but Gnome without panels after running Nautilus (which I find weird, as not like I ran Metacity or anything). 

Nautilus is used to manage the desktop in GNOME. Hence, when you run it in Fluxbox, it attempts to manage the desktop (set your wallpaper etc.) and you lose the Fluxbox right-click menu. The way to avoid this is to run nautilus like this (as I mentioned above):

```
nautilus --no-desktop
```Then you can use nautilus as a file manager without it trying to take over the desktop.

Here is the relevant entry from the nautilus man page:

```
**--no-desktop** 

Do not manage the desktop - ignore the preference set in the preferences dialog.
```

---

### Post by smartboyathome on 2007-07-08
> **OzzyFrank said:**
> I suggest those who want other DEs check out **FVWM-Crystal**, a slim and fast-loading desktop that's big on transparencies. I installed it yesterday, and looks cool:

**[http://fvwm-crystal.org/](http://fvwm-crystal.org/) ** (just a paragraph of basic info I'll list below... for screenshots, go straight to **[http://fvwm-crystal.org/screenshots.html](http://fvwm-crystal.org/screenshots.html)**).

FVWM-Crystal aims to create an easy to use, eye-candy but also powerful desktop environment for Linux or other Unix-like operating systems. It uses following programs: FVWM as a window manager and "main core", ROX-Filer as file manager (manages icons on the desktop), xterm, aterm, mrxvt or urxvt as terminal emulators, MPD or XMMS as music players (there's built-in support for controlling these programs), and several other tools for different functions, like setting a wallpaper or making screen shots.

[IMG]http://fvwm-crystal.org/screenshots/wallpapers_thumb.jpg[/IMG][IMG]http://fvwm-crystal.org/screenshots/music_thumb.jpg[/IMG][IMG]http://fvwm-crystal.org/user-screenshots/nemo_thumb.jpg[/IMG]

PS: FVWM-Crystal can be installed through Synaptic.

FVWM-Crystal isn't for everyone. You have to be comfertable with editing text files if you want a new theme. I am fine with this, and am actually making my own flavor of ubuntu to help my friends install it (plus, I like the experience I get from actually creating a distro ;)). Anyway, FVWM-Crystal isn't for everybody, and if you like it, you may want to look into the ROX desktop. :)

---

