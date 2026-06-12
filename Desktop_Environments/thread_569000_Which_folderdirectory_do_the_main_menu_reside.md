---
title: "Which folder/directory do the main menu reside"
date: 2007-10-06
forum: Desktop Environments
---

### Post by amsri on 2007-10-06
I am very new to Ubuntu and got the first taste of it by installing feisty two months ago. I am running Ubuntu (Gutsy) Beta on my laptop. I have also installed kubuntu-desktop(gutsy) and keep switching them frequently. In order to get my problem solved I will try to give as much information about my computer settings as possible. If anybody needs more information than give below I will try to give the same. I have spent hours solving this problem with no success.

I have recently installed crossover linux pro 6.1.0 using .sh installer . I installed this package as a single user and hence the same installed in  ~/cxoffice. The configuration files, bottles, widows software are in ~/.cxoffice. I was using gnome desk top when I installed the package.

Now as codeweaver says on its website that it will create two entries names 'Crossover' and 'Windows Applications' in the main menu and these will have launchers for crossover utilities and window applications and thus we can directly use all the functions from start/main menu. However, this did not happen and I cannot see both the above mentioned menus in the main pop up menu.

I can find the entries for different crossover menus in
~/.cxoffice/desktopdata/cxoffice-0/cxmenu/xdg-applications/CrossOver

~/.cxoffice/default/desktopdata/cxmenu/xdg-applications/Windows+Applications (there is also a start menu folder in this directory)

etc. Well the folder cxmenu is in different forms in different directories of /.cxoffice. I mean to say that I can also find cxmenu in ~/.cxoffice/win2000/desktopdata/cxmenu (again an additional start menu folder in here)

Now my question is in which folders/directories should I put the relevant cxmenu items so as to show crossover and windows application menu in the in the main menu (as said above). Is there a default directory where all the menu items of all installed application should be added  so as to appear in main menu. OR there is another solution for a newbie like me. Also when I try to configure crossover or bottle and click menu tab it never completes and get stuck at refreshing menu items.

Thanks in advance.

---

### Post by amsri on 2007-10-06
Found the solutions at

[http://ubuntuforums.org/showthread.php?t=520677&highlight=crossover+menu](http://ubuntuforums.org/showthread.php?t=520677&highlight=crossover+menu)

It works

Thanks

---

