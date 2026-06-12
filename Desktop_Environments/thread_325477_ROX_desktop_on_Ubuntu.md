---
title: "ROX desktop on Ubuntu?"
date: 2006-12-25
forum: Desktop Environments
---

### Post by raynevandunem on 2006-12-25
Has anyone tried installing [ROX Desktop]("http://rox.sourceforge.net/") on Ubuntu?

I'm curious about it because of how there are quite a few distributions of Ubuntu dedicated to specific desktop environments (XFCE, GNOME, KDE).

Thanks.

---

### Post by slimdog360 on 2006-12-25
Ive used the file manager, and thought about using the desktop environment, but it never panned out. The file manager it nice and fast but I still prefer konqueror.

If you do put ROX on your computer could you post your thoughts about it here. Id be interested in seeing what others think about it.

---

### Post by scooper on 2006-12-26
I've used Rox in the past, but my knowledge of it isn't necessarily up to date.  I like Rox a lot.  It does take getting used to.  For a full desktop, I believe there's a minimalistic window manager (ouroboros?).  I never got beyond using Rox desktop for everything but the WM, and I used fluxbox for the wm.  At the time ouroboros was missing many features.

It works great with any window manager, and provides a simple panel, desktop icons (the "pinboard") and file manager windows.  The panel and pinboard (desktop) were primitive, but serviceable and fairly powerful.  Just don't expect a lot of eye candy, unless the author's philosophy has greatly changed.

I'm about to switch back to fluxbox/rox after my usual tour of Gnome and KDE following a new Ubuntu release.  So you won't be alone, although I probably won't bother with the pinboard.  I find a panel is enough and I keep the desktop pretty.

As a file manager I'd much rather use rox than nautilus or konquerer.

Have fun, it's definitely worth a try.  Of course if you expect something as large and feature-ful as KDE or Gnome, maybe you'll be very disappointed. :)

---

### Post by 3rdalbum on 2006-12-26
The primary school I went to used RISC OS-based computers... I still have fond memories of dragging and dropping my files from the application to the file manager in order to save them! :-)

Apparantly, installing Rox Desktop on Ubuntu is no cakewalk. If the situation were different, or if I used a different distribution, I would seriously consider installing it.

---

### Post by raynevandunem on 2006-12-26
I've just found a guide for installing ROX on Ubuntu AND configuring it to look liked GNOME.

[http://chrisarndt.de/rox-ubuntu/](http://chrisarndt.de/rox-ubuntu/)

---

### Post by jdackle on 2007-07-22
> **raynevandunem said:**
> I've just found a guide for installing ROX on Ubuntu AND configuring it to look liked GNOME.

[http://chrisarndt.de/rox-ubuntu/](http://chrisarndt.de/rox-ubuntu/)

My problem following through that guide:
- I'm still on Ubuntu 6.06 Dapper Drake.
- When trying to instlal zeroinstall-injector, I get an error that it depends on python-control (not installed)
- There is NO python-control for Dapper. :(
- Edgy's version of python-control conflicts with my current python installation.

What should I do?

(I need a much faster WM/DE mix. My computer is to slow. Was planning on using ROX with Openbox (or maybe Fluxbox, even considered Blackbox) to replace Gnome/Metacity.)

---

### Post by kerry_s on 2007-07-22
Dude you don't need the rox applications to have a rox desktop. rox-filer is all you need. it can do the desktop icons & background, it also has the panel if you want to use that. to get rox as a desktop you just use> rox -p=pinboard <that's it, if you using fluxbox make sure you turn on compatibility.
i just built a setup for grandma with nothing but desktop icons for the applications. i used debian minimal+fluxbox+rox. ( [http://ubuntuforums.org/showthread.php?t=498808](http://ubuntuforums.org/showthread.php?t=498808) )
i set it up on my system and just transfered the settings when i did her install.

i still use some of the setup but don't need all that stuff grandma needed.
i forgot to mention my system is a measly 450mhz 256ram 20gig hd. after i got rid of the stuff i tested for grandma's setup my install is only around 570+mb(check out the system monitor in the pic) my system is so light and fast, i have to do alot to even get into swap space. :)

---

### Post by jdackle on 2007-07-23
Thanks a ton kerry_s! :D

You did read my post perfectly! I did think the ROX-filer .deb didn't suply the desktop features and I'dI need ROX-All (which is not on the repos).

Should be straight-forward then! :D

I'll try it out and post the results.

BTW... cool desktop!
And your CPU seems to be only a 234MHz. Mine is a 450MHZ with 512Kb RAM and having Thunderbird, Firefox and aMSN open at the same time would always shut-down Thunderbird or sometimes freeze the desktop! :( Never ever think of opening Openoffice at the same time with those in my current install!!! :P
If your system is now so light and fast it rarely gets into swap... That's what I need! :D

Thanks again! :)

---

### Post by jdackle on 2007-07-23
Yep, working fine! 8-)

Now I just have to get familiar with it and tweak it a bit...
Hardest part will now be to choose the WM... lol But that's not for this thread...

---

### Post by kerry_s on 2007-07-23
mines 450mhz, but i have it only show what it's running at, it has 8 levels of stepping, i already know its a 450mhz so i didn't see the need to put that in the monitor.

just to let you know, you can use the rox-apps if you want to, it's very easy to manually install them, most are drag & drop to the right place you just download them from the rox site. the thing is there all python, python is bloated & slow, your better off just sticking with light weight apps in the repos.

to get a light & fast like mine you need to go custom. i can use all those app's you mention at the same time and mine won't even stutter. :)

[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)
debian is faster on old machines.

start the install> installgui < for the fancy installer
when you get to the package selection, un-select all of them. that will give you a base only install no bloat.

log in as root

apt-get install xorg gdm synaptic fluxbox rox-filer leafpad

reboot(ctrl+alt+delete)

select fluxbox in the session menu & login

welcome to the world of custom install's, now open synaptic and get what ever else you want.

have fun.

---

### Post by jdackle on 2007-07-24
Thansk for all your tips, kerry_s!

Well, I wasn't really in the mood for a new form-scratch install. And I've heard Debian can be scary... It scares me just to read so many people having troucle even starting X... Well... At least, I've read some in the old days...
I think I can work around the bloat I already have now... :lolflag:

Regarding ROX apps... Have I understood correctly that you're suggesting to install non-ROX apps with it?
I'd need things that can work with ROX's panel, like a clock-applet, taskbar and the likes... Can this be done with non-ROX apps?

Thanks again for your precious help! :)

---

### Post by kerry_s on 2007-07-24
> **jdackle said:**
> Thansk for all your tips, kerry_s!

Well, I wasn't really in the mood for a new form-scratch install. And I've heard Debian can be scary... It scares me just to read so many people having troucle even starting X... Well... At least, I've read some in the old days...
I think I can work around the bloat I already have now... :lolflag:

Regarding ROX apps... Have I understood correctly that you're suggesting to install non-ROX apps with it?
I'd need things that can work with ROX's panel, like a clock-applet, taskbar and the likes... Can this be done with non-ROX apps?

Thanks again for your precious help! :)


if your going to use the panel, then you'll most likely have to use the rox-apps, so make sure you read the manual install instructions on where to drag it to to be detected. also make sure you grab the python dependency's from the repo. if the application don't work check your .xsession-errors for the dependency your missing. just play with it's simple.

---

### Post by jdackle on 2007-07-24
So... The ROX panel will only work with ROX apps, huh? Well, does make sense...
But... will it be worth it then?
My intention to use ROX's panel was... why put yet another program(panel) on top of ROX when the latest has its own?..
But considering wht you said about ROX apps being all python and thus bloated and slow... Won't it be a better choice to choose say pypanel (seems to be on everbody's mouth...) and some light applets to go with it?...

I know, I'm turning into a nag... Sorry...

---

### Post by RedSquirrel on 2007-07-24
> **jdackle said:**
> Well, I wasn't really in the mood for a new form-scratch install. And I've heard Debian can be scary... It scares me just to read so many people having troucle even starting X... Well... At least, I've read some in the old days...

If you ever get in the mood for a barebones install, you can do one with Ubuntu if you like. ;)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by jdackle on 2007-07-24
> **RedSquirrel said:**
> If you ever get in the mood for a barebones install, you can do one with Ubuntu if you like. ;)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

Matter of fact I think I would ... but not just now! :lolflag:
But thanks for the links. May come in handy at another time... :)

---

### Post by kerry_s on 2007-07-25
> **jdackle said:**
> So... The ROX panel will only work with ROX apps, huh? Well, does make sense...
But... will it be worth it then?
My intention to use ROX's panel was... why put yet another program(panel) on top of ROX when the latest has its own?..
But considering wht you said about ROX apps being all python and thus bloated and slow... Won't it be a better choice to choose say pypanel (seems to be on everbody's mouth...) and some light applets to go with it?...

I know, I'm turning into a nag... Sorry...

yes that's what i would recommend, there's really no use for the rox-panel unless you really want it.
panels are really over rated, i would suggest trying docker app's instead of a panel, to get the functions of the panel parts your looking for. i just use the standard fluxbox panel in auto hide mode, it provides the work space switcher, system tray, task bar, clock. i don't really need it cause i have rox setup to minimize to the desktop and i usually just middle click on the title bar to bring the background app's forward. i also like to use my full screen for the larger apps, like my browser.

---

### Post by jdackle on 2007-07-25
Thanks again, Kerry-s! :)

Something I've onlyu thought of today (it was late yesterday...):
Isn't pypanel a python app itself (I'm assuming it by the prefix: "py")?

I hear what you say about using the dock. I did use blackbox for a good while a few years ago. And fluxbox for a shorter time too. So I'm more or less familiar with the slit/dock.

I guess I can go do like, was it dockhouse.com?, and look for a workspace switcher, taskbar, system tray, clock, whatever. 'Cause I'm using openbox instead of fluxbox - fluxbox down here was sloooooooow...  And as you probably know, there is no panel in openbox.
The only one that concerns me a bit is the taskbar... My eyesight isn't so great and I'll need a good-visibility taskbar...

Thanks again! :)

---

### Post by jdackle on 2007-07-25
I've just noticed this is getting a bit offtopic... Or is it?
Guess it may be useful to have a little bit of info on alternatives to ROX Desktop's components, huh? ;)

BTW, very neat desktop you have! :cool:

But I myself prefer having the loaded apps loaded somewhere I don't have to minimize everything to access to... I am currently using that feature however. For the moment, it's still nicer than midle-clicking the desktop. :)

---

### Post by kerry_s on 2007-07-25
not middle clicking the desktop, middle click on the window title bar will cycle the windows to the top.

make sure you check the repo, most of the dock apps are there.

when i used openbox i went with thunar & xfce4-panel, since it was a dependency of thunar. i can't remember if i used rox in openbox, it's been along time since i used it.

---

### Post by jdackle on 2007-07-25
I didn't know about that middle-clicking on the window title bar. But all I got was cycling through the opened-up windows, NOT the minimized/iconified ones. :(
Without ROX's iconify-to-desktop feature, I have to middle-click the desktop to get a list of all windows (iconified and not) on all desktops. It's actually handy taht way, but only if you don'te have a bunch of maximised windows on your desktop as I usually have...
But thanks for the tip! That's a handy one too! :)

Hmm... I'll search the forum for some comparison between ROX-Desktop and Thunar/XFCE-panel...

Cheers!


I'm forking off to this thread for now: [Dock apps to build a kind of panel]("http://ubuntuforums.org/showthread.php?t=509474")

---

