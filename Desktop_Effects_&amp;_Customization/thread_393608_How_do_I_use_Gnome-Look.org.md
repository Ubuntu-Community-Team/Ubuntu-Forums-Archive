---
title: "How do I use Gnome-Look.org?"
date: 2007-03-25
forum: Desktop Effects &amp; Customization
---

### Post by Sean K on 2007-03-25
I'm a recent convert from Windows, and if there's ONE thing about Linux that doesn't sit well with me, it's how everything is so "Do It Yourself." I'm a fan of doing things on my own, but only when I have someplace to learn from. The Gnome-Look.org website has absolutely no documentation, no help, nothing.

Anyway, this isn't about what I don't like about Linux. I'm actually quite happy with the OS. My question is, how do I use this site? Often times there are multiple download links. Which one do I click? Which category do I download from? What is included in that download? Will it look like the screenshot?

Just, somebody, how do I skin Linux?

Thanks in advance.

---

### Post by Matt Yun on 2007-03-25
Download a theme from gnome-look.org.  If you want to "skin" Gnome, then download a GTK 2.x theme.

Go to the System menu -> Preferences -> Themes

Click the "Install Themes" button, and select the theme you just downloaded.

Caveat:  some of the themes on gnome-look.org require you to manually install them.  Just forget about these for now, and play with the ones that work with the Ubuntu themes tool.

I personally use [T-ish]("http://www.gnome-look.org/content/show.php/T-ish+Pack?content=30859").

---

### Post by Sean K on 2007-03-25
How do I know which require manual installation? For instance, I just tried this one: [http://www.gnome-look.org/content/show.php/Frozen+Plastic+Suite?content=44781](http://www.gnome-look.org/content/show.php/Frozen+Plastic+Suite?content=44781)

No luck with that one. Which file do I use when I open up the theme manager?

---

### Post by reclusivemonkey on 2007-03-26
> **Sean K said:**
> I'm a recent convert from Windows, and if there's ONE thing about Linux that doesn't sit well with me, it's how everything is so "Do It Yourself." I'm a fan of doing things on my own, but only when I have someplace to learn from. The Gnome-Look.org website has absolutely no documentation, no help, nothing.

Anyway, this isn't about what I don't like about Linux. I'm actually quite happy with the OS. My question is, how do I use this site? Often times there are multiple download links. Which one do I click? Which category do I download from? What is included in that download? Will it look like the screenshot?

Just, somebody, how do I skin Linux?



If you are struggling with this, there are some packages in the repos that will help. I am at work right now so I can't look, but I will post again when I get back home.

Usually, all you have to do with a GTK/Metacity/Icon package from Gnome-look is drag it to the theme preferences dialog box and it installs. YMMV

---

### Post by reclusivemonkey on 2007-03-26
[http://www.miketech.net/gnome-art/](http://www.miketech.net/gnome-art/)

Thats available in the repos. This thread may help you as well;

[http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093)

---

### Post by coolen on 2007-03-31
The download links will usually be fairly explanatory. For wallpapers, for example, the links might be for different sizes, or perhaps slight variations. There's no way to be sure, though. It's up to the user.
You'll usually download an archive (tar.gz or similar). You can either install it as stated above, or if you want it installed as a global theme for all users, open the archive as root and extract to /usr/share/themes (for GTK and metacity themes) or /usr/share/icons (for icon and cursor themes). They should appear in your Theme Details window the next time you open it.
Wallpapers are just opened straight from the Desktop Background window, although you may have to unpack an archive first if it's part of a set.

The download link will sometimes point you to another site, from which you can download the theme, and likely many more.

Oh, one tip: if sometimes when using the "Install theme" method, it might say it's an invalid archive (or something similar). It might be the case that the archive contains more than one theme...extract it, and try to install the contents (either directories or more archives) individually.

---

### Post by mcduck on 2007-03-31
> **Sean K said:**
> How do I know which require manual installation? For instance, I just tried this one: [http://www.gnome-look.org/content/show.php/Frozen+Plastic+Suite?content=44781](http://www.gnome-look.org/content/show.php/Frozen+Plastic+Suite?content=44781)

No luck with that one. Which file do I use when I open up the theme manager?

If there's more than one theme or color variation included you need to use manual install (and that's as easy as extracting the files to ~/.themes).

May themes use pixmap images, you need to install the 'gtk2-engines-pixbuf'-package for them to work correctly. Also some themes may require some other theme engine, for example Rezlooks and Murrina..

In the end it's all very simple, at least compared to using themes in WinXP ;)

---

### Post by coolen on 2007-03-31
Agreed. Someone using XP with a non-standard theme is a power user. Someone using Linux with their distro's default theme is a newbie.
It's what we love about it: we may have to do a bit more work sometimes, but in the end, our desktop is ours. Our desktops say as much about us as our CD collections.

---

