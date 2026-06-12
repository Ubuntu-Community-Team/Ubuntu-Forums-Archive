---
title: "xterm internationalization"
date: 2005-10-10
forum: Desktop Environments
---

### Post by duminas on 2005-10-10
I have a large amount of files with Japanese filenames that I wish to manipulate using xterm. The command I use to launch xterm is this: **uxterm -fn monospace -fs 10**. However, when I attempt to list the contents of a directory containing aforementioned files, I get a lot of boxy characters as output on the terminal. However, if I copy them out and paste elsewhere, this is printed (an example): &#33521;&#38596;&#20253;&#35500;&#8549; &#12300;&#31354;&#12398;&#36556;&#36321;&#12301;

And oddly, I keep getting an error that the "monospace" font cannot be found, even though a lot of other applications (gnome-terminal, namely) are able to use it fine; and thus, my font size declaration gets ignored.

Anyone have any ideas, here?
The output of locale is as follows:```
LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=
```
Thanks, guys.
If I need provide more information, feel free to ask.

---

### Post by r0ll3r on 2006-01-15
hi there,
if xterm is complaining about the monospace font, you should choose a correct font. Try xfontsel which might offer you lots of fonts. But i recommend you to look at /usr/share/fonts/ and /usr/share/X11/fonts/ and /etc/X11/fonts/ as these are good locations to check for fonts and alias names. Try looking at the misc subfolders, as usually there are some weird fonts like japanese and so on. Keep on trying and trying. :)

Use xlsfonts to list all available fonts.

---

