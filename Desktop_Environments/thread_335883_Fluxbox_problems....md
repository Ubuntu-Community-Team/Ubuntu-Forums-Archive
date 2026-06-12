---
title: "Fluxbox problems..."
date: 2007-01-10
forum: Desktop Environments
---

### Post by WetWired on 2007-01-10
I'm having trouble with fluxbox. I'd like to use it, but when I install it via Synaptic, and boot to it, it has no right click menu. I've tried copying the files from /etc/X11/fluxbox to my home directory, but it didn't work. I can't do much without a menu. lol

Also, is there a way to make it use the entire screen? I've hacked my xorg.conf to work properly in Gnome, and I think that's why it doesn't look right in fluxbox. I can't simply adjust it on my monitor because it's spread out as much as it can. So am I going to have to restore my xorg.conf to make it work, and then have to change it again every time I want to use Gnome? Is there a way to have an xorg.conf for each individual window manager you use?

Any comments would be appriciated.

---

### Post by jem7v on 2007-01-10
[http://fluxbox-wiki.org/index.php/Howto_edit_menu](http://fluxbox-wiki.org/index.php/Howto_edit_menu) explains about editing your menu.

Here's a snippet from one of mine so you can see what it might look like.

```

[begin] (JEMbuntu)

[exec] (Swiftfox) {swiftfox}
[exec] (Terminal2) {x-terminal-emulator}
[exec] (Nautilus) {nautilus --no-desktop}
[exec] (aMSN) {amsn}
[nop] (--------)
[exec] (GTK) {switch2}
[config] (Configuration) {}
[reconfig] (Reconfigure) {}
[submenu] (Wallpaper)
	[wallpapers] (~/Wallpaper) {fbsetbg -f}
[end]
[submenu] (Styles) {}
	[stylesdir] (/usr/share/fluxbox/styles) {}
	[stylesdir] (~/.fluxbox/styles) {}
[end]
[restart] (Restart Fluxbox)
[exit] (Exit)
[end]

```

---

### Post by WetWired on 2007-01-10
Ok, there's my menu... well, your menu, actually. How about the resolution part?

---

### Post by WetWired on 2007-01-10
What it's doing is using the same resolution that my login screen is using. When I boot into Gnome, it changes to what I have set in my xorg.conf, but I don't know how to make the login screen and fluxbox use the same configuration.

---

### Post by jem7v on 2007-01-11
No idea how to deal with the resolution, sadly... I'm not sure what to do there.  I never really took the time to figure out how to set things up properly in Fluxbox.  You'd probably find some answers here though: [http://fluxbox.sourceforge.net/docbook.php](http://fluxbox.sourceforge.net/docbook.php)

---

### Post by WetWired on 2007-01-11
Anyone got any ideas? I'd really like to use fluxbox, but if I can't make ubuntu do it, I may have to switch distro's :(

---

### Post by jem7v on 2007-01-11
What exactly is the problem with the screen, anyway?  Can you post a screenshot or a photo?

---

### Post by WetWired on 2007-01-11
I can, but it wouldn't show you what you need to see. It doesn't fill my monitor screen in fluxbox like it does in Gnome. I know the simplest solution would be to adjust the monitor, but it's adjusted as far as it can be. So there's not much else I can do unless there's some way to make fluxbox use the same resolution/refresh rate as gnome uses.

---

### Post by WetWired on 2007-01-11
I figured it out! 

[http://fluxbox-wiki.org/index.php/Howto_change_resolution](http://fluxbox-wiki.org/index.php/Howto_change_resolution)

I can play with this and make it just the way I want it. yay!

---

### Post by WetWired on 2007-01-11
k, now i have another question. How do I get rid of this tab?

[http://www.packet-surge.com/screenshot.jpeg](http://www.packet-surge.com/screenshot.jpeg)

---

### Post by ynnhoj on 2007-01-11
maybe that could be removed if you used a different theme?

[size=1](sorry, i'm not a fluxbox user, but i thought i'd throw that out there anyways, 'cause it's conceivable..)[/size]

---

### Post by yabbadabbadont on 2007-01-11
> **WetWired said:**
> k, now i have another question. How do I get rid of this tab?

[http://www.packet-surge.com/screenshot.jpeg](http://www.packet-surge.com/screenshot.jpeg)

Make sure that your ~/.fluxbox/init file contains:

session.screen0.tabs.intitlebar:        true

You should be able to change this setting through Fluxbox menu->Configure->Tab options->Tabs in Titlebar

---

### Post by WetWired on 2007-01-11
Thank you, sir. Much better now.

---

