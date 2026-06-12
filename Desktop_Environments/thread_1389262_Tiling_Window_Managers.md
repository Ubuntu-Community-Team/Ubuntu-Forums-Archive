---
title: "Tiling Window Managers"
date: 2010-01-24
forum: Desktop Environments
---

### Post by hv71 on 2010-01-24
Hey all,

I've been trying to find a tiling window manager that works for me; I've tried the following:

- ratpoison
- xmonad
- dwm
- i3
- wmii
- scrotwm
- awesome

what I am looking for is something that doesn't require learning a whole new language in order to be configured (like awesome or xmonad), but is still useable and has a relatively sensible way of handling floating windows.....

scrotwm seems very promising in this regard; on the project website:

"Scrotwm is a small dynamic tiling window manager for X11. It tries to stay out of the way so that valuable screen real estate can be used for much more important stuff. It has sane defaults and does not require one to learn a language to do any configuration. It was written by hackers for hackers and it strives to be small, compact and fast. "


...I really like the simplicity and to-the-point configuration of scrotwm, but unfortunately I am not having any luck getting it to work in a dual-screen setup....

Anyone else using scrotwm? Ideas?

Anyone else looking for a easy-to-configure, to-the-point tiling wm?

---

### Post by falconindy on 2010-01-24
I only know bits and pieces of C, and I thought that DWM was a breeze to setup. I think the real overhead in converting to any tiling WM setup is in (re)writing config files such as .Xdefaults and .xinitrc and building the proper support scripts to make the environment more workable. If you're interested, the GitHub link in my sig contains all my dotfiles and scripts, as well as my dwm build files.

---

### Post by Esthellin on 2010-06-28
I have been using scrotwm now and it is pretty good.

Although I have a few troubles settings some things up.
GNOME essentially REQUIRES use to have to use the gnome-panel to connect to the internet via the nm-applet. Iwconfig does not work at all for wireless network setup.
But if you try and run the gnome-panel if tiling window managers, it has a spasm and doesn't show any of the applets. Anyone found how to view the gnome-panel in these conditions?

---

### Post by burton247 on 2010-06-28
What languages do you know? 
What do you want to be able to configure?

I really enjoyed using both Xmonad and awesome (still use Xmonad) yes Haskell isn't the easiest to learn but you can do what you want with it. I use it with gnome.

If you just want to create floating windows and set apps to open on a certain desktop it's simple to config Xmonad following examples.

```


import XMonad
import XMonad.Config.Gnome
import XMonad.Util.EZConfig
import XMonad.Hooks.ManageDocks

myManageHook = composeAll 
				[ className =? "Gimp-2.6" --> doFloat
				, className =? "Gimp-2.6" --> doShift "3"
				, className =? "." --> doFloat
				]

main = xmonad $ gnomeConfig
	{ modMask = mod4Mask
	, manageHook = myManageHook <+> manageHook gnomeConfig
	}

```

Just a selection. Floats GIMP and sends it to work space 3, fairly simple IMO


> **Esthellin said:**
> 
GNOME essentially REQUIRES use to have to use the gnome-panel to connect to the internet via the nm-applet.

I have had nm-applet running in other things. Pretty much need a systemtray though, not only gnome-panel. It works with awesomes panel (and system tray). Will run in trayer or stalonetray or something. You should be able to run nm through CLI though, just not nm-applet.

---

### Post by Esthellin on 2010-06-29
> **burton247 said:**
> What languages do you know? 
What do you want to be able to configure?

I really enjoyed using both Xmonad and awesome (still use Xmonad) yes Haskell isn't the easiest to learn but you can do what you want with it. I use it with gnome.

If you just want to create floating windows and set apps to open on a certain desktop it's simple to config Xmonad following examples.

```


import XMonad
import XMonad.Config.Gnome
import XMonad.Util.EZConfig
import XMonad.Hooks.ManageDocks

myManageHook = composeAll 
				[ className =? "Gimp-2.6" --> doFloat
				, className =? "Gimp-2.6" --> doShift "3"
				, className =? "." --> doFloat
				]

main = xmonad $ gnomeConfig
	{ modMask = mod4Mask
	, manageHook = myManageHook <+> manageHook gnomeConfig
	}

```

Just a selection. Floats GIMP and sends it to work space 3, fairly simple IMO




I have had nm-applet running in other things. Pretty much need a systemtray though, not only gnome-panel. It works with awesomes panel (and system tray). Will run in trayer or stalonetray or something. You should be able to run nm through CLI though, just not nm-applet.

Unfortunately, there is no command line interface for the network manager in ubuntu, and using wireless-tools and ifconfig is useless.

I have however found a way to get the gnome-panel to appear correctly for me to use the nm-applet.

I added a quirk into the .scrotwm:
quirk[Gnome-panel:gnome-panel]=	FLOAT | ANYWHERE

When gnome-panel is run from a script or from the terminal, it will now place itself in its original position, allowing for wireless configuration and login.

:D

Thanks for the quick replies.

---

### Post by Shazzam6999 on 2010-06-29
I use dwm and I thought if was fairly easy to setup. That said it did take me a little time to figure out quite how everything works. No matter which wm you pick you should give it a couple weeks before you move on, there's a lot of little nuances that can take a while to master. I've never tried scrotwm but I've heard that xmonad works really well out of the box.

A bit of a side note: its cool that you got gnome-panel working in scrotwm, I do miss the traditional panel sometimes Whats the issue you have with ifconfig? I know that I have to use iwconfig/dhcpcd to connect.

---

### Post by burton247 on 2010-06-29
Shazzam6999 +1

Tricky to get my head round at the start but now hate using anything non-tiling, so much effort to do things! 

If you float gnome-panel can you move it around like any other window?

I like Xmonad cause it works with gnome, I have a full gnome environment just replace metacity with Xmonad. Those gnomeBindings things in my config allows Xmonad to work really well eith gnome-panel and everything else, It just tiles the area where there are no panels :)

---

### Post by Esthellin on 2010-06-29
> **burton247 said:**
> Shazzam6999 +1

Tricky to get my head round at the start but now hate using anything non-tiling, so much effort to do things! 

If you float gnome-panel can you move it around like any other window?

I like Xmonad cause it works with gnome, I have a full gnome environment just replace metacity with Xmonad. Those gnomeBindings things in my config allows Xmonad to work really well eith gnome-panel and everything else, It just tiles the area where there are no panels :)

Yeap, if its floating, you can move it around with the mouse, and use the right click to resize the window.

I agree about the non-tiling windows. I had to reinstall Ubuntu yesterday (screwed up my grub) and had to use the normal gnome-session with metacity. One word: ewwwwwwwwww haha. It was so frustrating having to - for just two windows - resize and finetune it (along with gnome-terminal's font size) so it all looked nice. In scrotwm and other tiling window managers. Open the two programs, done.

Shazzam6999-the issue is with not ifconfig, but with iwconfig. I have to use WEP encryption and a certain index to connect up, but for some reason, my computer doesn't want to 'associate' with the access points. I can set up the password and ESSID and everything. But I don't know what step I am missing to let me connect to the access point before I dhcpd. I have looked up forums with guides on the steps to take to get connected, but something is missing.

---

### Post by noahlt on 2010-06-29
If you don't want to learn a new language to configure your WM, try WMII.  By default the startup and configuration scripts are written in Bash, and the entire interface is exposed as a virtual filesystem, so it's very easy to configure.

---

### Post by Esthellin on 2010-07-14
I am using scrotwm, and it is really nice. However, I am having a little trouble with customozing the 'quirks'. For example, I want to be able to click on the 'fullscreen' button in youtube videos, and switch to that screen. But the fullscreen cant be switched to. It dissapears. Also, trying to click on the pages to zoom in full screen on this site: [http://www.gogoadelaide.com.au/feature/emedia/youyuadelaide.html](http://www.gogoadelaide.com.au/feature/emedia/youyuadelaide.html) is not possible. The screen flickers (the fullscreen thing appears) but dissapears straight away. I cant' even use the xprop trick to see what quirk to add because as soon as I switch to a terminal to start the program, the fullscreen thing dissapears.

Any hints on where to search for help?

EDIT: I am not sure if I need to add a quirk for Firefox, or for Adobe (what is used for the flash business. Any ideas?

---

