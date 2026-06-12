---
title: "customising Openbox"
date: 2009-07-23
forum: Desktop Environments
---

### Post by otz070 on 2009-07-23
ok I've finally found a replacement for gnome that I like.
only thing is that it lacks some features that gnome has that I really would like to have.

so using Openbox if anyone can help me with these things that would be much appreciated:D

ok
1. getting a panel that is there when I start it up, and allows for icons and all that good stuff, like the gnome panel,
(If I can't find anything else that I like I'll probably just use the gnome panel if possible)

2. I installed some stuff to get icons on the desktop (idesk), but no luck. is there anyway to make the desktop direct to the "desktop" directory?

3. I like the way the menu is, but I'd like to do a bit of customization. only thing is I can't find the directory to put all the scripts I want to use. 

If anyone has a link or whatever any help is very much appreciated:D

---

### Post by rjmdomingo2003 on 2009-07-23
> **otz070 said:**
> ok I've finally found a replacement for gnome that I like.
only thing is that it lacks some features that gnome has that I really would like to have.

so using Openbox if anyone can help me with these things that would be much appreciated:D

ok
1. getting a panel that is there when I start it up, and allows for icons and all that good stuff, like the gnome panel,
(If I can't find anything else that I like I'll probably just use the gnome panel if possible)

2. I installed some stuff to get icons on the desktop (idesk), but no luck. is there anyway to make the desktop direct to the "desktop" directory?

3. I like the way the menu is, but I'd like to do a bit of customization. only thing is I can't find the directory to put all the scripts I want to use. 

If anyone has a link or whatever any help is very much appreciated:D
[_This_]("http://urukrama.wordpress.com/openbox-guide/") will help you a lot.

---

### Post by dc2447 on 2009-07-23
> **otz070 said:**
> ok I've finally found a replacement for gnome that I like.
only thing is that it lacks some features that gnome has that I really would like to have.

so using Openbox if anyone can help me with these things that would be much appreciated:D

ok
1. getting a panel that is there when I start it up, and allows for icons and all that good stuff, like the gnome panel,
(If I can't find anything else that I like I'll probably just use the gnome panel if possible)

2. I installed some stuff to get icons on the desktop (idesk), but no luck. is there anyway to make the desktop direct to the "desktop" directory?

3. I like the way the menu is, but I'd like to do a bit of customization. only thing is I can't find the directory to put all the scripts I want to use. 

If anyone has a link or whatever any help is very much appreciated:D

use fbpanel and obmenu

---

### Post by otz070 on 2009-07-25
Thanks Much:D
I'm going to check them out and see if it makes it more comfortable for me to use:)

---

### Post by urukrama on 2009-08-02
> **otz070 said:**
> 
1. getting a panel that is there when I start it up, and allows for icons and all that good stuff, like the gnome panel,
(If I can't find anything else that I like I'll probably just use the gnome panel if possible)

You can use a wide variety of panels. Pypanel is popular with Openbox users, but very minimal. Fbpanel and lxpanel are also widely used. You can even use xfce4-panel or gnome-panel in Openbox -- just add them to your autostart file. 

> **otz070 said:**
> 2. I installed some stuff to get icons on the desktop (idesk), but no luck. is there anyway to make the desktop direct to the "desktop" directory?

You can use a file manager that draws the desktop, like PCManFM, Rox-filer, or even Nautilus (in which case you'll lose the Openbox right click desktop menu).

> **otz070 said:**
> 3. I like the way the menu is, but I'd like to do a bit of customization. only thing is I can't find the directory to put all the scripts I want to use. 

You can customize the menu by editing the menu.xml file (in ~/.config/openbox/). Obmenu makes this a lot easier to do, though it cannot configure some of the newer menu features (like a separator with text, etc.)

Have a look at my Openbox guide which rjmdomingo2003 linked to. I think it will help you get started.

---

### Post by snowpine on 2009-08-02
Give LXDE a try; it is basically Openbox plus the extras you describe.

---

### Post by jaxxstorm on 2009-08-02
If you're really interested in using Openbox, a lot of the customization has been done on some distros. One such distro is Crunchbang. Its Ubuntu, built from a minimal install and configured to make it easy to use, including a panel etc.

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by otz070 on 2009-08-05
> **snowpine said:**
> Give LXDE a try; it is basically Openbox plus the extras you describe.

Actually I think I've tried that one before, but I unfortunately did not like it too well...
I've tried alot of different window managers and desktop managers, and I found I like open box the best as of yet.

> **jaxxstorm said:**
> If you're really interested in using Openbox, a lot of the customization has been done on some distros. One such distro is Crunchbang. Its Ubuntu, built from a minimal install and configured to make it easy to use, including a panel etc.

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

Ok for this I can see the point of doing a fresh install on a new computer, but for my current systems is it that I have to actually wipe the linux drive and reinstall?
Because I really don't want to do that.

Now for a fresh install on a new system that could be something to think about, I really like the idea minimal installs. (I end up removing half the stuff from a basic ubuntu install anyway so)
> **urukrama said:**
> You can use a wide variety of panels. Pypanel is popular with Openbox users, but very minimal. Fbpanel and lxpanel are also widely used. You can even use xfce4-panel or gnome-panel in Openbox -- just add them to your autostart file. 



You can use a file manager that draws the desktop, like PCManFM, Rox-filer, or even Nautilus (in which case you'll lose the Openbox right click desktop menu).



You can customize the menu by editing the menu.xml file (in ~/.config/openbox/). Obmenu makes this a lot easier to do, though it cannot configure some of the newer menu features (like a separator with text, etc.)

Have a look at my Openbox guide which rjmdomingo2003 linked to. I think it will help you get started.

I've looked over your guide and found it extremely helpful. Its quite easy to understand:) Thanks.


Here's what I ended up with:
lxpanel
pcmanfm for file manager/desktop (I used that with gnome anyways so bonus I guess:))

things got pretty easy once I figured out how to get the autostart working right

:D Thanks Again

---

### Post by becxjo on 2009-09-18
Hello everyone. Recently I added OpenBox to the the list of window managers I have on my Ubuntu 9.04 (x86_64). By doing so I have two different possibilities for loging to my linux:

1- an ordinary version: Gnome + Metacity + Nautilus + OpenOffice + gnome-terminal + FireFox + other default packages of plane installation of Ubuntu.

2- a minimalist version: OpenBox + EvilVte + pcmanfm + other light things.

[I]Note: I'm not worry about space on my Hard Drive and can keep both desktops and their companions.
[/I]
My reasoning was that when I need an easy way of interacting with the linux, test the things and graphically configure them or use heavy handed utilities (text processor like OpenOffice) I would login in the ordinary version. When I need the computers' resources (CPU and RAM) for heavy calculations, then I use the lighter version that leaves these resources free for other programs. So far I configured the OpenBox successfully but I'm worry for additional routines that are running behind its back and I'm not aware of them. Which routines and services are not vital for the linux functionality and I can stop them before beginning my light version?

Also I would like to have a dynamic behavior for my files. When I'm logged in the ordinary version and using Nautilus, I want that after double clicking on a file the nautilus use a set of default programs for opening that file (gedit for texts, the default media player for media files and the default image viewer of gnome for pictures). But when I'm in the light version and using pcmanfm, I want that by double clicking on a file, lighter programs open them (LeafPad for text, feh for pictures and VLC for media). Is there any way to do this?

---

### Post by Lukios on 2009-09-24
> **otz070 said:**
> 

Ok for this I can see the point of doing a fresh install on a new computer, but for my current systems is it that I have to actually wipe the linux drive and reinstall?
Because I really don't want to do that.

Now for a fresh install on a new system that could be something to think about, I really like the idea minimal installs. (I end up removing half the stuff from a basic ubuntu install anyway so)

 

If you just want to mess around with the idea of Making a minimal install, you can always do so first in virtualbox. After you have configured it the way you like, I'm assuming you can use remastersys to make yourself a bootable recovery CD within that same environment. I would advise that you note all the configurations and changes you liked, then start over again with a fresh minimal install and apply only the configurations and changes you liked.

> **otz070 said:**
> 
I've looked over your guide and found it extremely helpful. Its quite easy to understand:) Thanks.


Here's what I ended up with:
lxpanel
pcmanfm for file manager/desktop (I used that with gnome anyways so bonus I guess:))

things got pretty easy once I figured out how to get the autostart working right

:D Thanks Again

Though lxpanel has come a long way from what it was, I would still suggest using gnome-panel. You already have gnome installed so just make sure that you have gnome-panel in start up for your openbox session. To easily solve the logout/shut down issue, you can always make an icon that points to the openbox logout/shutdown.

---

