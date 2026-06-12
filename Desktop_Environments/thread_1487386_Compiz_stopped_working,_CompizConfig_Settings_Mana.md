---
title: "Compiz stopped working, CompizConfig Settings Manager no longer accessible"
date: 2010-05-18
forum: Desktop Environments
---

### Post by gogolink on 2010-05-18
I did a clean install of Ubuntu 10.04 on a Toshiba Satellite, Intel graphics card, a few days ago, and had no trouble accessing the CompizConfig Settings Manager.  I changed a number of settings, and everything seemed to be working just fine.  But two days ago, I noticed that the compiz effects (rotating desktop cube, minimize effect etc.) were gone; and when I now try to access the Settings Manager, I see a "Starting CompizConfig..." appear in the panel and linger for about five seconds; then it's gone.  No settings manager, no error message.

The day that happened, I had (to the best of my memory) not installed any updates.  I had, however, removed a bunch of applications through the Software Center.  

I had also launched Ubuntu Tweak and changed a couple of settings.  The only option it showed, and shows, under 'Compiz Settings' was then (and still is): "Prerequisite Conditions" : "Install Advanced Desktop Effects Settings Manager".  The box was checked.  I have since unchecked and re-checked it, thereby uninstalling and re-installing the settings manager.  But that hasn't changed anything.

When I type **compiz --replace** in a terminal, the screen flickers, goes back to screensaver, returns, and I see the following message in the terminal window (with the process apparently stalled):

[INDENT]gogo@gogo-laptop-toshiba:~$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

[/INDENT]

I open another terminal window, and the following additional lines appear on the first one:

[INDENT](process:5421): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
 
[/INDENT]

I have tried uninstalling and re-installing all compiz I could find, but that hasn't changed anything.

Any ideas anyone?

---

### Post by gogolink on 2010-05-19
Does it look like a driver issue?  Graphics card blacklisted?  Or did I remove some dependencies that are necessary for compiz settings manager to launch?

Any ideas?

---

### Post by chubz on 2010-05-20
Hi, I'm totally new to Ubuntu, I've installed it 3 days ago, and my friend sugested to use the after fresh install script that loads many standard and usefull aplications and settings found to be best for ubuntu.

Among other thing he said I should use compiz to see what appearance settings exists for ubuntu and to tweak it to my graphical satisfaction.

I've tried running the compiz settings manager, but have a similar situation to one above:
I click it in the System->Preferences->Compiz Settings Manager
It lingers in the lower panel for about 20 seconds, then disappears without starting the manager. 
I've installed compiz fusion to se if it works at all and sure enough it does. I can choose between metacity and compiz and between Emerald an GTK WM.

Since I am a newb, and really not sure how to troubleshoot this problem any suggestions, or even ways to get any information you need is welcome.
This isn't a crucial problem, so I'm not expecting people to jump on it but such help would be appreciated, and also a learning experience.

random info says:
when I type in the terminal ~$compiz 
(process:1935): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(process:1937): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
I/O warning : failed to load external entity "/home/chubz/.compiz/session/106b7a168819b30304127436335428112600000013320001"

also my gfx card is: Nvidia GeForce 8800 GT 512 and have selected current driver (recommended) in hardware drivers.
There is another option in the drivers which says that alternative driver version 173 is open to install but I've kept the recomended because I don't know what is the difference between the two.

EDIT:
My ubuntu is 10.04 x64 - forgot to supply that info too.


Thanks in advance from Borislav

---

### Post by gogolink on 2010-05-20
I just found [this post]("http://bbs.archlinux.org/viewtopic.php?id=45398") on a different forum about what looks like the same problem.  I'm currently not at my own machine, but will try the fix tonight when I am.

Oh, and BTW, I also ran a post-installation script after fresh install, possibly the same one?  I used W8's "Ubuntu 10.04 Start" script, which I found [here]("http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html").

---

### Post by realzippy on 2010-05-20
@gogolink

*Or did I remove some dependencies that are necessary for compiz settings manager to launch?*

...always be careful when uninstalling anything via synaptic;it is
rigorous with deleting dependencies...so that is very likely.

---

### Post by gogolink on 2010-05-20
Then how would I get my dependencies back?

---

### Post by wishingstar on 2010-05-20
Hi,

i've never had that same exact error, but i had some problems with compiz, here are a few suggestions:

In terminal add:
```
sudo apt-get build-dep compiz compizconfig-settings-manager
```This should build the dependencies for both.
I also had a similar problem with compiz after installing some extra plugins, i found that restarting the system helped on that one.

hope this helps!

WishingStar

---

### Post by realzippy on 2010-05-20
> **wishingstar said:**
> Hi,

i've never had that same exact error, but i had some problems with compiz, here are a few suggestions:

In terminal add:
```
sudo apt-get build-dep compiz compizconfig-settings-manager
```This should build the dependencies for both.
I also had a similar problem with compiz after installing some extra plugins, i found that restarting the system helped on that one.

hope this helps!

WishingStar

As far as I know...  "apt-get build-dep *packagename*" does not show a package's dependencies,it shows the necessary packages to compile that package from source.
```
apt-cache depends *packagename*

```

shows the dependencies.
General infos gives:

```
apt-cache showpkg *packagename*

```

---

### Post by wishingstar on 2010-05-20
Dear realzippy,

I'm didn't know about this command, thanks! However, the build-dep helped me when dolphin was missing some features, i removed the package, built dependencies and voila! dolphin was feature-complete :)

---

### Post by realzippy on 2010-05-20
> **wishingstar said:**
> Dear realzippy,

I'm didn't know about this command, thanks! However, the build-dep helped me when dolphin was missing some features, i removed the package, built dependencies and voila! dolphin was feature-complete :)

Maybe,but the "build-dep" packages have nothing to do with the "depends" packages...e.g. dolphin needs *kdelibs5* to run but -of course- not to compile..
But,real sorry  ;-)  ,back to topic:

---

### Post by gogolink on 2010-05-20
Voilà -- CompizConfig Settings Manager is running again.  It apparently was a **locales** problem.  The file /etc/default/locale was missing entries for LANGUAGE and LC_ALL (which accounted for the "Gtk-WARNING **: Locale not supported by C library.Using the fallback 'C' locale" I had been getting - and chubz has been getting, too...)  I fixed it by:

```
cd /etc/default
sudo gedit locale
```

...then, in gedit, adding the lines:

```
LANGUAGE="en_US.UTF-8"
LC_ALL="en_US.UTF-8"
```

...and saving.  I rebooted, tried to open CompizConfig Settings Manager, and lo and behold -- it worked!

---

