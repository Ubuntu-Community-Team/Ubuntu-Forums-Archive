---
title: "HOWTO: change the rhythmbox icon to the SVN one"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by MRiGnS on 2007-05-14
1.Download this package: rhythmbox-icons.tar.gz

2. copy the icons to the /scalabe/apps folder of your icon theme

the are located in ~/.icons/<theme> or /usr/share/icons/<theme>

for example: /usr/share/icons/UbuntuStudio.

3.now open a terminal and run:

sudo gtk-update-icon-cache -f "IconThemeDirectory"

Without the quotes. For me it would be:

sudo gtk-update-icon-cache -f /usr/share/icons/UbuntuStudio

Now it should work.

If you are running Rhythmbox, restart it.

The icon package is avaiable on my blog:

[http://mrigns.ath.cx/index.php/2007/05/14/howto-change-the-rhythmbox-icon-to-the-svn-one/](http://mrigns.ath.cx/index.php/2007/05/14/howto-change-the-rhythmbox-icon-to-the-svn-one/)

and

[http://mrigns.ath.cx/index.php/2007/05/14/rhythmbox-gets-a-new-icon/](http://mrigns.ath.cx/index.php/2007/05/14/rhythmbox-gets-a-new-icon/)

Have fun!

---

### Post by kpolice on 2007-05-14
No offense but it seems that you want to spam ubuntu forums to get some traffic to your blog and this has already been posted the last week.

---

