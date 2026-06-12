---
title: "LXPanelMenu creating new and altering existing start menu sections and sub-sections"
date: 2014-04-17
forum: Desktop Environments
---

### Post by guiliker on 2014-04-17
Hello,

I have Lubuntu 13.10 Saucy Salamander installed and my problem is how do I edit the LXPanel menu?

I have read the following tutorials and wiki's: [http://lkubaski.wordpress.com/2012/06/29/adding-lxde-start-menu-and-desktop-shortcuts/](http://lkubaski.wordpress.com/2012/06/29/adding-lxde-start-menu-and-desktop-shortcuts/) and  [http://lkubaski.wordpress.com/2012/11/02/adding-lxde-start-menu-sections/](http://lkubaski.wordpress.com/2012/11/02/adding-lxde-start-menu-sections/) and [http://wiki.lxde.org/en/LXPanel](http://wiki.lxde.org/en/LXPanel) (which incidentally the command: ```
lxpanel -p LXDE &
``` creates a hang and a string of error codes!) and [http://wiki.lxde.org/en/LXDE:Questions#LXPanel](http://wiki.lxde.org/en/LXDE:Questions#LXPanel) as well as several old posts on here and elsewhere.

However I fine with creating custom .desktop files which work perfectly for adding start menu entries to already established menus e.g. Diablo II under Wine-Programs or Hardinfo under Accessories. What I want to do is add new start menu sections and alter some of the sections such as Games to display the menu entries to my own preferences. This I cannot seem to do!

I have tried Alacarte (From the Ubuntu repositories) which screwed up the Wine entries (which incidentally was rescued by deleting ~/.cache/menus/23cdab6ec1465592c20ec24e052bb7a and rebooting), LXMenuEDitor (LXMED) from: [http://sourceforge.net/projects/lxmed/](http://sourceforge.net/projects/lxmed/) and menulibre from [ppa:menulibre-dev/devel](https://launchpad.net/~menulibre-dev/+archive/devel) . LXMED and menulibre have some ability to create .desktop files but I do not seem to be able to create or alter LXPanel menu sections. Following laurent kubaski's tutorial I was expecting to see the 'custom menu entries' as shown in the screenshots on their tutorial however there is nothing! Am I missing something? Have I screwed a file? Help! Thanks :)

Attached are the contents of:
 ~/.cache/menus/23cdab6ec1465592c20ec24e052bb7af
 /etc/xdg/menus/lxde-applications.menu
 /etc/xdg/menus/applications-merged/wine.menu

---

