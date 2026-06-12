---
title: "Shrink Window To Title Bar"
date: 2007-09-10
forum: Desktop Environments
---

### Post by hyreia on 2007-09-10
Okay, Google is no help, probably because I don't know exactly what to search for.

I've seen setups where there's an extra icon on the title bar. When it's clicked, the window shrunk down to just the titlebar, minimizing the space it took up. Then just clicking the button again would bring it back to the way it was. You could even get rid of the minimize button and the taskbar and just organize and sort your windows like that.

Apparently if I right-click and change some settings I can make it so if I double-click the titlebar it rolls up. But I don't want that, I want an individual button that can do that.

Can I do that with Gnome and Ubuntu? I'm willing to change to change to different environments and distributions if its easier (as long the ability to have a pretty theme isn't compromised).

So, will anybody help out a first-time Linux forum poster?

---

### Post by swisscow on 2007-09-11
If I follow correctly, what you mean is 'shade' - the window rolls up into the title bar like a blind. On Kubuntu this is enabled by default (right click on title bar - shade). I gnome and I could be outrageously wrong here, I think some themes support this but which ones, I know not.

---

### Post by CowzRule on 2007-09-11
I'm not sure if this is what you want, but with Gnome when you double click the titlebar of a window it will maximize the window by default. You can change it to shade when you double click by going into Preferences - Windows and change the Titlebar Action to Shade.

Also, If you install Beryl or Compiz Fusion along with Emerald, there are some Emerald themes that have an additional button that will shade the window with a single mouse click. Plus with the Emerald Theme Manager you can easily customize the look, colors and position of the whole theme.

I'm sure it's possible to add the extra button to the standard GTK window themes, but I don't know how. I'm sure it would involve modifying the configuration files of the theme.

---

### Post by the yawner on 2007-09-11
On Emerald it is possible to customize the buttons on the window decoration regardless what theme you're using. Just edit the theme and go to tab Titlebar. There's a parameter there called Titlebar Object Layout. On my current Emerald theme it's currently set to *I:T:N(5)X(5)C(3):HI*. And there's a legend there to guide you which buttons can be enabled on the decoration and on which part of the titlebar it should appear. Just be sure you have an image assigned for every button.

I'm not sure if there's any easy way to do that if your using Metacity though.

---

### Post by mcduck on 2007-09-11
Metacity doesn't support any more buttons than what it uses by default. It can shade windoes, but only by double-clicking the title bar.

If you really want a button for it you need to use some other window manager.

---

### Post by hyreia on 2007-09-20
Thanks everyone! You've all been a big help!

---

### Post by mojoman on 2007-09-21
Xfce has this by default as well.

---

