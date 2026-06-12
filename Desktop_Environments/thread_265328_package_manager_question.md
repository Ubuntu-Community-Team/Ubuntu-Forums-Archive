---
title: "package manager question"
date: 2006-09-25
forum: Desktop Environments
---

### Post by MightyFlea on 2006-09-25
Hi folks,

I have a question regarding package managers (synaptic, adept, kynaptic, etc.)

So far I have been using aptitude, which works rather well - however finding packages is somewhat uncomfortable. Now there are some nice GUI package managers out there (see above), but they all seem to be missing the one feature that aptitude has and I do not want to live without:

Aptitude marks packages that were auto-installed as dependencies. This enables you to see what is on your system because you wanted it, and what just got pulled in through a dependency. Also it uninstalls auto-installed packages when the last package that depends on it is uninstalled.
So this is a very nice feature that helps a lot with keeping your system nice and tidy.

So, my question: Is this feature available in any decent GUI package managers? Does it maybe need configuration to be enabled? Or am I stuck with choosing between nice GUI and superior functionality? ;-)

Help please!

Cheers,

MightyFlea

---

### Post by JAwuku on 2006-09-26
Yes, I've just discovered aptitude. It makes installing KDE/XFCE a breeze, for all you need to do is

**sudo aptitude update**
**sudo aptitude install kubuntu-desktop**

and it installs everything. You can just as easily remove KDE by using  **sudo aptitude remove kubuntu-desktop** instead of install.

Looking at [http://ubuntuforums.org/showthread.php?t=37736](http://ubuntuforums.org/showthread.php?t=37736)

it states there is a menu system for aptitude, if you type ```
sudo aptitude
``` on its own.

---

### Post by MightyFlea on 2006-09-26
> **JAwuku said:**
> Yes, I've just discovered aptitude. It makes installing KDE/XFCE a breeze, for all you need to do is

**sudo aptitude update**
**sudo aptitude install kubuntu-desktop**

and it installs everything. You can just as easily remove KDE by using  **sudo aptitude remove kubuntu-desktop** instead of install.
true..
(I was just going to point out that you can do the same with apt-get, but that is actually the point - if you installed with apt-get and uninstall kubuntu-desktop, all the packages you installed stay there and have to be uninstalled by hand.)
But why would you want to uninstall kubuntu-desktop anyway? ;-)
> **JAwuku said:**
> Looking at [http://ubuntuforums.org/showthread.php?t=37736](http://ubuntuforums.org/showthread.php?t=37736)

it states there is a menu system for aptitude, if you type ```
sudo aptitude
``` on its own.
Hmmyes.. I know. And I will likely stick to aptitude.
But the filter / search functions of adept are really quite nice. I want the best of both worlds.. is that too much to ask? ;-)

---

### Post by JAwuku on 2006-09-26
I think there ***is*** a GUI equivalent of aptitude:

from the website [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

to quote:

> However, there is a graphical version of aptitude. For Ubuntu, it's Synaptic Package Manager. For Kubuntu, it's Adept. In both, you're essentially doing the same thing. There's also a nice "browsing" environment in which you can search for packages by name and/or description. You can browse by categories of software or look at what's installed versus what's not installed. It's a lot like an ecommerce model of "shopping" for software, except you don't have to pay when you "check out." The equivalent of sudo aptitude update is clicking the Reload button. The sudo aptitude install command, however, is broken into different steps. Instead of listing a bunch of applications you want to install, you mark each one for installation (or removal), and then click Apply Changes or Commit Changes and then everything's downloaded and installed (or uninstalled). [I've written another guide on how to use Synaptic Package Manager]("http://www.psychocats.net/essays/winuxinstall.php") (complete with screenshots), in case you need pictures to see what it's all about.


BTW I've tried all 3 desktops, and have settled with Gnome (a bit faster and more stable than KDE IMHO);) , but I insist on k3b and Amarok. Beats anything equivalent in Gnome! KDE I have to admit does look nicer and is more intuitive, especially the new Kubuntu Edgy Knot 3 theme :cool:

---

### Post by MightyFlea on 2006-09-26
Thank you!

Well, unfortunately, if you read on a bit:
> **The advantages of aptitude over apt-get**
 aptitude has an important feature that its command-line cousin apt-get and the graphical frontends Synaptic and Adept do not have--it remembers dependencies. If you update with aptitude, install with aptitude, and then uninstall with aptitude, all the dependencies you installed with a particular package will be removed when that package is removed (unless other packages also depend on those dependencies). If you install with Synaptic, Adept, or apt-get, uninstalling will uninstall only the package you specify--not the dependencies that came with it.
So this confirm once more that what I am looking for is not there.

I am going to live with aptitude. For searching the repositories in a more comfortable way there is always packages.ubuntu.com after all.

Especially since lately I discovered a way around the one problem I have with the auto-uninstall in aptitude - by default, packages that are only suggested get deinstalled unless you install them manually (which defeats the auto-cleanup niceness).
if you add the line
```
aptitude::Keep-Suggests "true";
```
to the file ~/.aptitude/options it keeps those suggestions around once they are installed, until the last packages suggesting it (or depending on it, of course) is uninstalled.
You still have to install the packages manually though - so if I want to install a suggested package, i press "+" (for installing) followed immediately by "M" (for marking it as auto-installed). This is case-sensitive by the way, pressing "m" works the other way round - it clears the autoinstalled-flag.

(For good measure I also added ```
aptitude::Keep-Recommends "true";
``` to my options file, but I think that is the default anyway.)

(PS I've been jumping back and forth between Gnome and KDE, whenever I ran into a particular problem that the other desktop environment did not have in the distribution i used at the time.
But since I am using KDE at the moment, I just could not bring myself to not making that comment.. ;-) )

---

