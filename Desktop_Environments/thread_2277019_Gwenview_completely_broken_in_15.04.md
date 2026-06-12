---
title: "Gwenview completely broken in 15.04"
date: 2015-05-06
forum: Desktop Environments
---

### Post by stinktier2 on 2015-05-06
I use xubuntu and every since I updated to/installed version 15.04 Vivid Vervet the Gwenview program is not working properly anyone. It doesn't show any files when switching from View to Browse, scrolling to the next or previous image in a folder doesn't work (neither by mouse, keyboard or toolbar button), no metadata are shown at all, KIPI plugins are not loaded (though installed), keyboard shortcuts don't work, the "mouse worping bug" occurs when viewing an image at 100% that is larger than screen resolution...

The strange thing is, this happens on all my computers – netbook, laptop, home PC, work PC which are all slightly different configured and hardware-wise equipped. Even a freshly installed xubuntu 15.04 on a newly-bought computer has this issue, so it cannot be a faulty upgrade from 14.10. I even switched from XFCE to LXDE on one login and the problems all persist.

I have tried several things like reinstalling Gwenview, but I am completely stumped. This is a major issue and I'm confused that I haven't found anything about it online. It can't just be me and my computers!

So if anybody here as any idea how to proceed and help me find a solution, please let me know.:-?

---

### Post by mc4man on 2015-05-06
At a min you'd likely need kio  kinit  kdelibs-bin kded5 & maybe some kde icons &  theme stuff.   That may get you basic functionality. Run from terminal to see.

---

### Post by SeijiSensei on 2015-05-06
Have you tried installing Kubuntu?  Gwenview is the native KDE graphics viewer.

---

### Post by stinktier2 on 2015-05-06
Thank you for your suggestions! :-)

> **SeijiSensei said:**
> Have you tried installing Kubuntu?  Gwenview is the native KDE graphics viewer.
No. There was no need before and I'd rather stick with xubuntu. Especially on my older hardware KDE is no fun, but I like some of them "K" software...

> **mc4man said:**
> At a min you'd likely need kio  kinit   kdelibs-bin kded5 & maybe some kde icons &  theme stuff.   That  may get you basic functionality. Run from terminal to see.

After I installed *kio* (plus dependencies) via Synaptic I finally got some error message when opening Gwenview (which still wasn't working):[INDENT=4][FONT=courier new]Could not start process
Cannot talk to klauncher: The name org.kde.klauncher5 was not provided by any .service files.[/FONT][/INDENT]

Then I installed *kinit* and finally Gwenview was somewhat working at last – browsing, folder viewing and metadata are displayed. The error message also doesn't appear anymore. Not working are my custom keyboard shortcuts, Kipi plugins and rotating the image according to camera orientation (everything is displayed in landscape format). The "mouse worping bug" also persists.
*kded5* and *kdelibs-bin* have already been installed (either previously or by *kio*).

Any ideas how to bring Gwenview now from basic functionality to fully-featured?

---

### Post by mc4man on 2015-05-06
> Any ideas how to bring Gwenview now from basic functionality to fully-featured? 
Most likely - install kubuntu-desktop/plasma-desktop or just use kubuntu itself
(- installing either of those desktop meta-packages will install **a lot** of kde stuff, most of it unneeded. You could  see if any improvement & then start removing all the extra stuff via synaptic. Would take some time & may prove fruitless.

---

### Post by Copper Bezel on 2015-05-06
That's ... kinda disappointing. I use a handful of Kapps right now on 14.04. gThumb replaced Gwenview for me recently, but Krita, which I depend on pretty heavily, is as dependent on KDE libraries as I am on Gnome. = P It is unfortunate if either KDE apps or Ubuntu's Gnome base are now less amenable to the a la carte approach.

---

### Post by stinktier2 on 2015-05-06
> **mc4man said:**
> Most likely - install kubuntu-desktop/plasma-desktop or just use kubuntu itself (- installing either of those desktop meta-packages will install **a lot** of kde stuff, most of it unneeded. You could  see if any improvement & then start removing all the extra stuff via synaptic. Would take some time & may prove fruitless.

Like I'd say, I'd rather have the dependencies fixed in xubuntu (I can't believe I'm the only one who uses Gwenview in xubuntu!) than installing 1GB of Kubuntu stuff and playing beta tester to install/remove hundreds of files.

By the way, when I start Gwenview with the Terminal I get the following output:[INDENT][FONT=courier new]Could not find drkonqi at /usr/lib/x86_64-linux-gnu/libexec/drkonqi
kf5.kiconthemes: "Theme tree: (Oxygen)"
Invalid pixmap specified.
QTimeLine::setDuration: cannot set duration <= 0
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
Invalid pixmap specified.
QTimeLine::setDuration: cannot set duration <= 0
Invalid pixmap specified.
QTimeLine::setDuration: cannot set duration <= 0
kf5.kservice.sycoca: Trying to open ksycoca from "/home/boris/.cache/ksycoca5"
Invalid pixmap specified.
QTimeLine::setDuration: cannot set duration <= 0[/FONT]
[/INDENT]

Perhaps somewhere in there is a hint what might be wrong...

---

### Post by linux-k2 on 2015-05-07
> **stinktier2 said:**
> Like I'd say, I'd rather have the dependencies fixed in xubuntu (I can't believe I'm the only one who uses Gwenview in xubuntu!) than installing 1GB of Kubuntu stuff and playing beta tester to install/remove hundreds of files.

Perhaps somewhere in there is a hint what might be wrong...

I have exactly the same problem after upgrading from 14.10 to 15.04.
It looks like gwenview is KDE5 but my main installed version is KDE4.
Yes, installing gwenview does install a lot of KDE5, but not enough.  I did try the packages suggested above, but it didn't help.
What is needed is a KDE4 version of gwenview, but I can't find one at the moment.
The version of gwenview (4:14.12.3-0ubuntu1) suggests it is KDE4, but the dependencies are KDE5.

Anyone know how to get an earlier version?  I tried looking with apt-cache but the above is the only suggestion.

---

### Post by mc4man on 2015-05-07
You all could try this - 
remove current gwenview
run autoremove or use synaptic to clear out crud
Install gdebi
Go here & download utopic gwenview package for your arch - under the Download Gwenview  section
[http://packages.ubuntu.com/utopic/gwenview](http://packages.ubuntu.com/utopic/gwenview)

Install with gdebi (- installs about 120 or so packages, if someone had bothered  fix the gdebi  Details window to be more than a couple of lines high could of  been informative for what's needed with the 15.04 version
Works pretty well out of the box, terminal if used is pretty clean

---

### Post by stinktier2 on 2015-05-11
So you don't think this issue of broken packages/depndencies will be solved by the makers of xubuntu?

---

### Post by mc4man on 2015-05-11
> **stinktier2 said:**
> So you don't think this issue of broken packages/depndencies will be solved by the makers of xubuntu?

Why would they do that?

---

### Post by Copper Bezel on 2015-05-12
If applications aren't working in their environment because of broken dependencies, then that *is *a problem for Xubuntu, pretty much by definition.  This is a package in the repositories that depends on other packages that are not presently listed as dependencies. How that should be resolved is an open question, and it might well be by making the Plasma desktop package a dependency of Gwenview in the Ubuntu repos, without changing a jot of anything to do with Xubuntu. But yeah, I'd think it'd be something the Xubuntu team would have an interest in looking into if the problem only appears on Xubuntu because those dependencies are already met in vanilla Ubuntu for some other reason.

---

### Post by mc4man on 2015-05-12
It doesn't work in 15.04 Ubuntu & likely not in any 15.04 except Kubuntu. So in that regard this is an issue for the gwenview maintainer/packager. 
Any interested user should file a bug against gwenview in 15.10

---

### Post by stinktier2 on 2015-05-12
> **mc4man said:**
> It doesn't work in 15.04 Ubuntu & likely not in any 15.04 except Kubuntu.

That's really sad as Gwenview worked for many years on all my xubuntu PCs and I've grown used to it for my work...

---

### Post by Copper Bezel on 2015-05-12
> **mc4man said:**
> It doesn't work in 15.04 Ubuntu & likely not in any 15.04 except Kubuntu. So in that regard this is an issue for the gwenview maintainer/packager. 
Any interested user should file a bug against gwenview in 15.10
Gotcha. Then yeah, that's the appropriate channel. I use vanilla Ubuntu, but I'm still on 14.04, or I would have checked.

---

### Post by mirod2 on 2015-06-01
> **mc4man said:**
> It doesn't work in 15.04 Ubuntu & likely not in any 15.04 except Kubuntu. So in that regard this is an issue for the gwenview maintainer/packager. 
Any interested user should file a bug against gwenview in 15.10

Actually gwenview doesn't quite work in kubuntu either. After the upgrade pictures are not displayed rotated, and the plugin menu is empty. So it looks like a gwenview issue, not one that xubuntu should deal with.

---

### Post by mc4man on 2015-06-01
> **mirod2 said:**
> Actually gwenview doesn't quite work in kubuntu either. After the upgrade pictures are not displayed rotated, and the plugin menu is empty. So it looks like a gwenview issue, not one that xubuntu should deal with.
Then it's definitely the packager/maintainer's issue or even gwenview upstream.  Personally don't use it or kubuntu  so no bug reports emanating from me.

---

### Post by vedavrata on 2015-07-27
> **mc4man said:**
> At a min you'd need **kio  kinit  kdelibs-bin kded5** & maybe some kde icons &  theme stuff. 
  That may get you basic functionality. 
Run from terminal to see.

I hade the same problem...
This helped me:
```
  sudo apt-get install  kio kinit kdelibs-bin kded5 
```

---

### Post by foreturiga on 2015-09-10
if the last reply doesn't help try this 
[COLOR=#444444][FONT=sans-serif]
remove as root:[/FONT][/COLOR]

[COLOR=#444444][FONT=sans-serif]sudo rm ~/.cache/ksycoca5[/FONT][/COLOR]

[COLOR=#444444][FONT=sans-serif]Rebuild database:[/FONT][/COLOR]

[COLOR=#444444][FONT=sans-serif]kbuildsycoca5 --noincremental

from [/FONT][/COLOR]https://bugs.archlinux.org/task/43485[COLOR=#444444][FONT=sans-serif]
[/FONT][/COLOR]

---

