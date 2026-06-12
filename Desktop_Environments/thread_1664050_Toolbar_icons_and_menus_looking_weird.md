---
title: "Toolbar icons and menus looking weird"
date: 2011-01-10
forum: Desktop Environments
---

### Post by *uu on 2011-01-10
Hi all,

for quite a while now I noticed this behavior in the Arora browser, but since I only use it every once in a while for quick testing, it didn't bother me enough -- see first two attached screenshots.

But starting today I noticed the same weird behavior in qbittorrent, and well, that does bug me: The toolbar icons (qbt_toolbar.png, note also the background of the Search tab) and some other UI icons (qbt_options.png) look very weird, like the wrong icon with a wrong scale is being used. Also some menus have a strange icon-like background (qbt_menu.png).

I suppose this has to do with GTK+ icon sets. I already re-installed all gnome icon sets, but to no avail. Does anyone have any suggestions as to what I could do to repair this?

In qbittorrent, this started today after I had some strange dependency issue with the package libtorrent-rasterbar5:

```
E: /var/cache/apt/archives/libtorrent-rasterbar5_0.15.5-0ubuntu1~lucid_amd64.deb: 
trying to overwrite '/usr/lib/libtorrent-rasterbar.so.6.0.0', which is also in 
package libtorrent-rasterbar6 0
```

When trying to resolve this, suddenly qbittorrent (and deluge, as well) appeared not to be installed (both were never removed). I then removed the problematic libtorrent-rasterbar6 package and re-installed qbittorrent, which only depends on libtorrent-rasterbar5, and everything then installed fine -- only qbittorrent having this strange appearance now.

So, any help appreciated. :popcorn: If you need further info, please, let me know.

*uu

P.S.: Sorry if something like this was already asked before -- in the vast amount of threads I couldn't find anything that fits...

---

### Post by *uu on 2011-02-10
By now I'm a few steps closer to solving this issue. I could still need some help, though:

The problem appears to be my icon theme for GNOME. I use the icon theme "OSX-NiX". The applications in question are based on Qt, not GTK+. Appearently, most GNOME icon themes provide icons for Qt applications, as well, or at least some kind of fall-back. This seems to be lacking in the the icon theme I use, and therefore **some** Qt apps seem to miss certain icons. 

I wanna emphasize "some" here, as most Qt or KDE apps don't show these symptoms, and shortly after my original post, also *qbittorrent* got its icons back -- I didn't change any settings, I assume it was repaired when *qbittorrent* was updated once again, or maybe some sort of a local theme hick-up.

As long as I have the icon theme "OSX-NiX" selected, the *arora* browser still misses most of its icons. And also the Open/Save dialogues of *LyX* (a LaTEX based document processor, according to the credits it also uses Qt to some extend) lack most of their toolbar buttons, as I discovered today. When I switch to some other icon theme, there are icons shown in both applications, though, not necessarily the icons of the selected theme.

Am I missing some way of setting the fall-back icons foor my desktop theme? In my theme file [FONT="Courier New"]~/.themes/MyShinobi/index.theme[/FONT] I see:

```
[X-GNOME-Metatheme]
GtkTheme=OSX-NiX
MetacityTheme=Shinobi-menuicon
IconTheme=OSX-NiX
```

The corresponding file [FONT="Courier New"]/usr/share/icons/OSX-NiX/index.theme[/FONT] contains:

```
[Icon Theme]
Name=OSX-NiX
Comment=OSX-NiX
Inherits=gnome, hicolor
Example=x-directory-normal
```

The icon theme "Humanity" has the same *Inherits*, and when I choose that, the icons in the Qt apps in question are fine. So what am I missing here? What do I have to tweak?

Please, anybody? :confused:

*uu

---

### Post by *uu on 2011-02-11
Well, I figured it out by myself -- kind of.

Right after posting my last post, I stumbled upon the thread [[Solved] Changing mouse icon theme for applications using qt on a gnome desktop]("http://ubuntuforums.org/showthread.php?t=1481311"), as it was at the top of the recent posts list.

Inspired by the solution there I created a directory [FONT="Courier New"]~/.icons/OSX-NiX/[/FONT] and in there a file [FONT="Courier New"]index.theme[/FONT], so now I have **two** folders and index files defining the icon theme "OSX-NiX", one in [FONT="Courier New"]/usr/share/icons/[/FONT] and this new one in my [FONT="Courier New"]$HOME[/FONT]. I played around with many different combinations of content for the new file, starting with only the *Inherits* line, which was the solution to the other thread. But whenever I put something other than "OSX-NiX" (so, actually, itself) there, the Qt apps would get the corresponding icons, but also my whole desktop would get the icons of the icon theme inherited there. When I put only "OSX-NiX" there, it would be the same as if the file wouldn't exist: Correct icons for Gnome, missing icons in *arora* and *LyX*.

In the end, I put an exact copy of the file [FONT="Courier New"]/usr/share/icons/OSX-NiX/index.theme[/FONT] to [FONT="Courier New"]~/.icons/OSX-NiX/index.theme[/FONT], and now it works: I still have my OSX-NiX icons for Gnome, and I have the icons from the first theme listed in the *Inherits* line for the Qt apps in question.

I don't get it, actually. Those single Qt apps seem to ignore the system wide installed icon theme, but as soon as there's one in my home by the same name, they use that instead -- even though it's identical to the system wide one. Maybe someone can explain that to me?

Feels like sort of a dirty solution to me, but I guess I'll mark the thread as solved, anyway.

*uu

P.S.: Weeh, it's so nice that at least I do talk to myself... :P

---

### Post by hzFVOW00pw on 2011-11-11
Copying over the file to ~/.icons/.ThemeName/index.theme worked for me too, thanx.

It seems to be a scaling bug in QT: when it loads icons from system icon themes it only provides the exact sizes that the theme has.

[http://code.google.com/p/clementine-player/issues/detail?id=1057](http://code.google.com/p/clementine-player/issues/detail?id=1057)

[http://groups.google.com/group/clementine-player/browse_thread/thread/95cbe837d67833b](http://groups.google.com/group/clementine-player/browse_thread/thread/95cbe837d67833b)

---

### Post by hzFVOW00pw on 2011-11-11
I found a system wide solution for this: Symlink /usr/local/share/icons/IconTheme/theme.index to /usr/share/icons/IconTheme/theme.index for the icon thems that have problems.

A script (ease of use for multiple installs):

```

#!/bin/bash

# Fix QT icon themes bug

if egrep -q "(lucid|maveric|natty|oneiric)" "/etc/lsb-release" ; then

    for ICONTHEME in Revenge ; do

	[ -d "/usr/local/share/icons/${ICONTHEME}" ] || mkdir -p "/usr/local/share/icons/${ICONTHEME}"

	[ -f "/usr/share/icons/${ICONTHEME}/index.theme" ] && ln -sf "/usr/share/icons/${ICONTHEME}/index.theme" "/usr/local/share/icons/${ICONTHEME}/index.theme"

    done

fi

exit 0

```

---

