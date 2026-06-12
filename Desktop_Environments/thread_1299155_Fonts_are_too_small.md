---
title: "Fonts are too small"
date: 2009-10-23
forum: Desktop Environments
---

### Post by johann_p on 2009-10-23
I had to switch to KDE recently because GNOME frequently locks up when I start an application from the panel.

Now, with KDE this does not happen, but for some reason, the fonts in applications like Firefox, Netbeans, Eclipse etc are totally differently sized than in GNOME, and usually much worse.

For example, in Netbeans the fonts for the menu and other GUI elements are so tiny I barely can read them. The editor content can be adapted in the options (I had to set font size to 16 which is crazy).
On the other hand, Firefox has menu and GUI fonts that are too big, but the fonts from websites are way too small and I need to to use extreme zoom.

This all looks as if KDE would report totally wrong screen DPIs to the applications and/or the applcations do not correctly deal with the DPI settings (but the same applications work fine with GNOME).

Changing the settings in the system settings has an impact on some apps and not on others. In some cases an undesired impact, e.g. when I set the font size so large that I can read things in some apps, the calendar widget gets all messed up with the days breaking out of the widget frame.

This is rather unsatisfactory and since both GNOME and KDE are nearly unusable for mea (for different reasons) I wonder if there is any alternative you could recommend? I just want to use my applications without any screen lockups or unreadable fonts!

---

### Post by CRAY-4 on 2009-10-23
well if i were u i would just upgrade to ubuntu 9.10(gnome), often switching from gnome to kde besides a clean install will give you problems

---

### Post by johann_p on 2009-10-23
> **CRAY-4 said:**
> well if i were u i would just upgrade to ubuntu 9.10(gnome), often switching from gnome to kde besides a clean install will give you problems

To be honest I am extremely reluctant to do this as I need my computer for work and 9.10 is not released yet. When I upgraded to 9.04 and 8.10 (and before) I had issues every time (usually with some of the packages that are not that popular bit which I need) although I did those upgrades several weeks *after* the release each time. 

I am  rather frustrated by this, I have to say. It is no fun to have your sceeen locked up when you are in the middle of working on project with several dozen windows open. It is no fun to have to look at the screen from 2 inches away to be able to read the stuff that is shown there.

I'd really give up all the fancy screen effects, widgets, gadgets, lovely looks and what have you for just a stable and usable window manager which is capable to show any 12 point font exactly 12 points big.

---

### Post by Zorael on 2009-10-24
KDE apps will listen to KDE's own configuration for font settings, which you can toggle in System Settings -> Appearance -> Fonts. Perhaps a dpi needs to be enforced there, if fonts are too large across the board.

Also make sure to go to GTK+ Appearance (in the same section of systemsettings) and set it to "Use my KDE fonts in GTK+ applications". I think the package you need if you don't have this entry is kde-style-qtcurve (and perhaps kwin-style-qtcurve).

Finally, see if you have a **~/.fonts.conf** file that defines any fonts to be used for the virtual fonts serif, sans-serif and monospace. Rename the file and restart any GTK app to see if it helped.

---

### Post by kerry_s on 2009-10-24
grab lxapperance to set the gtk programs settings, it uses a gtktrc file so should work in kde.

---

### Post by johann_p on 2009-10-25
I have been doing all of this, and it is possible to change the font sizes for some things by various methods. 
However, there seems to be no way to generally make the fonts shown for webpages larger in firefox. Oddly, the same webpages look better under GNOME! I can change the menu and dialog fonts indirectly though the KDE font settings but not the fonts displayed in the page. 
It is the other way round with Netbeans: there the menu and gui fonts are too small in KDE but ok in GNOME and again, there does not seem to be a way to change them. 
Also one can only "overwrite" the DPIs in the font settings to 90 and 120, not to my actual value (or measure the value). 

Font sizing is not optimal under GNOME either but still much better and not so extremely unusable as in KDE. Especially the Netbeans problem is serious -- with such small GUI fonts, it is impossible to work. 

I am grudgingly had to go back to GNOME again and live with the occasional locked screens. 

I even tried icewm but there, i could not even get the wireless going as it is done with some magic in KDE & GNOME and I would not know which program to start to do it manually.

---

### Post by larytet on 2009-11-18
How to fix fonts in the Firefox menus and on the tabs. This advice mainly targets users with eyes problems. LCD screens require to use the native resolution to get the sharp picture. One of the simplest way to enlarge picture is to use more dots per inch for all fonts. 

Open page *about:config*. Find *layout.css.dpi* and set value to zero (default is -1). From this point Firefox will use system default font size. Now in the *System/Preference/Appearance* click Fonts tab and Details. Set font size to something like 150. Restart Firefox. Finally in the *Firefox preference/Content/Advanced* change default font size and minimal font size

---

