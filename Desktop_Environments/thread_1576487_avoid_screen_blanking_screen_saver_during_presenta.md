---
title: "avoid screen blanking /screen saver during presentation"
date: 2010-09-17
forum: Desktop Environments
---

### Post by RikoW on 2010-09-17
Dear all,

during presentation from my laptop and longer discussions on one particular slide (for example the summary slide), it often happens, that the screen goes blank and/or the screen saver turns on.

Do you know how to avoid this happening in full screen mode of an application? I'd be happy to create a button on the panel to toggle this on and off with a shell script, alas I don't know how to turn off the screen saver (except killing it) and screen blanking from the command line ...

Any hint would be appreciated.

Thanks and cheers,
           Riko

---

### Post by cutekazuya on 2010-09-17
can you not just go to System > Preferences > Screensaver

and Untick "Activate screensaver when computer is idle"

if for whatever reason this doesnt work

you can press "Alt+F2" type "gconf-editor" press enter

go to apps > gnome-screensaver > untick "idle_activation_enabled"

---

### Post by dirty_harry on 2010-09-17
Like presentation mode?

Maybe Caffeine is what you looking for. "A status bar application able to temporarily prevent the activation of both the screensaver and the "sleep" powersaving mode." 
[https://launchpad.net/caffeine](https://launchpad.net/caffeine)


Caffeine in Lucid Lynx Howto:
[http://www.liberiangeek.net/2010/07/temporary-prevent-screensaver-powersaving-mode-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/temporary-prevent-screensaver-powersaving-mode-ubuntu-10-04-lucid-lynx/)


I use it on Xubuntu 10.04 for flash movies and presentation. Works fine...

---

### Post by RikoW on 2010-09-17
Of course, I could disable them by hand, but I wanted something a bit more convenient (and quicker).

It seems like caffeine is exactly what I was looking for. Particularly useful is the the feature that you can specify programs upon which it should react.

Let's see how it will behave in real life :)

Thanks for the tip,

               Riko

---

### Post by scorchgeek on 2010-09-17
There's actually a nice GNOME panel app called "Inhibit Applet" that does exactly that--just click on the icon and power-save and screensaver is blocked. It doesn't provide quite the level of control Caffeine does, but it's right there and works great if you just want to keep the monitor on for twenty minutes.

---

