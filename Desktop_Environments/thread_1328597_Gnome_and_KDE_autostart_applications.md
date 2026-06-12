---
title: "Gnome and KDE autostart applications"
date: 2009-11-16
forum: Desktop Environments
---

### Post by Arlanthir on 2009-11-16
Hello,

I decided to try KDE so I installed kubuntu-desktop on my Ubuntu machine. I chose to keep GDM for now, and started tweaking KDE to my taste.

I use Gnome-do a lot, so I had it autostarting on gnome, but it seems that for some reason (even if I remove it from the autostart in KDE) it keeps starting, so I wrote a small script that checks if the $DESKTOP_SESSION is gnome and, if it is, runs gnome-do.

That solved the problem, but now **I'm suspecting other gnome applications are autostarting in KDE**, when they shouldn't because they're gnome-centric (and I want to use the K replacements).

The most annoying one is Nautilus! It not only keeps drawing the desktop below Plasma, as it mounts all my media automatically, not letting Dolphin unmount it. Plus, it prompts the gnome dialog for autoplay for every device I plug in.

I think I'm not the only one trying the two DE's together, so, why is this still difficult to do!? Does anyone have a solution for this?

**Edit**: K applications are autostarting in gnome too... Argh!

**Edit2**: Found this: [http://better-linux.blogspot.com/2009/03/prevent-gnome-apps-autostart-in-kde-or.html](http://better-linux.blogspot.com/2009/03/prevent-gnome-apps-autostart-in-kde-or.html)
KDE ones seem to hang out on /usr/share/autostart too.

---

### Post by F*disk on 2009-11-16
That website you found has the simplest solution I know of.  Just add the line OnlyShowIn=GNOME; or OnlyShowIn=KDE; in those .desktop files.  Other than that there are probably ways to configure your path so different environments use different directories, but unless you are planning to frequently change the apps that autostart, this is the quickest fix (that I know of).

---

### Post by Arlanthir on 2009-11-16
> **F*disk said:**
> That website you found has the simplest solution I know of.  Just add the line OnlyShowIn=GNOME; or OnlyShowIn=KDE; in those .desktop files.  Other than that there are probably ways to configure your path so different environments use different directories, but unless you are planning to frequently change the apps that autostart, this is the quickest fix (that I know of).

Thanks for the input :)
I can't find the autostart for nautilus, though, where is it?

---

