---
title: "Move menu from top panel back to its program in Unity"
date: 2011-05-07
forum: Desktop Environments
---

### Post by ianc1 on 2011-05-07
I'm getting frustrated.  I decided to persist with Unity having spent until today launching in an Ubuntu Classic session.  The thing that bugs me the most is the fact that each program has its menu (ie File, Edit etc) in the top panel.  This may be fine for netbooks but not my laptop.

I just launched Tomboy, which startde with its window in the bottom right of the screen, however to get to the programs menu I have to move the cursor all the way to the top right of the screen - miles.

How can I move this menu back to the program?  Any ideas?

Thanks

---

### Post by mc4man on 2011-05-07
Do you want to move back only on specific apps or all apps?
I do the former, though if you wish to do for all then search appmenu in synaptic and remove just these 2 packages
appmenu-gtk
appmenu-qt

or this in a terminal
```
sudo apt-get remove appmenu-gtk appmenu-qt
```
Then log out/in

If you wish to do some apps individually just ask..

---

### Post by spamalam on 2011-05-07
What an awful feature!  It makes it fell like a crummy mac :(

Thanks for the command!  This worked for most apps, but firefox is still defaulting to the docking of menus to the top panel... any idea how to fix this issue?

---

### Post by ajgreeny on 2011-05-07
Not sure, but can you remove global-menu?  I am not running 11.04 so am not sure if it will help, nor even if it is possible to do that.

---

### Post by mc4man on 2011-05-07
Firefox uses an extension for global menu - either disable in firefox - tools -addons 
or remove the extension package
firefox-globalmenu

---

### Post by ianc1 on 2011-05-08
Thanks everyone, I've now got the menu back as I like it and can persevere with Unity which is OK not too bad.  I still dislike the fact its harder to see all applications and its less efficient (clicking find and tying program name etc).

In case anyone is interested there is also a Thunderbird package to integrate Thunderbird into Unity, it's called thunderbird-globalmenu.  I've not tested it yet but I assume removal of this will revert the Thunderbird menu back to Thunderbird.

Thanks again everyone.

---

### Post by blueridgedog on 2011-05-09
> **mc4man said:**
> If you wish to do some apps individually just ask..

This would be good to know...how do you do it individually?

---

### Post by ianc1 on 2011-05-09
Hi

I'm unsure if this is a consequence of removing appmenu-gtk and appmenu-qt packages but whenever I start tomboy from the terminal the terminal outputs something along the lines of:```
[INFO 19:50:24.487] Initializing Mono.Addins
```and then hangs.  The tomboy icon appears as normal on the panel.

Is this hanging because the terminal is expecting tomboy to send an exit code and I haven't closed tomboy or is it an error/bug I've introduced by removing the above packages.  Any ideas?

Cheers

---

### Post by mc4man on 2011-05-09
> **blueridgedog said:**
> This would be good to know...how do you do it individually?
Because I do find use for the Gm in some instances so  I leave it installed and - 
I do it this way for apps started from menu or right click - editing the Exec= in the apps .desktop, adding blue

Ex. for  gtk apps (using gedit.desktop as example 
```
gksudo gedit /usr/share/applications/gedit.desktop
```
```
[Desktop Entry]
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Exec=[COLOR="Blue"]env UBUNTU_MENUPROXY=0[/COLOR] gedit %U
..clipped
```

Ex. for qt apps using vlc.desktop as example
```
clipped...
Comment[zh_CN]=&#20026;&#24744;&#35835;&#21462;&#12289;&#25429;&#33719;&#25110;&#21457;&#36865;&#22810;&#23186;&#20307;&#27969;
Exec=[COLOR="Blue"]env QT_X11_NO_NATIVE_MENUBAR=1[/COLOR] vlc %U
Icon=vlc
Terminal=false
clipped..
```

Because of the many possibilities of using/editing/creating .desktops in natty/unity I just create 2 nautilus actions specific to .desktops - Open Desktop File as Root and Open Desktop File
Makes life easy..

For adjusting cli use of an app an alias can take care of - ex. of totem
```
alias totem='export UBUNTU_MENUPROXY=0 && totem'
```

Also of minor interest is these env's can be used with quicklists, whether as add. entries for an app or as part of a group of apps
(in other words you could have a quicklist entry that uses the Gm in app A and one that doesn't in app A - many interesting possibilities there
Some Ex.'s (posts 29,34.36
[http://ubuntuforums.org/showthread.php?p=10778758#post10778758](http://ubuntuforums.org/showthread.php?p=10778758#post10778758)

[http://ubuntuforums.org/showthread.php?p=10765280#post10765280](http://ubuntuforums.org/showthread.php?p=10765280#post10765280)

(there is also a 3rd way by creating a binary diversion that affects all uses of an app - but I think not needed due to other alternatives avail.

Also note that .desktops in /usr/share/applications that have been edited are subject to an update over writing, either stash a copy or just cp to/create ones in ~/.local/share/applications or if multiple users then use /usr/local/...

---

