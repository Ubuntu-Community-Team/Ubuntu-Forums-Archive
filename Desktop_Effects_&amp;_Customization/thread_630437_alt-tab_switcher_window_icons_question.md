---
title: "alt-tab switcher window icons question"
date: 2007-12-03
forum: Desktop Effects &amp; Customization
---

### Post by evuraan on 2007-12-03
Pls refer the screenshot:

[IMG]http://evuraan.googlepages.com/alt-tab.png[/IMG]

Other than Firefox's icon, those other tasks seen running were launched from their own respective launchers on the panel/desktop - Each launcher  has its own icon as well. 

IOW, if I create a launcher for /usr/bin/blah with a customized icon, I don't see its icon in the  alt-tab switcher icons list. 

How do I go about adding tasks/apps have their own icons? (in the alt-tab switcher window) 

That would make choosing the right app from alt-tab switcher list much easier, esp when you prefer running gnome with no special effects. 

The nearest info I could find was [here,]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/18371/") but is not enough to answer this question.

Thanks..!

---

### Post by flamacue on 2007-12-15
I was having the same issue, and wanted to know the solution, too...

Note also that the icon(s) for such tasks are the same generic window icon instead of being the application's icon.  I would like to change those, too...

I think _[COLOR="Blue"][[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=634933")[/COLOR]_ is the answer.  It seems it's on a per-app basis, i.e. however the app in question handles its icons.


EDIT:  Success for GNUzilla Icecat!  (formerly GNUzilla Iceweasel, not to be confused with Debian Iceweasel...)

I installed it per the directions at

_[COLOR="Blue"][https://wiki.ubuntu.com/InstallIceweasel#head-43da090da143b7418bc776bea55d51d98f0cef4a](https://wiki.ubuntu.com/InstallIceweasel#head-43da090da143b7418bc776bea55d51d98f0cef4a)[/COLOR]_

using /usr/lib as "the_directory_where_you_want_iceweasel_installed".

Then
```
cd /usr/bin
sudo ln -s ../lib/icecat/icecat .
```

and I added a launcher to my Menu with System --> Preferences --> Main Menu

using /usr/lib/icecat/icons/default.xpm as the icon for the icon for the launcher.

NOW for the subject of this thread (in regards to Icecat, anyway)...

```
sudo mkdir -p /usr/lib/icecat/chrome/icons/default
cd /usr/lib/icecat/chrome/icons/default
sudo ln -s ../../../icons/default.xpm .
```

THAT will cause the taskbar icon and task switcher icons to use the default Icecat icon!


EDIT2:  I was able to figure that out due in large part to

[http://ubuntuforums.org/showthread.php?t=347689&highlight=iceweasel+icons](http://ubuntuforums.org/showthread.php?t=347689&highlight=iceweasel+icons)

Thanks to those posters.  :)

---

### Post by evuraan on 2007-12-20
Right. The icon at the upper left corner is some .xpm file - this xpm is picked up by metacity (window manager) when it populates the alt-tab list. 

For instance, /usr/share/pixmaps/gnome-terminal.xpm would be the icon for gnome-terminal in the alt-tab list. 

I will revise/rephrase my question:

How can I implement unique alt-tab icons for the following? 

1) xterm -T "host-one" -e "ssh host1"
2) xterm -T "host-two" -e "ssh host2"

Yeah, I will create host1.xpm & host2.xpm and then what? 

Any takers? Thanks..!

---

