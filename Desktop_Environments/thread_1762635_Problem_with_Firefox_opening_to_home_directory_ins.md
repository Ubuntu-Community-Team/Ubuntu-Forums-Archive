---
title: "Problem with Firefox opening to home directory instead of homepage"
date: 2011-05-19
forum: Desktop Environments
---

### Post by davesalyers on 2011-05-19
Hi all,

I have Ubuntu (10.10) running with three different desktop environments (GNOME, LXDE, and XFCE) which I or my kids use for different sessions. In GNOME and LXDE, Firefox opens just fine to the assigned homepage, but on Xubuntu Firefox (from either the Application Menu or launcher from the Taskbar) opens to the home directory of the harddrive. When I then click the homepage icon it then goes to the correct page.

Is there any way to correct this default setting for Firefox on Xubuntu so that it opens directly to the homepage?


Thanks!

---

### Post by davesalyers on 2011-05-19
bump

---

### Post by Toz on 2011-05-19
A few things to try:

1. Make sure that in Firefox properties, on the General tab, that "When Firefox starts" is set to "Show my home page"

2. Open a command terminal and type in:```
firefox
```Does it work properly?

3. Open a command terminal and type in:```
exo-open --launch WebBrowser %u
```Does it work properly?

4. Right-click the launcher icon, select Properties, click on the "edit the currently selected item" icon, and post back the command that is being run.

---

### Post by davesalyers on 2011-05-19
I'm at the office but I will try that tonight when I get home and post the results. Thanks so much!:)

---

### Post by davesalyers on 2011-05-19
Awesome! The command "exo-open --launch WebBrowser %u" opened Firefox to the home directory (and that was the command that was being run from the Launcher) so when I changed it to just "firefox" as the command in the Launcher properties then the problem was fixed.

Thanks so much for the help!

---

