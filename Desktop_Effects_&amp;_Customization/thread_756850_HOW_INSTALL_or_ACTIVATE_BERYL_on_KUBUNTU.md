---
title: "HOW INSTALL or ACTIVATE BERYL on KUBUNTU?"
date: 2008-04-16
forum: Desktop Effects &amp; Customization
---

### Post by macnyak on 2008-04-16
i need ur expertise... please help me, im a newbie... how can i install or activate beryl? what are the step by step procedures?

please explain it to me briefly coz i dont know such terms or commands for kubuntu...

for those who will help I THANK YOU from the buttom of my heart... and more power...

---

### Post by Zorael on 2008-04-16
Are you using Gutsy? Beryl is old and deprecated; Compiz has superseded it.

I am on a l0sedows machine right now so I can't confirm things, but Compiz is likely available in Adept Installer. It may be called GL Desktop or Advanced Desktop Effects. But in case it isn't there, read on.


**Graphical instructions (long and annoying!)**
Open Adept Manager. You may need to enable repositories; it is available in the menu someplace. May be called Software Sources.

Search for **compiz** and mark it for installation. It is a package bundle that refers to several real packages.

To double-check that it marked the correct packages, make sure the following ones were marked.
[list][*]**compiz-core**
[*]**compiz-kde**
[*]**compiz-plugins**
[*]**compiz-compcomm-plugins-main** (if it even exists anymore. If not, skip)
[*]**compiz-fusion-plugins-main** (for fusion plugins)
[*]**compiz-fusion-plugins-extra** (for fusion plugins)[/list]
You don't need **compiz-gnome**, so it's safe to unmark. It might say that you're breaking the compiz bundle, but that's safe to do.

Lastly, find and mark the following packages:
[list][*]**compizconfig-settings-manager**
[*]**emerald**[/list]
Then apply. See below for Emerald themes.


**Terminal instructions (short and easy!)**
```
$ sudo apt-get install compiz* emerald*
$ sudo apt-get autoremove --purge compiz-gnome
```
See, terminal commands are easy! :>


**Emerald themes**
Download the Emerald themes from the Feisty repositories [here](http://ubuntuforums.org/newreply.php?do=postreply&t=756850), and double-click it in your file manager of choice. It will, of course, ask for your password.

Alternatively, the terminal way:
```
$ sudo dpkg -i emerald-themes*
```

---

