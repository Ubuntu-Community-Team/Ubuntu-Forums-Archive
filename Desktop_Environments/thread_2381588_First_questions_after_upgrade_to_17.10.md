---
title: "First questions after upgrade to 17.10"
date: 2018-01-02
forum: Desktop Environments
---

### Post by 2CV67 on 2018-01-02
Hi!
I just upgradedfrom 17.04 to 17.10
Obviously a lot of effort has gone into making it look & behave like Unity, so not too much adaptation is necessary at first - good!
But & am surprised how some things stopped working or were less good. (OK - not that surprised after experience of numerous upgrades).
I started the usual searching & found that people are "blaming" Wayland (whatever that is) for all or most of the problems.
Checking at login, I see I do have an option to use "Ubuntu on Xorg" (again - whatever that is) but I haven't tried that yet.

I would be interested to hear from experts (compared with me, that's easy..) whether I should be using Xorg or trying to find alternative & compatible applications to do the jobs which no longer work.
I guess that might depend on whether these problems are temporary bugs which will soon be fixed, or are permanent incompatibilities?

The main items which need fixing are:
- Epson V200 photo scanner
- Shutter screen-shot app.
- Synaptic Package Manager
- I understand GParted won't work either though I haven't tried it yet.

Things which seem less good & I would like to improve:
- Icons in Dash only launch/open apps whereas with Unity they would toggle open/hide, which was very handy.
- Icons in Dash don't show which apps are active but hidden - Unity showed that by different tile background color which was handy for orderly shut-down & also for finding active apps slightly easier, not to mention for checking at a glance that I have not forgotten to activate Thunderbird. EDIT - I found there is a tiny red dot on active tiles, but it is hardly visible at the edge of my screen...
- Probably lots of items can be improved using Gnome Tweaks Tool, but it is not available in the "Software" app (which has very little in it at all...) or in Synapt which I can't open from the dash/launcher. Maybe I could install/open Tweaks &/or Synapt via terminal, but I strongly prefer to stick to "safer" GUI methods.

Comments on any of these items would be appreciated!

Thanks!

---

### Post by #&amp;thj^% on 2018-01-02
"Ubuntu on Xorg" is like all the buntu's we have become accustom to.(All commands and functions)
Wayland is the New replacement for Xorg and has many difference's compared to what we once were in the habit of seeing.
Many GUI's will need elevated privlige's that can be called with adding a command on the Terminal _that will only last that logged in session._
For that workaround use this:
```
xhost +si:localuser:root
```
**You can also use xhost + to allow and xhost &#8211; to return it to the default state.**
Now All/Most GUI's "Synaptic Gparted Gdebi etc etc" with the proper syntax will open.
But in the end only you can decide if it is better than a Xorg session.
Some folks like myself are just not as graceful in accepting new changes to our systems  :)

---

### Post by ajgreeny on 2018-01-02
If you want to continue using wayland and not go back to xorg simply add that **xhost +si:localuser:root** command to your startup applications; there is no need to create a script or anything else to do this, simply copy that command to the "command" line when you add a new startup application.

---

### Post by 2CV67 on 2018-01-02
Well, I tried an Xorg session.
It looks & works about the same as Wayland.
- Scanner still won't connect (is this an expected result?).
- Shutter works OK except its own window obscures the target selection instead of hiding when you start defining the selection.
- Synapt opens & allows installing stuff - including Gnome Tweak Tool.
- Tweak let me shift the window buttons Left, which I wanted, but had nothing for highlighting launcher buttons of minimized apps, nor for toggling min/max via the launcher.

I undid those tweaks & opened a Wayland session:
- Tweaks worked OK as above.
- Shutter NG.
- Synapt NG.

I checked the scanner In Windows 10 with its Epson driver & it works OK (so not a cable problem).
It is noticeable that in W10, the scanner wakes up, turns on lamps & excercises the scan head as soon as I press the On button (which it also did in Ubuntu 17.04) whereas in 17.10 nothing happens with the on button.
I shall have to search that behaviour.

So - some progress but still no scanner & still no window-toggling from the launcher & still no visible sign of minimized windows on the launcher.
Which would be the best replacement for Shutter if that is not going to work?

All suggestions welcome!

Thanks both, for your suggested command.
I am so far from understanding it that I will keep it in reserve for the moment & stick to switching sessions, though I don't doubt at all that it is effective & safe!

---

### Post by 2CV67 on 2018-01-03
Well, I made a new startup application with "xhost +si:localuser:root" & that allows Synapt to run in Wayland OK - thanks.
It has no effect on Shutter though & I can't run stuff like "gksu nautilus" either, so I am temporarily going back to Xorg as the least-problem option.

The scanner does not work in Wayland or Xorg or Unity & I think I will start a specific thread on that, with my troubleshooting so far, for what may be a big problem!

Back in the details of the Gnome desktop, I have not been able to locate any Launcher button for "show desktop" - is there a 1-click solution for that (minimizing all apps)?

And no suggestion for making the active apps more visible on the Launcher tiles?
I wondered whether there was a more comprehensive tool than Tweaks?

---

### Post by 2CV67 on 2018-01-04
The Epson scanner is now working OK in Wayland & in Xorg.

I found the solution on the French Ubuntu Forum.
The exlanation is that 17.10 doesn't use the traditional libsane library, but an experimental version (!!) called libsane1 - 1.0.27-1~experimental2ubuntu2.1
You can see that in Synapt.

Apparently libsane1 looks for the scanner data in /usr/lib/x86_64-linux-gnu/sane/ and not in the usual /usr/lib/sane/.
So you need to copy the Epson data to the new position:

```
sudo cp /usr/lib/sane/libsane-epkowa.* /usr/lib/x86_64-linux-gnu/sane/
```

[https://doc.ubuntu-fr.org/scanner_epson](https://doc.ubuntu-fr.org/scanner_epson)

---

### Post by 2CV67 on 2018-01-16
I found a way to "Show Desktop" which I had been looking for.
There is a "Show Desktop Button" available as a Gnome Shell extension.
This involves jumping through strange hoops, going via Firefox to install "gnome-shell-extensions" add-on then "chrome-gnome-shell".
After that, the "Show Desktop Button" extension can be added via the Gnome Extensions website.
[https://extensions.gnome.org/](https://extensions.gnome.org/)
It can then be activated & edited either via that website or via Gnome Tweak Tool.

Not as good as the Unity version in that it is on the top panel rather than on the Launcher.
But still it works OK - toggling between Desktop & whatever you had open previously.

Now I need something to make the Launcher Tiles toggle open/closed too...

And better visibility for the Tiles which are active...

All idea welcome!

---

