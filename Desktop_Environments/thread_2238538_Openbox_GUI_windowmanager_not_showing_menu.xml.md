---
title: "Openbox GUI windowmanager not showing menu.xml"
date: 2014-08-08
forum: Desktop Environments
---

### Post by Coder88 on 2014-08-08
I installed the openbox window manager GUI, but when i use [FONT=courier new]obmenu[/FONT] to add/create submenus and add apps (Firefox, Thunderbird, etc) and save the menu.xml I am not seeing the newly created (using obmenu) openbox menu with apps etc. I checked and indeed menu.xml is in 
  [FONT=courier new]~/.config/openbox/menu.xml [/FONT]
and when i view that file with the [FONT=courier new]less[/FONT] command my newly customized menu is in fact in that menu.xml

I also made sure the same customized menu.xml is in 
  [FONT=courier new]/etc/xdg/openbox/menu.xml[/FONT]

I log out then log back in to Ubuntu with the Openbox chosen as the window manager and right click and all i see is the default thin and barely usable openbox menu that has virtually no links to my many ubuntu installed software. I even rebooted the computer for good measure. No joy.

Anybody? This window managuer GUI certainly does not seem ready for prime time until it can be made to recognize already installed software and add that to its menus and submenus. Frustrating. The live openbox CD I burned is fine, has lots of apps and right clicking shows them, but adding openbox via synaptic has just resulted in frustration; sure I can run apps from a terminal but I should not have to, the menu.xml should be usable by openbox but for some reasons it is not. I checked permissions and menu.xml is readable by owner, group, others.

---

### Post by vasa1 on 2014-08-09
Please look at ~/.config/openbox/rc.xml. You should have a section that has something like this:```
  <menu>
    <!-- You can specify more than one menu file in here and they are all loaded,
       just don't make menu ids clash or, well, it'll be kind of pointless -->
    <!-- default menu file (or custom one in $HOME/.config/openbox/) -->
    **<file>/home/vasa1/.config/openbox/menu.xml</file>**
    <hideDelay>200</hideDelay>
    <!-- if a press-release lasts longer than this setting (in milliseconds), the
       menu is hidden again -->
    <middle>no</middle>
    <!-- center submenus vertically about the parent entry -->
    <submenuShowDelay>100</submenuShowDelay>
    <!-- time to delay before showing a submenu after hovering over the parent
       entry.
       if this is a negative value, then the delay is infinite and the
       submenu will not be shown until it is clicked on -->
    <submenuHideDelay>400</submenuHideDelay>
    <!-- time to delay before hiding a submenu when selecting another
       entry in parent menu
       if this is a negative value, then the delay is infinite and the
       submenu will not be hidden until a different submenu is opened -->
    <applicationIcons>yes</applicationIcons>
    <!-- controls if icons appear in the client-list-(combined-)menu -->
    <manageDesktops>yes</manageDesktops>
    <!-- show the manage desktops section in the client-list-(combined-)menu -->
    <showIcons>yes</showIcons>
    <!-- show icons on the menu -->
  </menu>
```Do the contents between **<file>** and **</file>** point to the menu.xml file you want to use?

---

### Post by bradwilliams923 on 2014-08-12
Openbox's menu can actually be configured to automatically add apps when installed, through use of pipe menus. I've seen distros do it before. For example: [http://crunchbanglinux.org/wiki/configuring_the_openbox_menu#auto_updating_menu](http://crunchbanglinux.org/wiki/configuring_the_openbox_menu#auto_updating_menu). Never interested me, since it defeats the purpose of keeping openbox so simple and quickly configurable. That's just my opinion. I understand your frustration with the blank, "vanilla" openbox setup, though. Distros and live CD's typically preconfigure their openbox setups the way they want them before shipping.

---

### Post by vasa1 on 2014-08-12
> **bradwilliams923 said:**
> ... Distros and live CD's typically preconfigure their openbox setups the way they want them before shipping.
That applies to distros which have Openbox as their default window manager; I'm thinking of distros like Crunchbang and maybe Manjaro. It doesn't apply if one has a "non-Openbox" distro and then installs Openbox. In the latter case, the user has to do some work.

---

### Post by bradwilliams923 on 2014-08-13
> **vasa1 said:**
> That applies to distros which have Openbox as their default window manager; I'm thinking of distros like Crunchbang and maybe Manjaro. It doesn't apply if one has a "non-Openbox" distro and then installs Openbox. In the latter case, the user has to do some work.

Agreed. Often it's quite a lot of work, particularly if you're not already familiar with the way Openbox works. If one is interested in trying out Openbox, I'd recommend playing with one of those pre-configured distros first (Crunchbang is particularly helpful) before setting one up from scratch on your distro of choice. Openbox is may favorite choice for a desktop, and it can be so simple and powerful and fast, but it takes a little investment of time to learn the ropes.

---

