---
title: "[SOLVED] Nuvola Theme in Hardy Ubuntu Broken?"
date: 2008-06-13
forum: Desktop Environments
---

### Post by SabreWolfy on 2008-06-13
Hi guys,

I came across the beautiful Nuvola theme today (pictures [here]("http://en.wikipedia.org/wiki/Nuvola")). I see this theme is available in the gnome-themes-extras package apparently. There is mention of gtk-engine-nuvola in the package description, but no mention of Nuvola in the list of themes in this package. After installing this package, I could not find Nuvola anywhere. I searched for any file called "nuvola", which also turned up nothing. Some posts on the 'net I found indicate that some people have managed to install this theme and get it working. What am I doing wrong? I'm using Hardy Ubuntu.

Thanks.

SabreWolfy.

---

### Post by soccerboy on 2008-06-13
Have you tried to download the theme from [www.gnome-look.org](www.gnome-look.org) or the kde equivalent and install it from the System>Preference>Appearance gui?

---

### Post by SabreWolfy on 2008-06-13
Thanks. I looked around at GNOME-look for Nuvola, but none of them really looked like the ones I posted in the link in my first post. The closest was the Olive one which I downloaded and installed, but the icons don't change. The screenshot shows different icons, but I can't seem to get my icons to change. Any ideas?

---

### Post by soccerboy on 2008-06-13
What you have to do is go into System>Preferences>Appearance.  Click on your theme you want, click Customize.  Then go the Icon tab and install your icon theme that you want.  That should change icons to your liking.  btw did you search gnome-look for gtk themes or icon themes.  Seems like Nuvola is an icon theme only.  You probably have to apply it your current window theme.

---

### Post by SabreWolfy on 2008-06-13
There were no icon themes. The Olive one I downloaded was a tiny file that just changed the colours slightly and modified a few of the widgets.

The package downloaded from *apt* (4.4MB) as mentioned in my first post, which is a .deb file, did not appear to contain any Nuvola files. However, there is a different file (6.4MB), with a very similar name, referred to on the Wikipedia Nuvola page (see first post), from gnome.org, which I have downloaded. This is a normal tar.gz file and has folders for Nuvola with icons in them. It seems to be a collection of themes which need to be compiled locally.

---

### Post by soccerboy on 2008-06-13
Compiling themes is beyond my knowledge.  You could try to see if some other website has Nuvola for gnome.  I found it for kde if you use that on kde-look.org

---

### Post by SabreWolfy on 2008-06-13
Yes, the instructions to compile in README were wrong and the ones in INSTALL are giving me errors. How complicated can it be to install a few icons? Hehehe! I'll post here again if I manage to get it installed. Thanks for your suggestions.

---

### Post by SabreWolfy on 2008-06-13
Could not figure out how to compile the theme, as ./configure was needing gtk-engines-2. I did however manage to find a Debian package for the latest gnome-themes-extras-0.9 [here]("http://packages.debian.org/lenny/all/gnome-themes-extras/download"). I'm still not sure why there seem to be two "releases" of these packages: one numbered 0.9 which seems to include Nuvola, and the other (available through the repositories) numbered 2.22.0, which does not include Nuvola.

Upon installation of the package, I was told that newer version is available in the repositories. There was also a link to some screenshots ([here]("http://librsvg.sourceforge.net/theme.php")) showing the themes, including Nuvola. The theme installed without any problems and provided me with Amaranth, Gorilla, Lush, Nuvola and Wasp themes!

[I did expect the icons (for example, the blue folder icon) to be more beautifully rendered, as all the icons are SVG (?)]

Edit: Placing a shortcut for gedit onto the desktop and then stretching the icon did work. The icon was not "pixelated". However, the tiny gedit shortcut icon in a panel did look pixelated.

---

