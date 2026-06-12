---
title: "Font Unsmooth"
date: 2011-06-06
forum: Desktop Environments
---

### Post by akung on 2011-06-06
I'am Maverick user,,,

After installing kde desktop my font in LibreOffice, Chrome, and some application goes to umsmooth and broken.

This is the preview [IMG]https://lh6.googleusercontent.com/-xe2cWMSRXI0/TexIyrvPjcI/AAAAAAAAAl4/pNJWm8O5jy0/pecah.png[/IMG]

But if I creat a new user, fonts are normal

Please help me to fix this... Thanks

---

### Post by Copper Bezel on 2011-06-06
Now, I'm assuming that the unsmoothed font only happens in Gnome? If that's the case, the simplest thing would be to install qt4-qtconfig and run it from Preferences. It'll allow you to set font smoothing for Qt apps (and in this case font rendering) under Gnome. If your font smoothing in those apps *everywhere* is unsmoothed, then check that you have hinting turned on in KDE's System Settings -> Application Appearance -> Fonts (Scroll to the bottom, "Enable" antialiasing, and click "Configure" for details.)

---

### Post by akung on 2011-06-06
> **Copper Bezel said:**
> Now, I'm assuming that the unsmoothed font only happens in Gnome? If that's the case, the simplest thing would be to install qt4-qtconfig and run it from Preferences. It'll allow you to set font smoothing for Qt apps (and in this case font rendering) under Gnome. If your font smoothing in those apps *everywhere* is unsmoothed, then check that you have hinting turned on in KDE's System Settings -> Application Appearance -> Fonts (Scroll to the bottom, "Enable" antialiasing, and click "Configure" for details.)

Yes,,, I'm Gnome user,,, I forgot to say it...

I have been installing qtconfig,,, but I could'nt find where the button is?

Thaks for ur help :)

---

### Post by Copper Bezel on 2011-06-07
Button? Oh - I don't actually see font smoothing in qtconfig, now that I check it again. I could have *sworn* that was in there. Have you tried running systemsettings under Gnome and setting it there?

[img]http://dl.dropbox.com/u/17749392/Screenshots/systemsettings-font.png[/img]

---

### Post by akung on 2011-11-10
Yeach,,, it seems I have been installed Kubuntu Desktop.. Now its fixed...
Thank you very much

---

