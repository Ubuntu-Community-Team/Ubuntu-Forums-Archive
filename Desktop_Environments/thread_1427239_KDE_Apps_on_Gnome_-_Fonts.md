---
title: "KDE Apps on Gnome - Fonts"
date: 2010-03-11
forum: Desktop Environments
---

### Post by hhh on 2010-03-11
A picture is worth a thousand words (click for full-size)...

[[img]http://omploader.org/tM3N2Mg[/img]](http://omploader.org/vM3N2Mg)

The pic shows PcManFM behaving as it should, VLC inheriting the GTK theme but with ugly font rendering (I installed and then removed qGTKStyle as it didn't change font rendering for me, but it seems my settings persisted) and UNetbootin looking just plain ugly.

I can't remember VLC looking like that in previous Ubuntu systems I've had though, so I'm wondering if it's something I've done to my font configuration. Ideas, anyone?

---

### Post by hhh on 2010-03-11
Well, I've solved my problem, but the solution makes so little sense that I hesitate to post it. I based it on the last comment from this blog post...
[http://thedarkmaster.wordpress.com/2007/07/03/kde-applications-looking-bad-in-gnome-lets-fix-em-up/](http://thedarkmaster.wordpress.com/2007/07/03/kde-applications-looking-bad-in-gnome-lets-fix-em-up/)

I installed systemsettings. I ran gksu sytemsettings and set appearance to gtk+ and fonts to DejaVu Sans/DejaVu Sans Bold/DejaVu Sans Mono 8px (all other pix sizes looked jagged). I set antialiasing on and hinting at slight. I saved the settings. I did the same without root privileges. I uininstalled/purged systemsettings. I rebooted. Everything looks as it should (UNetBootin has a grey background because it's running with root privileges). Here's the screenshot, this time I'm in my Openbox session...

[[img]http://omploader.org/tM3QyZA[/img]](http://omploader.org/vM3QyZA)

Hey, it's working, screw knowing why. Linux, my OS of choice, whatever.

---

