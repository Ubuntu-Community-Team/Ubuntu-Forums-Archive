---
title: "KDE Window DECORS! Can't INSTALL. :("
date: 2009-07-12
forum: Desktop Environments
---

### Post by JK3mp on 2009-07-12
Alright. So i was normally using Ubuntu 9.04 on this machine, decided to install KDE4 onto it to give it a shot.Looks all good, not speedy but i didn't expect it too be. Now i apply themes from KDE-look.org BUT the panel changes and widgets change, but the windows decor stay the same...i looked around a little and seen that Kwin was the window manager for KDE, well i found windows in configuration but no Kwin nor anything to install window themes...any help appreciated, thanks in advance.

---

### Post by benerivo on 2009-07-12
Try```
apt-cache search kwin
``` to see what decorations are available from the repositories. I don't think that they are easily installable directly from the desktop, or from kde-look downloads, in the same way plasma themes are.

---

### Post by Pziko on 2009-07-12
Currently I'm mucking about with KDE4, and I ran into the same thing... The window options were just sort of "bleh". You might consider installing Enlightenment (E16) as a replacement. I've found it to be a little quirky but that's mostly just my own lack of familiarity with the KDE desktop and using it with other window managers.

If you use Adept or SPM, search for and install Enlightenment. Some of the theme repositories have vanished, so here is a link I've found that has a reasonable selction: 

[http://themes.effx.us/packages/e16/](http://themes.effx.us/packages/e16/)

There's no screenshots, but they're small packages, so I just downloaded them all and tried out which ones I liked then removed the ones I didn't.

Download them someplace where can find them easily, then move them to the E16 themes directory:

/usr/share/e16/themes/

As I said, I'm still tinkering so this is what I've been doing: Log out of KDE. Use the options button at the log in to choose e16 as your session. You'll log in just to the Enlightenemt desktop, which can be a little confusing, but if you goof about you'll get the hang of it. If you have a keyboard with a Windows key, click that and click on your desktop. You'll have a pop up menu with "Themes". Find a theme you like. Left click on the desktop and I think that's the menu that will have an option for logging out.

From the log in screen again, options, there might be an option that says "e16-KDE" or something along those lines. When KDE starts, you'll now have Enlightenment as your window manager.

The quirks I've been running into are pretty simple. For one thing, I can't find a way to use the e16 menus to change my theme while in KDE. Clicking on the desktop or anywhere else gets you the KDE menus, of course. So in order to change themes I've had to log out and switch sessions. Also, e16's desktop pagers randomly change sizes on me. But other than that, I am really enjoying it as an addon to KDE.

---

### Post by izizzle on 2009-07-13
Ummm what? Plasma themes don't modify your window decorations at all. For window decorations you need to use something like DeKorator or Bespin, both of which are available in the repos.

---

### Post by Pziko on 2009-07-15
> **izizzle said:**
> Ummm what? Plasma themes don't modify your window decorations at all. For window decorations you need to use something like DeKorator or Bespin, both of which are available in the repos.

Ahh, my apologies. Much of this is pretty much new to me as well. 

I believe he may be looking for System Settings > Appearance > Style?

---

### Post by ssri on 2009-07-15
To change windows decor, go to:

System Settings -> Appearance -> Windows (Windows Decoration tab)

Look under windows decorations in kde-look for other packages.

I highly recommend dekorator (plus a number of dekorator themes) and bespin...

---

