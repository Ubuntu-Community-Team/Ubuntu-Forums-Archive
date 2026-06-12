---
title: "Not sure how to title this - general question"
date: 2011-04-09
forum: Desktop Environments
---

### Post by ClientAlive on 2011-04-09
I was reading this article:  [http://www.ghacks.net/2008/12/09/get-to-know-linux-desktop-environment-vs-window-manager/](http://www.ghacks.net/2008/12/09/get-to-know-linux-desktop-environment-vs-window-manager/)  and got the idea that if a person were using Compiz Fusion as their window manager they could run their system with just Compiz on top of X and that's it.

You see, one of the things I think about a lot is not having extra stuff hanging around on the system that is not being used. I love what I've seen Compiz can do and would like to go with it; but, since I don't know much about how to use Compiz yet, I'm not sure I would actually take that leap right this minute. I just wondered if I would even need Gnome with it or the window manager Gnome uses?

Thanks in advance.
Jake
:D

---

### Post by 3Miro on 2011-04-09
Compiz is the default window manager in Ubuntu. If your hardware supports compiz, you are already using it.

Stand-alone compiz is harder to setup (as compiz wasn't intended as a standalone app), but it is absolutely doable. You will lose the panels, some of the applications that do the settings and maybe some of the sound/network controls. You can get those back if you get AWN + Compiz (for example).

---

### Post by ClientAlive on 2011-04-09
So then, if I am running Ubuntu 11.04, the way things are by default is: Compiz on top of X then Unity on top of Compiz? Or in other words: X plus Compiz plus Unity?

If I were to be running and earlier version of Ubuntu (say 10.04 for example) it would be X plus (Compiz?) plus Gnome?

Just trying to get a grasp of this.

Thanks
Jake

---

### Post by Copper Bezel on 2011-04-09
Gnome is a suite of applications that make your life simpler - services and daemons and settings managers. When you look at the Processes pane of your System Monitor, most of those little bits running are Gnome. It's not a single program.

The Gnome desktop environment primarily consists of Nautilus (which draws the desktop as well as providing the file manager), Gnome Panel (which provides the panel itself and other services, like the Run Dialog), and the Metacity window decorator and window manager. Compiz is a window manager and compositor that can be run (and on most systems usually is run) in place of Metacity in its role as a window manager. There are other things running, of course, like the network manager to allow for network connections and the settings daemon to apply GTK theming and other settings to your running applications.

After 10.04 or 10.10, setting up a Compiz standalone session got quite a bit easier. However, a Compiz session running Nautilus, Gnome Panel, and Gnome settings and services just *is* Gnome for all intents and purposes, except that some applications and services won't really work if they don't recognize your session - xdg-open (which handles what application a file is sent to) and the session menu items in the Gnome Menu or Session Indicator Applet, for instance.

You can make your desktop just a bit lighter-weight by doing this, but it may or may not be worth the trouble. You can get documentation [_from the Ubuntu Wiki_]("https://help.ubuntu.com/community/CompizStandalone").

I've switched, and I like the result - things are a bit faster on my netbook without the Nautilus desktop, for instance, using Compiz wallpaper instead, and I don't use the Gnome Panel - but you can get most of the same effects more easily by changing the required components for your Gnome session through gconf-editor.

But to the, ah, philosophical side of your question:

Whatever you're running is running within an xsession, and whether it's Unity or Classic Gnome, it consists of a compositor or window manager (Metacity's or Compiz), a window decorator (Metacity's or Emerald), the visible applications themselves (like the panel and desktop and whatever else you're running), and services running in the background. In my case in CompizStandalone on a fresh boot, that's Compiz, Emerald, AWN, and Gnome background services.

Unity is a plugin for Compiz; it's provided by the same process that's running all of the usual visual effects and managing the window compositing. The same relationship is true of Gnome Shell and Mutter. In both cases, what's traditionally the "panel" has been integrated into the window manager, so if you wanted to think of it as layers, Unity actually *removes* one in comparison to Classic. = ) 

But that actually doesn't mean anything, because it's the same things that need to be done whether it's broken up into two applications or not. = )

---

### Post by ClientAlive on 2011-04-10
Thanks Copper. That sure gives me a lot to go on. I appreciate it.

Jake

---

