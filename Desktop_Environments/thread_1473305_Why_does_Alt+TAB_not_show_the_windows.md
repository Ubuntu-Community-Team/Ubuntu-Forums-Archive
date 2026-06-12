---
title: "Why does Alt+TAB not show the windows?"
date: 2010-05-05
forum: Desktop Environments
---

### Post by barna on 2010-05-05
Hi,
After upgrading to 10.04, the Alt+TAB walking through windows has changed behaviour. It does not anymore show the windows themselves as I walk through them, whatever I set under Navigate Through Windows/Effect (No effect, Box switch, Present windows, Cover switch, Flip switch).
I want the old behaviour back!
Thanks

---

### Post by Zorael on 2010-05-05
Do you have compositing enabled? If disabled it will only show a vertical list no matter what your setting is.

---

### Post by barna on 2010-05-05
Thanks a lot, that was it. 
It is very scenic, although I am wondering why this terrible overhead and unnecessary scenery is needed to make this simple task. I was very happy with the old way, without any 3D effects, where compositing and other similar things were not needed. 
Thanks again.

---

### Post by barna on 2010-05-05
I am wondering if it is possible to make the summary box from the 'Box switch' mode disappear...

Another question: after enabling the compositing, my taskbar (or panel, or whatever it is called recently) got slightly transparent. How can I disable transparency of it?

Thanks

---

### Post by shihkster1015 on 2010-05-05
you can right click on the taskbar and go to properties. Then go to the background tab and there should be a slider for transparency

---

### Post by barna on 2010-05-05
I don't seem to have these options. Right-clicking on the panel, I have Panel Options, below which I have 
- Add Widgets
- Add Panel
- Lock Widgets
- Panel Settings
- Remove this panel

Under Panel Settings there is also nothing like background.
Thanks

---

### Post by shihkster1015 on 2010-05-05
sorry mate 
i was refering to the GNOME interface
maybe you might wanna give that a go!
i think GNOME's much easier to use compared to KDE

---

### Post by Zorael on 2010-05-06
> **barna said:**
> I am wondering if it is possible to make the summary box from the 'Box switch' mode disappear...
The plugins themselves have very limited configurability. If there isn't a wrench icon next to the box switch plugin in the plugin list, I don't think you can disable it without modifying the source itself.

> **barna said:**
> Another question: after enabling the compositing, my taskbar (or panel, or whatever it is called recently) got slightly transparent. How can I disable transparency of it?
Transparency is handled by the panel theme, so it's up to the theme designed to decide how transparent it should be. I don't like the decision, but that's how it currently works, at least. The workaround is to use the Aya panel theme, which is opaque-ish. It will also inherit the colors you have set your windows up to use (in Appearance -> Colors), so it should fit well regardless of if you have a dark or a bright look. The Aya theme is in the **plasma-desktopthemes-artwork** package.

Open up System Settings -> Advanced tab -> Desktop Theme Details, select the base theme you want, make your changes (change the panel theme to Aya) and apply. Your new theme will be saved as "(Customized)", and it may apply immediately depending on your settings. If it doesn't, go to Appearance -> Style -> Workspace tab and pick (Customized) there.

---

### Post by kid1000002000 on 2010-05-09
make sure to mark as "solved" if your thread problem got fixed!

---

