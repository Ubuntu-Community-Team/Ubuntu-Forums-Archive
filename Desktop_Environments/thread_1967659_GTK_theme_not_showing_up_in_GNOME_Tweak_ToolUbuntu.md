---
title: "GTK theme not showing up in GNOME Tweak Tool/Ubuntu Tweak"
date: 2012-04-28
forum: Desktop Environments
---

### Post by Tornikee on 2012-04-28
Hello, I have three questions regarding themes in GNOME Shell 3.4:

(1) I've put a couple of GTK themes in *.themes* folder, but only 'window theme' field (both in GNOME Tweak Tool and Ubuntu Tweak) shows them, while the 'GTK+ theme' field drop-down list does not contain those (screenshot: [http://bit.ly/KkUo8R](http://bit.ly/KkUo8R)); How can I make those themes (Orta, Orta Squared, Equinox Evolution Dawn) show up in that list?

(2) Switching to 'Hope' or 'Hope Dark Toolbar' theme in 'GTK+ themes' field makes application and folder fonts go white, rendering them invisible on white background. This didn't happen in Ubuntu 11.10/GNOME 3.2. Is there a way to solve this issue?
 
(3) [SOLVED] How can I delete unwanted GNOME Shell/GTK themes? I knew a couple techniques for this, but none of them seem to work in Ubuntu 12.04/GNOME Shell 3.4.

Thanks in advance.

---

### Post by Tornikee on 2012-04-29
Any tips? Guess at least (3) should have easy solution.

---

### Post by ram0s on 2012-04-29
Hi. I've also been breaking my head around this during this weekend, and I've had enough of it. 
Themes can't be installed by copying them through root access to /usr/share/themes. 
They don't show up, and when they do, they don't work correctly like wrong colors and buggy stuff. 

The same goes for custom icons you install in usr/share/icons. 
Install them manually, apply them in gnome tweak/advanced setting/unsettings/wtv and the icons don't show up, instead, default gnome icons are applied. Every guide online is wrong. They will say to simply extract the themes on usr/share/themes and pick them on the application. Doesn't work that way, but I'm already too annoyed to find out.

If the themes and icons, etc are installed through repository, they do work. I managed to install faenza icons and about 2 themes by following youtube guides, which had specific repositories to be added.

These kind of bugs always stain ubuntu for me.

---

### Post by Tornikee on 2012-04-29
Guess these are issues of the new release and will be solved with time, although at least deleting unwanted themes should be possible now.

---

### Post by ram0s on 2012-04-29
I guess you could just delete them using alt f2 to run gksu nautilus for root access?

---

### Post by Tornikee on 2012-04-29
> **ram0s said:**
> I guess you could just delete them using alt f2 to run gksu nautilus for root access?
That enables me to delete themes installed manually, but how can I delete those installed from repositories? Those don't appear in relevant root folders.

---

### Post by ram0s on 2012-04-29
Well, at least from my experience, the only custom themes or icons I managed to install successfully were from repositories (ppa:tiheum/equinox and ppa:webupd8team/themes), and they do show up in /usr/share/themes and /usr/share/icons, as well as the default themes and icon sets.

Now, about them not showing up to be selected or bugging out, while installing manually, I think it might be related to file permissions.. (?) I really don't know, maybe something that can be solved with chown. My linux knowledge is really limited.

---

### Post by Tornikee on 2012-04-29
Did another search, and found the folders. Thanks for the hint.

---

### Post by ram0s on 2012-04-29
Cool, I also made a little progress and managed to correctly apply a custom theme I manually installed (Elements Theme downloaded from gnome-look). 

What I did differently was to use MyUnity to apply it. I had been using Advanced Settings and Unsettings. All of these are available through Ubuntu Software Center.

---

### Post by Frogs Hair on 2012-04-29
For 12.04, make sure the themes are Gnome 3.4 compatible and that the packages manually installed are fully extracted. I just installed two themes that included 3.2 and 3.4 packages and if I hadn't checked folder the themes would not have appeared in advanced settings.

---

### Post by Tornikee on 2012-04-29
Thanks for the tip.

---

