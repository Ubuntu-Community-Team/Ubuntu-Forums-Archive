---
title: "Potential for transparency?"
date: 2009-10-24
forum: Desktop Environments
---

### Post by dbowlin17 on 2009-10-24
I recently installed ubuntu, so i am rather new to this all. I was able to make the top and bottom bar be semi transparent to give it a more modern touch. However I am looking to do that to the menu bars on my windows. Is that possible? Please keep in mind, i have very limited programming skills (next to none).

---

### Post by MelDJ on 2009-10-24
right click the panel and press properties
then press the background tab. then slide the style to how opaque or transparent you want the panel to be

---

### Post by dbowlin17 on 2009-10-25
ah, i see that. thank you. but I am talking about the window, so I want to make it be semi transparent where it says ubuntu forums - reply to topic - mozilla firefox and where it has the minimize, maximize, and close buttons. I don't know it if it possible, but i would like to find out.

---

### Post by Nate8nate on 2009-10-25
I think you that you may need to use a different theme if you want the title bar partially transparent.

[Gnome-Look]("http://www.gnome-look.org") is a good resource.  

The title bar is drawn by Metacity, and the buttons and such inside windows are GTK.

To install a theme open System -> Preferences -> Appearance and drag the downloaded _____.tar.gz to the Appearance window.

---

### Post by twright on 2009-10-25
If you install the now rather outdated emerald theme manager you will have the option to do this and more.

---

### Post by MelDJ on 2009-10-26
> **twright said:**
> If you install the now rather outdated emerald theme manager you will have the option to do this and more.

+1 
change the opacity of your window to 0

---

### Post by mcduck on 2009-10-26
> **dbowlin17 said:**
> ah, i see that. thank you. but I am talking about the window, so I want to make it be semi transparent where it says ubuntu forums - reply to topic - mozilla firefox and where it has the minimize, maximize, and close buttons. I don't know it if it possible, but i would like to find out.

IF you have Visual Effects enabled, and you are using Metacity themes for your windows (the default in Ubuntu, not Emerald), you can control the window border transaprency with gcnf-editor. To some level, at least.

Press Alt-F2 and runn"gconf-editor". THen use that to browse to apps/gwd, and you'll find options to enable active/inactive window opacity, and for controlling the opacity levels for both. If you want a window manager/decorator with themes that are actually intended for transparency, you'll have to install Emerald and use that instead of Metacity/GWD.

---

### Post by kaboyish on 2009-10-26
maybe this could help. if you have compiz, go to the settings and click the accessibility settings from the menu. you'll get an option called opacify. check it and go to its settings.under the misc. option, there is a bar for passive opacity. you can choose the level of opacity you want. 
by the way, to activate opacity, press the "super key + o"

---

