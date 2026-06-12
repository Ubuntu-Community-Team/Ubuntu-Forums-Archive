---
title: "compiz on kubuntu"
date: 2009-08-24
forum: Desktop Environments
---

### Post by spedax on 2009-08-24
When reading the Desktop effect FAQ it says ubuntu and kubuntu both have compiz, but it seems like they only tell you how to access it when using ubuntu.

How do I know if Compiz is enabled (How can I disable Compiz?)

    On Ubuntu 7.10 and up:
    Open System > Preferences > Appearance. Click on the Visual Effects tab. If Compiz and desktop effects are enabled, Normal, Extra, or Custom will be selected. If Compiz is disabled, None will be selected. To switch modes, simply click on another selection. Changes take effect immediately.

So I tried looking with packet manager but all the packages of compiz say its for gnome. 

Any suggestions how to install it on kubuntu ? ( I tried a couple search engines and didnt find something clear enough for me to try, dont want to mess up my system )

Thanks in advance

---

### Post by MickS on 2009-08-24
You've Most likely already got Compiz installed, just need to be able to control it so you need CCSM to adjust things and it's well worth getting the Fusion icon for switching between window managers. I have Kubuntu and my compiz works very well and did from the day I installed it. Both CCSM and the fusion icon are in the repositories so make sure you have them before worrying about anything else.

Mick

---

### Post by Zorael on 2009-08-24
First you'd need to install Compiz, obviously.
```
$ sudo aptitude install compiz-core compiz-plugins compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-kde compiz-wrapper compizconfig-settings-manager
```
Alternatively find and tag those packages in your package manager of choice (Synaptic, etc).
> [list][*]compiz-core
[*]compiz-plugins
[*]compiz-fusion-plugins-main
[*]compiz-fusion-plugins-extra
[*]compiz-kde
[*]compiz-wrapper
[*]compizconfig-settings-manager[/list]
It's possible to just install the virtual package **compiz**, but then you get **compiz-gnome** pulled as a dependency that you really don't need.

Then you'd need to set KDE to use Compiz as the default window manager. System Settings -> Default Applications -> Window Manager, Use a different Window Manager, compiz-wrapper (or compiz or whatever is listed there).

That should hopefully make it start automatically when you log in, but to apply it immediately, open up a terminal and run the following. (Do it in a terminal to be able to spot any error messages that would otherwise go lost if you ran it from a run box [alt+f2].)
```
$ compiz --replace &
```

Use the CompizConfig Settings Manager (**ccsm**) to configure it - this replaces the whole "visual effects" deal. It should pop up in your kickoff menu, though you could start it manually by running ccsm (from a run box).

You could also install the fusion tray icon (package name **fusion-icon**), to allow for easy swapping between window managers (and compositors).

Do note that Compiz doesn't really integrate well into KDE, so any options that you find in ccsm will override similar options found in System Settings.

---

### Post by krazyd on 2009-08-24
@spedax:
also note that kde has it's own compositing engine built in. it's quite similar to compiz. Just go to System Settings > Desktop > Desktop Effects and enable it.

---

