---
title: "[SOLVED] Mass amount of Gnome/Compiz errors on 12.04"
date: 2013-03-10
forum: Desktop Environments
---

### Post by Halfling Rogue on 2013-03-10
Hey guys, I'm a longtime 10.04 user who's avoided upgrading to 12.04 due to a severe dislike of Unity and past nightmare scenarios in trying to get around it. I was recently forced to upgrade to 12.04 for requirement issues and the nightmare has begun anew. Anyone who can offer help for any of the following situations will have my undying gratitude.

Please note I have installed gnome-panel and gnome-tweak-tool, and unity is still installed. Ideally I'd like to be able to work in Gnome Classic view. Effects are not necessary as long as I have the functionality I want.

1) Noticing that none of the Gnome options provide Alt+Tab functionality for switching windows, I turned it on in CompizConfig Settings Manager under Window Management > Application Switcher. Since then, every time I use Gnome classic all of the windows are lacking a title bar, and the only thing that fixes it is running "compiz --replace" in a terminal (I tried resetting Compiz to default settings, and turning Window Decoration on and off; neither worked). Actually using Alt+Tab to app switch either freezes the system, glitches the top Gnome panel, or eradicates the title bar again. Turning the Application Switcher off again doesn't fix the title bar issue either.

**UPDATE:** After trying "Reset to Defaults" in Compiz again, "compiz --replace" has stopped restoring window title bars. Instead I get this message in the terminal:

```
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0xc00003

compiz (core) - Warn: failed to receive ConfigureNotify event on 0xc00014

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3000004

Initializing composite options...done
Initializing opengl options...done
Initializing mousepoll options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0x3400093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3400096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3400099!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
```

Running "metacity --replace" does restore the window title bars, but it's obviously not ideal. I currently have the command on the list of startup programs so that I don't have to keep a terminal open with it all the time. (Also, if the metacity command gets killed, not only do the title bars disappear, but the keyboard stops responding.)

Is there a way to fix this title bar issue? And is there a way to enable Alt+Tab functionality without getting Compiz involved?

2) Since making all of the above changes, if I try to log in to a session using "ubuntu" instead of any of the Gnome options, I get the desktop and absolutely nothing else. No panels, no launchers, no menus. Ctrl+Alt+Del and logging out is the only way to escape that mode. However, Unity is still installed as far as I can tell. Is there a way to fix this mode so that it has a menu/launcher again?

3) Gnome panel will, often and at random, refresh itself or just die entirely. Running "gnome-panel" from a terminal restores it but obviously I have to keep the terminal running or it dies again. Is there at least a way to restore it that doesn't necessitate keeping it running via a terminal?

4) I've used gnome-tweak-tool to change the theme colours; originally I selected Adwaita for GTK+ theme and Window theme and the window title bars were blue, but after checking a few other themes and then switching back, the Adwaita Window theme was displaying as white-gray instead. I prefer the blue Adwaita windows but I'm not sure if the glitch caused blue to show up when it doesn't exist in that theme, or if it exists and a glitch is causing it to *not* show up now. (Also for some reason, the Adwaita GTK+ theme has light-coloured window buttons on the task bar, etc., but the task bars themselves are black. Is there a way to tweak that?)

---

### Post by Paddy Landau on 2013-03-16
I'm sorry that I don't have an answer to your question, but could I ask why you installed gnome-panel? Ubuntu 12.04 already comes with GNOME Classic fall-back.

If you don't like Unity, it's best not to install Ubuntu but instead to install Kubuntu, Xubuntu or Lubuntu (whichever you prefer). No fall-back will be available in Ubuntu 14.04.

My suggestion is to back up your data and reinstall from scratch, using one of the other *buntu distros instead of Ubuntu.

---

### Post by Halfling Rogue on 2013-09-07
I was having issues with the GNOME Classic and was following a workaround online that lead me to my current configuration.

I wouldn't mind Unity so much if there was a way to keep a taskbar and a structured menu instead of an app search bar. Do you know if there are plans to accommodate either of those configurations? I want to stay with Ubuntu if I can because a large number of my apps (games, editors, etc.) are programmed only for this distro and I don't know how compatible they'd be with, say, Kubuntu.

Got into Ubuntu because of its flexibility and easy customizability, it's kind of a shame it's been swinging in this direction. :(

---

### Post by grahammechanical on 2013-09-07
Ubuntu was intended from its inception to be for humans. So, I am not surprised that there had been a determined shift away from the traditional Linux way of easy customizabiltiy. The more we modify away from the default setup the more we risk breaking things. But hey, that's the Linux way. Right? 

Why do you think the Compiz Configuration Settings Manager will modify Gnome panel? It modifies Compiz and its Unity plugin module. Sometimes a reinstall is the easiest way of fixing things. I am about to do it to an install of Saucy Salamander that determinedly refuses to load to a desktop. I do not modify my system as much as you but I have come to the conclusion that something is broken, be it Lightdm, Compiz, Unity. I have messed around trying to fix it and I have failed. Now, I am thinking - reinstall.

Regards.

---

### Post by Paddy Landau on 2013-09-07
> **Halfling Rogue said:**
> I wouldn't mind Unity so much if there was a way to keep a taskbar and a structured menu&#8230;
Unity has a structured menu. Press Super then the Applications button (or just press Super+A), and you'll see the words "Filter results" at the top right. That's your menu. You can use the menu in conjunction with the search bar, which is nice.

But, as I wrote before, just install an alternative flavour, such as Kubuntu, Xubuntu or Lubuntu, depending on your preferences and the power of your machine.

> **Halfling Rogue said:**
> I want to stay with Ubuntu if I can because a large number of my apps (games, editors, etc.) are programmed only for this distro and I don't know how compatible they'd be with, say, Kubuntu.
The apps are programmed for Linux, not for Ubuntu or Unity. A bit of background may help:
[LIST]
[*]Gnome 3 uses Gnome (obviously). 
[*]Ubuntu uses Gnome. 
[*]Kubuntu uses KDE. 
[*]Xubuntu uses XFCE. 
[*]Lubuntu uses LFCE. 
[/LIST]

 If you install an app designed for something other than your distro's manager (e.g. KDE for Ubuntu, XFCE for Lubuntu), all that happens is that the package manager will *automatically* install the required libraries.

So, suppose you have Kubuntu and you decide to install [FONT=lucida console]gnome-calculator[/FONT] because you prefer it. When you go to the Kubuntu Software Centre or Synaptic Package Manager, or you use [FONT=lucida console]apt-get[/FONT] on the command line, the system will automatically install all the necessary Gnome libraries as well as [FONT=lucida console]gnome-calculator[/FONT].

When you run [FONT=lucida console]gnome-calculator[/FONT], it will run perfectly within Kubuntu. It may look a little strange because it has a different theme, but it will work.

Later, you decide to install [FONT=lucida console]gedit[/FONT]. This time, the system will not install all the Gnome libraries, because it already did so when you installed [FONT=lucida console]gnome-calculator[/FONT]. It will install only gedit.

As with [FONT=lucida console]gnome-calculator[/FONT], [FONT=lucida console]gedit[/FONT] will run perfectly, although the theme may look a little out of place.

So go ahead, install a different *buntu flavour, and install whichever extra apps you want.

> **grahammechanical said:**
> Ubuntu was intended from its inception to be for humans. So, I am not surprised that there had been a determined shift away from the traditional Linux way of easy customizabiltiy.
Sort of. Remember that Canonical's aim is to unify (hence "Unity") across several platforms. That is the reason it is moving away from easy customisability. For great customisability, you need to look at a different *buntu flavour.

If you look at the various months' screenshot examples (e.g. [this month's]("http://ubuntuforums.org/showthread.php?t=2171766"), [last month's]("http://ubuntuforums.org/showthread.php?t=2164581"), or [July's]("http://ubuntuforums.org/showthread.php?t=2159269")), you'll see occasional examples where people have done extraordinary things with Xubuntu, Kubuntu, Lubuntu, Mint, Windows, Mac, Android, and more &#8212; yes, even Ubuntu. Customisability is all there, albeit not that easy with Unity, Windows, Android or iPad.

> **grahammechanical said:**
> &#8230; I have come to the conclusion that something is broken, be it Lightdm, Compiz, Unity. I have messed around trying to fix it and I have failed. Now, I am thinking - reinstall.
Sounds like Windows :)

Yes, a reinstallation is often easier. But, if you find out what specifically is broken, a complete uninstall ("purge") followed by a reinstallation may solve your problem.

---

### Post by ibjsb4 on 2013-09-07
> **Paddy Landau said:**
> No fall-back will be available in Ubuntu 14.04.

I believe it will be called "Flashback" in the future.

---

### Post by Halfling Rogue on 2013-09-07
That's the first I've heard that about the result filtering - thank you! And good point - a lot of my games etc. install with .debs which should be compatible (a lot, but not all - it'd be an easier decision to make if I could remember the formats of the mess of things I have installed).

With that in mind I might try dual-booting Kubuntu and Ubuntu until I figure out which I'd like to keep (if I can get my [monitor working again]("http://ubuntuforums.org/showthread.php?t=2172903")...).

Thanks very much everyone for all the advice.

---

### Post by Paddy Landau on 2013-09-07
I've just seen your monitor problem. May I suggest that, as you don't have an answer, you reinstall as you suggest.

But first: create a Live CD (or a Live USB) with Kubuntu. Boot the Live CD and try Kubuntu. Does it work? Do you feel happier with the panel and menu? If so install Kubuntu overwriting Ubuntu.

You could try Lubuntu instead if you have a low-spec computer.

Ensure that you have a **full backup** first!

**EDIT**: If you need stability, install the LTS version 12.04. Bear in mind that Lubuntu does not have an LTS version.

---

### Post by Halfling Rogue on 2013-09-07
I just managed to fix it! Seems like it was a conflict between the default Ubuntu packages for nvidia and the proprietary driver I downloaded from Nvidia's site.

A live CD does indeed sound like a good idea. I'lll do a backup and give it a shot. Thanks again!

---

### Post by Paddy Landau on 2013-09-08
Excellent! I'm pleased you managed to fix it.

If this has solved your problem, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

If you try one of the other *buntu flavours, let us know how it goes.

---

