---
title: "How-to: Expand/Collapse the Xfce menu with the Windows key"
date: 2009-01-09
forum: General Help
---

### Post by NearlyALaugh on 2009-01-09
Note: Originally posted by me on the [Debian Forums](http://forums.debian.net/viewtopic.php?t=34671&start=0). If you're using the Xfce desktop environment, these steps should work.


[size=6]How-to: Expand/Collapse the Xfce menu with the Windows key[/size]

Whether you're going for an [all-out lookalike of Windows XP](http://chris4585.wordpress.com/2008/05/18/windows-xp-or-should-i-say-xfce/) or would simply like to make use of all the keys on your keyboard, you may find it desirable to be able to expand and collapse the Xfce menu with your Windows key:

[img]http://nearlyalaugh.com/files/xmenu.gif[/img]

I know this is merely a cosmetic tweak, but it's convenient, and I know there are people out there who wish to have this capability.

The steps below will also show you how to map the "Menu" key to expand and collapse the Xfce window list at the position of your cursor:

[img]http://nearlyalaugh.com/files/menu.gif[/img]

Both of these may be accomplished with a few simple steps. I'm using Debian Lenny, but I presume that much the same may be accomplished in Xfce on Ubuntu.

(My desktop background, by the way, is of the cave painting at [Cueva de las Manos](http://en.wikipedia.org/wiki/Cueva_de_las_manos) in Argentina.)

[size=5]Create a Simple Shell Script[/size]

You can expand the Xfce menu with the command **xfce4-popup-menu**; try it yourself in a terminal. By default, the keyboard shortcut <Ctrl>+<Esc> does just this. The problem is that there is no equivalent command to collapse the menu -- for this you must use the <Esc> key. The same goes for the window list, whose command is **xfdesktop -windowlist**. (If you want to make it really Windows-like, find the command that brings up the context menu and use that in place of the window list.) To get around this problem, I wrote a simple shell script that temporarily turns the Windows or Menu keys into Escape. Enter these commands into a terminal:
```
$ cd ~/
$ mousepad .popup
```This should bring up a blank file. Into it, paste the following:
```
#!/bin/bash

if [ "$1" = "win" ] ; then
	if [ "$popup" == 1 ] ; then
		xmodmap -e "keycode 115 = Super_L"
		xmodmap -e "keycode 116 = Super_R"
		popup=0
	else
		xfce4-popup-menu
		xmodmap -e "keycode 115 = Escape"
		xmodmap -e "keycode 116 = Escape"
		popup=1
	fi
fi

if [ "$1" = "menu" ] ; then
	if [ "$popup" == 1 ] ; then
		xmodmap -e "keycode 117 = Menu"
		popup=0
	else
		xfdesktop -windowlist
		xmodmap -e "keycode 117 = Escape"
		popup=1
	fi
fi
```Save and exit the file. This will be a hidden file in your home directory. You may, of course, save it to whatever directory you choose; just modify the steps accordingly. Also note that your keycodes may not be the same as mine. Use the **xev** command to look for the proper keycodes if these don't match up.

Before you can use this script, you have to make it executable:
```
$ chmod 755 .popup
```

[size=5]Map the Windows and Menu keys to the Popup Script[/size]

There are two ways of going about this: the first is less user-friendly but more efficient whereas the second is much easier but causes a (minimal) process to run in the background.

**The Xmodmap Method:**

This method makes use of already-present processes -- xmodmap and Xfce's built-in keyboard settings. See [the Xfce wiki](http://wiki.xfce.org/faq#keyboard), from which the below steps are taken:> **Is it possible to use Media keys in the Shortcut Editor?**

Use xmodmap to assign keycodes to your Media keys to make them available for the Xfce shortcut editor:

To determine keycodes of the multimedia keys use the program xev. Create a .Xmodmap file in your $HOME directory containing those keycodes and assign keysyms to them. Example:

```
 keycode 162 = XF86AudioPlay
 keycode 164 = XF86AudioStop
 keycode 160 = XF86AudioMute
 keycode 144 = XF86AudioPrev
 keycode 153 = XF86AudioNext
 keycode 176 = XF86AudioRaiseVolume
 keycode 174 = XF86AudioLowerVolume
 keycode 237 = XF86AudioMedia
 keycode 230 = XF86Favorites
 keycode 236 = XF86Mail
 keycode 178 = XF86WWW
```


All possible keysyms can be found in /usr/lib/X11/XKeysymDB or /usr/share/X11/XKeysymDB. To ensure that the .Xmodmap file is loaded when you start Xfce add /usr/bin/xmodmap $HOME/.Xmodmap to your .xinitrc or .xprofile file. When you start the shortcut editor the assigned keysyms should show up when you press one of your multimedia keys. Now it is possible to assign a command to them.These steps will probably require some modification to work. See also [this post](http://ubuntuforums.org/showpost.php?p=5112319&postcount=5) at the Ubuntu Forums for additional ideas.

Once you have your keys mapped, go to **Xfce Menu > Settings > Keyboard Settings**, click the "Shortcuts" tab, and create a new keyboard theme (such as "Custom"). Map the Windows keys to the command **./.popup win** and the Menu key to **./.popup menu**. That should take care of it -- the (nominally) hard part is just getting the keys mapped satisfactorily.

**The XBindKeys Method:**

This is the route I chose to go: It costs you a minimal process running in the background, but provides one-click modification to all of the keys on your keyboard:

[img]http://nearlyalaugh.com/files/xbindkeys-config.png[/img]

Install XBindKeys:
```
$ sudo aptitude install xbindkeys-config
```
Tell it to create a config file:
```
$ xbindkeys --defaults > ~/.xbindkeysrc
```
And finally run the GUI:
```
$ xbindkeys-config
```

To map a new key, press the "New" button at the bottom: give the key a name, use "Get Key" and press the key you want, and set "Action" to either **./.popup win** for the Windows key or **./.popup menu** for the window list.

Finally, be sure to set **xbindkeys** to run on startup: Go to **Xfce Menu > Settings > Autostarted Applications** and add a new application. It doesn't matter what you call it -- for me, the name is "xbindkeys" and the description "Enable Custom Keybindings" -- so long as the command is **xbindkeys**.

That's it! Your Windows keys should now expand and collapse the Xfce menu, and the Menu key should do the same with Xfce's window list.

[size=5]In Defense of Debian (And Ubuntu)[/size]

Why is it necessary to go through all these steps just to set up working keybindings? I shouldn't have to explain this to many people here, but for those migrating from Windows with lingering doubts, here it is: Everybody's keyboards -- and tastes -- are different. The Linux programmer is tasked with creating programs that work, not in emulating all the usual features of another operating system. Furthermore, many of settings that appear to "just work" in Windows have actually been tweaked by the PC manufacturer. If you switched out one keyboard with another, there's a good chance that Windows wouldn't recognize the new settings either. The great thing about Linux is that it gives you the tools to modify whatever you like. It's my guess that the steps above are much simpler than those necessary to fix similar hardware tweaks in Windows.

I hope this has helped you make your desktop even more amenable to your personal preferences. Have fun!

---

