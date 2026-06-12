---
title: "Theming problems on Unity (Trusty)"
date: 2015-06-19
forum: Desktop Environments
---

### Post by silex89 on 2015-06-19
Hi all. I have a problem with the theming of my Unity desktop.

A few days ago, I accidentally shutdown my laptop incorrectly (I was shutting down Ubuntu and I unplugged the power supply before it was done and I did not notice that I was without the battery). I used to have the Numix's project GTK and icon themes in my desktop, but when I logged back in Unity reverted back to the default set of icons and GTK+ theme. I noticed the fonts also changed, the Ubuntu font was not being used, I think it is the Gnome default font (see the screenshot of the search field in the dash).
[ATTACH=CONFIG]262717[/ATTACH]

The thing is that I tried to go back to the Numix GTK+ and icon themes but the Tweak Tool does not work. I tried then to reinstall everything using 'apt-get install --reinstall numix-icon-theme-circle' and I got this output.

```
Preparing to unpack .../numix-icon-theme-circle_1.0.2+3~201502071451~ubuntu14.04.1_all.deb ...
Unpacking numix-icon-theme-circle (1.0.2+3~201502071451~ubuntu14.04.1) over (1.0.2+3~201502071451~ubuntu14.04.1) ...
gtk-update-icon-cache-3.0: The generated cache was invalid.
WARNING: icon cache generation failed for /usr/share/icons/Numix-Circle
gtk-update-icon-cache-3.0: The generated cache was invalid.
WARNING: icon cache generation failed for /usr/share/icons/Numix-Circle-Light
Configurando numix-icon-theme-circle (1.0.2+3~201502071451~ubuntu14.04.1) ...
gtk-update-icon-cache: The generated cache was invalid.

```

Can you give me some hint to correct this?

Thank you in advance! :D

---

### Post by RobGoss on 2015-06-21
Hello and welcome, do you have a restore disk or USB, you can use sometimes this is a better fix and much faster.

I don't think unplugging the machine would effect your themes settings at least I have never encountered this

This also might help you to fix the problem, [http://www.webupd8.org/2013/08/new-ppa-for-numix-gtk-and-icon-themes.html](http://www.webupd8.org/2013/08/new-ppa-for-numix-gtk-and-icon-themes.html)

---

### Post by steveo314 on 2015-06-26
> **silex89 said:**
> Hi all. I have a problem with the theming of my Unity desktop.

A few days ago, I accidentally shutdown my laptop incorrectly (I was shutting down Ubuntu and I unplugged the power supply before it was done and I did not notice that I was without the battery). I used to have the Numix's project GTK and icon themes in my desktop, but when I logged back in Unity reverted back to the default set of icons and GTK+ theme. I noticed the fonts also changed, the Ubuntu font was not being used, I think it is the Gnome default font (see the screenshot of the search field in the dash).
[ATTACH=CONFIG]262717[/ATTACH]

The thing is that I tried to go back to the Numix GTK+ and icon themes but the Tweak Tool does not work. I tried then to reinstall everything using 'apt-get install --reinstall numix-icon-theme-circle' and I got this output.

```
Preparing to unpack .../numix-icon-theme-circle_1.0.2+3~201502071451~ubuntu14.04.1_all.deb ...
Unpacking numix-icon-theme-circle (1.0.2+3~201502071451~ubuntu14.04.1) over (1.0.2+3~201502071451~ubuntu14.04.1) ...
gtk-update-icon-cache-3.0: The generated cache was invalid.
WARNING: icon cache generation failed for /usr/share/icons/Numix-Circle
gtk-update-icon-cache-3.0: The generated cache was invalid.
WARNING: icon cache generation failed for /usr/share/icons/Numix-Circle-Light
Configurando numix-icon-theme-circle (1.0.2+3~201502071451~ubuntu14.04.1) ...
gtk-update-icon-cache: The generated cache was invalid.

```

Can you give me some hint to correct this?

Thank you in advance! :D


try this in a terminal:
gtk-update-icon-cache -f /usr/share/icons/hicolor

and then try this:
apt-get install --reinstall numix-icon-theme-circle

---

