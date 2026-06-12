---
title: "Font problems"
date: 2006-02-05
forum: Desktop Environments
---

### Post by pbb on 2006-02-05
I've been messing around with the Font Properties dialog, and now I can't get my Application Font setting to be obeyed by most programs!

The settings for Desktop Font, Window Title Font and Terminal Font are obeyed, but the setting for Application Font seems only to be obeyed by Synaptic applications (like Synaptic and Add Applications) and Mozilla programs (Firefox, Thunderbird). ALL other programs seem to stick to Sans 12 for some reason.

See the enclosed screenshot. I've set everything to Chancery 8 just to make the difference obvious. I can live with Application Font being fixed to Sans, but 12pt is just far too big for me.

Can anybody tell me why my applications aren't accepting the value for Application Font? I believe they used to in the beginning.

---

### Post by pbb on 2006-02-05
bump...

---

### Post by cdhotfire on 2006-02-05
For the size, go to "Details", font and lower the "Resolution".

For the other problem try doing in terminal
```

$ sudo dpkg-reconfigure fontconfig

```

Select Autohinter and Automatic.  Then maybe try rebooting.  I dont know how else to fix this. :(

---

### Post by pbb on 2006-02-06
Okay, I've found the solution, but this seems like a bug to me!

When both Ubuntu (Gnome) and Kubuntu (KDE) are installed, then the Application Fonts in Gnome don't listen to the setting made in the Gnome Font Properties window, they only listen to the settings in the KDE GTK Styles window!!! So, to change your font settings in Gnome, you actually have to boot into KDE...

This seems like a bug to me... I don't know if anybody who has both Ubuntu and Kubuntu installed, can replicate the problem? And where should I report a bug like this?

---

### Post by cdhotfire on 2006-02-06
Ah, I see.  I don't think its a bug. Go to KDE and go to the Control Panel, there is some option for all GTK applications to use KDE font.  Ive had this problem before, I just wasn't aware that you had both installed.

---

### Post by pbb on 2006-02-06
I didn't realize also having KDE was a mentionable aspect ;-)
But, isn't it a bug that when KDE is installed, I can't use Gnome anymore to change the fontsizes in Gnome ???

---

### Post by cdhotfire on 2006-02-06
[QUOTE=pbb]I didn't realize also having KDE was a mentionable aspect ;-)
But, isn't it a bug that when KDE is installed, I can't use Gnome anymore to change the fontsizes in Gnome ???[/QUOTE]

You can, but you must uncheck in KDE settings the option that allows KDE to use its fonts on GTK applications.  Im not able to tell you excatly where to find it, because I currently do not have KDE installed, and would not like to install it for only this purpose :( .  But I guess it might be consired a bug. Go here:

[https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

Good luck with that. :)

---

### Post by ShanghaiTeej on 2006-02-14
I have this same problem.  I installed kubuntu-desktop alongside my ubuntu installation and KDE has really screwed up my fonts in gnome.  It seems to be permanent, because there is nothing I can do to change it.

---

### Post by pbb on 2006-02-16
I can not get into my Linux machine anymore at the moment (the PSU broke down), but I believe I got to a point where the fonts looked right in both Gnome and KDE.
The key to the solution is setting the DPI value right, using the DisplaySize parameter in xorg.conf. I can't help much further at the moment since I can't boot my own machine, but an internet search will probably bring up some usefull information.

One additional point I remember, is that Firefox (1.5) didn't seem to follow the set DPI value, even though Thunderbird did. Firefox needed to be set to the right DPI in it's Content > Fonts > Advanced configuration.

See also: [http://www.mozilla.org/unix/dpi.html](http://www.mozilla.org/unix/dpi.html)

---

### Post by ShanghaiTeej on 2006-02-16
Thanks, I'm reinstalling Kubuntu to give it another go, and I know I'll run into this problem again.

---

