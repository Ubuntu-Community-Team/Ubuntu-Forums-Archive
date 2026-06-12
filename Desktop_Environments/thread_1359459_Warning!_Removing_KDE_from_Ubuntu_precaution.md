---
title: "Warning! Removing KDE from Ubuntu precaution"
date: 2009-12-19
forum: Desktop Environments
---

### Post by haribol707 on 2009-12-19
Hello, I just removed KDE from my system by following instructions from here

[http://www.psychocats.net/ubuntu/puregnomejaunty](http://www.psychocats.net/ubuntu/puregnomejaunty)

I found the link from one of the threads on this forum ([http://ubuntuforums.org/showthread.php?t=210294)]("http://ubuntuforums.org/showthread.php?t=210294")

Voila! Disaster!! It removed wine, NetBeans and vlc player along with KDE :( I had only recently installed Office 2007 and I need to reinstall it now!

Word of caution: I am not sure where I went wrong, but if some of you are going to follow the same instructions to remove KDE, I would want you to be aware of this.

Btw, afair I installed these packages while logged into gnome session. Any ideas why these were uninstalled? I am not sure what other packages are broken as of now. Will post if I find any other broken packages.

---

### Post by lovinglinux on 2009-12-19
> **haribol707 said:**
> Voila! Disaster!! It removed wine, NetBeans and vlc player along with KDE :( I had only recently installed Office 2007 and I need to reinstall it now!

Not a big deal. Just install the applications you need again. You won't loose any settings.

> **haribol707 said:**
> Btw, afair I installed these packages while logged into gnome session. Any ideas why these were uninstalled?

This has nothing to do with the fact that you were log in into a Gnome session. The package manager does not depend on the desktop environment your are using. They were removed because those applications depend on some packages (libraries applications) removed by the command suggested by psychocats. 

> **haribol707 said:**
> I am not sure what other packages are broken as of now. Will post if I find any other broken packages.

If you still have **ubuntu-desktop** package installed, then you have all packages installed by the default Ubuntu installation. If not, just install it again and it will take care of missing packages. 

Any additional applications that you have installed manually would only be completely removed if they depend on any package removed by the command. So is not likely that you will find broken packages. Nevertheless, some applications also install recommended packages. While they do not depend on these to work, some functionality might be missing.

Whenever I'm about to make drastic changes, I do a backup of the list of installed packages using [UMarks](https://addons.mozilla.org/en-US/firefox/addon/13153/) (I'm the developer of that extension). If something goes wrong I can compare the backup before and after the changes, to see which packages has been installed/deinstalled and also revert the changes by running a backup through UMarks.

---

### Post by jerrrys on 2009-12-19
umarks rocks :)

---

### Post by haribol707 on 2009-12-19
Thanks for the post. I will take a look at UMarks.

---

