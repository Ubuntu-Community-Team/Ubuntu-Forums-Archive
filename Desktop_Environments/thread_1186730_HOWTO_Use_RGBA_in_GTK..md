---
title: "HOWTO: Use RGBA in GTK."
date: 2009-06-13
forum: Desktop Environments
---

### Post by damis648 on 2009-06-13
Through some random boredom, I decided to make an easy and simple installer to getting all GTK applications and engines to use RGBA, mainly for those who do not yet find themselves not yet adept enough to do it themselves. The RGBA colormap basically allows the interior of windows to set an alpha value, and thereby achieve Vista-like transparency effects that go beyond the window borders. (See screenshots)

This is basically just an installer to automatically install [this]("http://gnome-look.org/content/show.php/RGBA+Gtk%2B+module?content=100556") and configure it, as well as install a patched nautilus and provide a utility to enable/disable/manage RGBA. Just download the attached archive, CD into the folder, and install.
```
cd /path/to/downloaded/folder
./setup.sh --install
```
Then log out and back in for Vista-like effects. :popcorn:
Some applications cannot support RGBA, however, and will crash on startup. I have included in the controller application a quick command that can be used to restrict applications from using RGBA, and it can also easily enable/disable RGBA like so:
```
rgbacontrol --enable
rgbacontrol --disable
rgbacontrol --restrict pidgin
```
where pidgin is an example of an application you might want to prevent from using an RGBA colormap because it crashes on startup.

The theme used in the screenshots is ThinIce, complimented by my own custom emerald theme. Post if you would like me to uplaod it.

I hope this comes in handy for someone.:popcorn:

[DOWNLOAD LINK]("http://www.mediafire.com/download.php?zjjn0zizmwq")

---

### Post by Kreisverkehr on 2009-06-16
Thanks for your skipt, this is exactly what i was looking for.
But are your *.deb pakages aviable for my amd64 architeckture?

please let me know

Kreisverkehr

---

### Post by Psimon on 2009-11-02
Is there another link to download the archive? I get an error page.

Thanks.

---

