---
title: "HOWTO :  get latest compiz package  deb...from Shame repo...."
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by AlexenderReez on 2007-11-18
wondering why you can't get full plugins like in youtube video after install compiz from ubuntu repositories?the answer is simple....those package just provide basic package...so you won't get full plugins.....:)

[COLOR="Red"]*WARNING*[/COLOR] :[COLOR="RoyalBlue"] this is for whoever don't like to use git repo....(which quite pain even by using script)...but noted that these packages are not ubuntu standard package....[/COLOR]

this howto is working for gutsy gibbon...can't guarantee for other version...

ok straight to the point......firstly....open source list -->

1.using terminal

> gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

2.disable all off officlal repo --> ubuntu software collum....with uncheck all...close.[B]..[COLOR="Blue"]don't reload yet.....

(This because we don't want to these package conflict with ubuntu packages.....)

3.open synaptic ...search for compiz ...uninstall all packages ( compiz package)....close synaptic

[/COLOR][/B]

4.in terminal -->
>  gksudo gedit /etc/apt/sources.list

add

> deb [http://download.tuxfamily.org/shames/debian-lenny/desktopfx/unstable/](http://download.tuxfamily.org/shames/debian-lenny/desktopfx/unstable/) ./

5.in terminal

> wget [http://download.tuxfamily.org/shames/A42A6CF5.gpg](http://download.tuxfamily.org/shames/A42A6CF5.gpg) -O- | apt-key add -
save...close.....

6.download attachments below-->

double click libwnck18_2.18.3-1_i386.deb(one of those attachments)....install it.....

7.then in terminal --> > sudo apt-get update



8.in terminal
> sudo apt-get install compiz-manager

9a.for gnome
> sudo apt-get install compiz-fusion-gnome


9b.for kde

> sudo apt-get install compiz-fusion-kde

-->then install another 2 attachments like previous attachment...

10.using terminal

> gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

--> enable back all ubuntu repositories....then reload....open synaptic

l[COLOR="MediumTurquoise"]ock those all software versions -->[/COLOR]

-compiz
-compiz-gnome #if using gnome .... 
-compiz-plugins
-python-compiz-config
-compiz-core


there..you have done....you have got all plugins after you have install (ceck it)-->
> compiz-fusion-plugins-main
compiz-fusion-plugins-extra
compiz-fusion-plugins-unsupported

current extra unstable plugins -->
[PHP]
- bs
- cubedbus - NEW
- filedebug - NEW
- fireflies - NEW
- freescale - NEW
- freewins
- maximumize
- notifier
- photowheel
- screensaver
- stars
- visualevent
- wallpaper[/PHP]

(list will be update by time....:)

---

