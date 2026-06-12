---
title: "What is the Best Ubuntu Flavour?"
date: 2019-03-29
forum: Desktop Environments
---

### Post by DuckHook on 2019-03-29
**Contents:**

[Introduction]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848093#post13848093")
[Ubuntu Versions]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848094#post13848094")
[Desktop Environments, Shells, Window Managers & Display Servers]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848095#post13848095")
[Official Ubuntu Flavours]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848096#post13848096")
[Unofficial Desktop Environments]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848097#post13848097")
[Alternative Window Manager Environments]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848098#post13848098")
[FAQs]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848099#post13848099")
[Tips and Tricks]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848100#post13848100")
[HR][/HR]
**Introduction:**

> What is the best Ubuntu flavour?

Setting aside for the moment the entirely subjective nature of the question, there are so many variables and elements that go into determining what is "the best" that this question is basically unanswerable.

Admittedly, the 'buntu ecosystem has grown into a complex and multifarious collection of different versions, flavours, desktop environments and windowing systems, both official and unofficial. For Ubuntu veterans, this may be an embarrassment of riches, but for new users it is often confusing and intimidating.

What follows is an incomplete overview of how deep and broad the Ubuntu landscape is. Armed with this knowledge, users can hopefully decide for themselves what works for them and what doesn't.

> **Any flavour of Ubuntu is available for the price of a simple download. Burn some LiveUSBs. Try them all out.**

**A Few Caveats:**

[list]
[*]The following survey is representative; not exhaustive. The intent is to give enough information to enable exploration, but the actual exploring is left to the user.
[*]We do not recommend installing different Desktop Environments ("DE"s) side-by-side. While some have done this successfully, enough users have experienced problems that they serve as a warning to all. Different DEs may install conflicting or incompatible configuration files. It is not a good idea to mix these.
[*]Ubuntu is ever evolving. The following survey is a snapshot of the Ubuntu landscape as of Jammy (22.04).
[*]The survey is restricted to only such DEs and Window Manager Environments ("WME"s) as are properly Ubuntu. There are many distributions ("distros") that are "Ubuntu-based". These are independent of Canonical; their developers make their own choices and customizations. Such distros are not Ubuntu and should not be conflated with Ubuntu.
[/list]

---

### Post by DuckHook on 2019-03-29
Ubuntu offers their operating system in two interlaced versions: The LTS versions and the Standard versions.

While Standard versions come out every six months, LTS versions are offered only in the April release of even numbered years. Hence, LTS version numbers are 18.04, 20.04, 22.04, 24.04 etc. LTS stands for "Long Term Support" and, as the initialism states, such versions have longer support than Standard versions. Some flavours of LTS are supported for five years, whereas Standard versions are supported for nine months. **Ubuntu intends almost all general users to use LTS.** Standard versions are for those who:

[list]
[*]require the latest kernel/drivers for very new hardware
[*]must use the most current apps
[*]don't mind being on the upgrade hamster-wheel
[*]are knowledgeable and patient enough to fix more frequent system breakage
[*]are willing to test and report bugs and regressions
[/list]
[This wiki page]("https://wiki.ubuntu.com/Releases") shows the support period for each version, LTS and Standard. Flavours have their own support period which are usually shorter.

> 
More forum members tend to be knowledgeable about LTS versions because many members skip the Standard releases altogether. Keep this in mind when asking for help with standard versions: such help may be harder to come by.

---

### Post by DuckHook on 2019-03-29
The distinction between desktop environments, desktop shells, window managers and display servers is confusing, especially for new users. Hopefully, this brief overview will be both explanatory and helpful in setting the framework for the sections that follow.

The pretty desktop that we see on a typical Ubuntu installation is actually the result of a number of layers—one on top of another—with each successive layer more complex and resource-intensive than the one below.

The lowest layer is the Linux kernel. It is the foundation for everything else. Just above this is a large and impressive collection of tools, utilities, libraries and modules, all of which allow users to interact with the kernel. We deal with this layer primarily through the command line. Though powerful, these two layers are very technical and arcane, and are beyond the scope of this article.
[HR][/HR]
**The Display Server**

The next layer is the display server. It is the fundamental layer needed to produce a graphical environment. As of Jammy (22.04), all flavours of 'buntu use as their default the Wayland server. The display server is the foundation of your graphical interface. It creates and manipulates all of the primitive elements that make up the typical graphical experience—drawing geometric shapes, defining resolutions, setting screen boundaries, animating motion, registering mouse movements, etc.

> ***A note on X11***

X11 has been deprecated and suffers from assorted issues that are beyond the scope of this article. Wayland is the modern alternative. Canonical has decided to move to Wayland although X11 is still available as an alternative at the login screen. Use X11 with care. Although it is still available, expect Canonical to drop support for it at some point in the near future
[HR][/HR]
**The Window Manager**

To make the display server usable, the next layer is essential. This is the window manager. The WM fleshes out the skeleton of the Wayland environment by creating the desktop, the windows, borders, colours, a selection of fonts, etc. It also adds controls like slider bars and buttons that allow users to manipulate these elements easily. Some WMs add panels and docks (which turn them into Window Manager Environments), though many don't. This layer is the beginning of a truly usable graphical experience. There are many WMs available for Ubuntu. The example below shows Openbox.

[img]https://i.imgur.com/BVG3qdh.jpg[/img]
*The default Openbox is very plain and stark.*

Some users prefer the simplicity of a WM alone without further bells and whistles. This is a perfectly valid endpoint to the graphical experience and a number of distros exist that are based around a WM that is then refined into an attractive desktop. Such distros tend to be very light on resources and run well on older or less powerful hardware. In fact, it is not difficult installing such a window manager environment on Ubuntu and this is addressed in the section on [Alternative Window Manager Environments]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848098#post13848098").
[HR][/HR]
**The Shell** (or Desktop Shell)

The next layer is the desktop shell. However, the distinction between "shells" and "DEs" is admittedly vague, ambiguous and—truth be told—pedantic. Many people use the two terms interchangeably and this is perfectly acceptable. For our purposes, we will distinguish between the two in the interest of clarity: the shell positions trays, panels and docks in distinctive areas of the desktop for a look that is appealing to the eye. It also adds control panels, system dialogues, utilities, file managers, notifications, etc. These are the items that give a desktop its unique look and feel.
[HR][/HR]
**The Desktop Environment**

If the shell defines the look of the desktop, then the DE is the topmost layer and is the logical culmination of the graphical experience. In essence, it is a shell plus themes, high-level utilities and a suite of default apps chosen by its developers to produce the "total experience" that most users expect from a complete distro.

Each of the official 'buntu flavours is a DE. These are explored in the next section: [Official Ubuntu Flavours]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848096#post13848096").

---

### Post by DuckHook on 2019-03-29
When [Ubuntu attributes the status of "Flavours" to some DEs]("https://wiki.ubuntu.com/UbuntuFlavors") this just means that these are "DEs officially supported by Ubuntu". Canonical funds them and provides resources for oversight, development, maintenance and ongoing support. As we shall see, Ubuntu can run other DEs from within the Ubuntu repositories themselves, but these do not constitute flavours, because they are not officially supported.
[HR][/HR]
[**Ubuntu**]("https://www.ubuntu.com/") (sometimes called vanilla Ubuntu or plain Ubuntu)

Starting with 17.10, Ubuntu uses the [Gnome3 shell]("https://www.gnome.org/gnome-3/") on its DE, but modified from the default Gnome style to look more like the traditional Ubuntu desktop. Since most new users start with this flavour, the desktop below is representative of what such users would see.

[img]https://i.imgur.com/tWlHVSA.jpg[/img]

Ubuntu has tried to make the desktop more attractive with each passing version. It is certainly more resource-intensive than it was a few years ago. Resources are dedicated to things like 3D effects, compositing and animations. It also comes with a full suite of software. The result is a complete and pretty DE that can be sluggish on older or underpowered hardware.

Because it is Ubuntu's flagship flavour, it tends to get the most tender loving care. And because it uses Gnome Shell, it has the additional backing of the whole Gnome ecosystem. Ubuntu continues to refine the DE with each release and it is now quite solid.

The recommended way to install Ubuntu is to download the ISO from its [download website here]("https://www.ubuntu.com/download").

It can also be installed from the command line with:```
sudo apt install ubuntu-desktop
```
[HR][/HR]
[**Kubuntu**]("https://kubuntu.org/")

Kubuntu has been around for many years and is a proven entity with solid support and an enthusiastic, committed community. It uses the [KDE/Plasma shell]("https://kde.org/plasma-desktop").

[img]https://i.imgur.com/ncldcCM.jpg[/img]

Kubuntu is an attractive DE with many apps developed specifically for the KDE/Plasma environment. Some of these apps may even be considered best-in-class within the Linux ecosystem. But, like Gnome, this attractiveness comes at a similar price: Kubuntu is one of the more resource-intensive flavours in the 'buntu repertoire. It is not the best choice for old or underpowered hardware.

The KDE community is a very active and dynamic one and Kubuntu derives a lot of benefits from the work this community does.

The recommended way to install Kubuntu is to download the ISO from its [download website here]("https://kubuntu.org/getkubuntu/").

It can also be installed from the command line with:```
sudo apt install kubuntu-desktop
```

A stripped down desktop consisting of only the plasma shell can be installed with:```
sudo apt install plasma-desktop
```
[HR][/HR]
[**Xubuntu**]("https://xubuntu.org/")

Many power users swear by Xubuntu because it combines a light footprint with power and flexibility. It has been around long enough to establish itself as solid and reliable. Xubuntu uses the [xfce shell]("https://www.xfce.org/").

[img]https://i.imgur.com/4ov5phj.jpg[/img]

Many users prefer Xubuntu's simpler aesthetic to what they consider the frills and distractions of Ubuntu or Kubuntu. In return, they get a desktop that is flexible and customizable. Because its default install is so light, it also runs more responsively on old or underpowered hardware.

The recommended way to install Xubuntu is to download the ISO from its [download website here]("https://xubuntu.org/download/").

It can also be installed from the command line with:```
sudo apt install xubuntu-desktop
```

A stripped down desktop consisting of only the xfce shell can be installed with:```
sudo apt install xfce4
```
[HR][/HR]
[**Lubuntu**]("https://lubuntu.me/")

Lubuntu is even lighter than Xubuntu, at the cost of an even sparser appearance. However, this does not take away from its power or flexibility. It uses the [LXQt shell]("https://lxqt-project.org/") which sits on top of Openbox.

[img]https://i.imgur.com/B4MKVrK.jpg[/img]

Lubuntu is designed for old and underpowered hardware. Therefore, it replaces many mainstream apps with lighter and leaner alternatives. It is also stripped down to more basic operating system components. A comparison between the memory footprint of a Lubuntu installation vs an Ubuntu installation is very eye-opening. Because the basic DE is so much lighter, even some users with powerful hardware will run Lubuntu for the sake of its improved quickness and responsiveness.

Note that Lubuntu used to use a different shell, [LXDE]("https://www.lxde.org/"), which a few people still prefer over LXQt. However, this is not recommended. LXDE has been deprecated and is no longer under active development.

The recommended way to install Lubuntu is to download the ISO from its [download website here]("https://lubuntu.me/downloads/").

It can also be installed from the command line with:```
sudo apt install lubuntu-desktop
```

A stripped down desktop based on the LXQt shell can be installed from the command line with:```
sudo apt install lxqt
```
[HR][/HR]
[**Ubuntu-MATE**]("https://ubuntu-mate.org/")

Some users prefer the old Gnome2 look to Gnome3 and decided to spin a flavour based on Gnome2 using the [MATE shell]("https://mate-desktop.org/"). The result is Ubuntu-MATE.

[img]https://i.imgur.com/xyH1Cqr.jpg[/img]

MATE is lightweight because it is based on older desktop technologies that forego 3D, compositing, etc. Therefore, it not only continues the older look and feel that many users prefer; it is also more responsive than newer/heavier DEs.

The recommended way to install Ubuntu-MATE is to download the ISO from its [download website here]("https://ubuntu-mate.org/download/").

It can also be installed from the command line with:```
sudo apt install mate-desktop-environment
```

A stripped down desktop consisting of only the MATE shell can be installed with:```
sudo apt install mate-desktop
```
[HR][/HR]
[Ubuntu Budgie]("https://ubuntubudgie.org/")

[Budgie is an elegant shell]("https://github.com/BuddiesOfBudgie/budgie-desktop") that has been ported to many distros. Ubuntu officially brought Budgie into its big tent as of 17.04. It has since gained a substantial following within the Ubuntu community.

[img]https://i.imgur.com/8hN9LCM.jpg[/img]

Budgie offers some different takes on performing traditional tasks—some subtle, some not so subtle. For example, its default terminal is Tilix which is known for its tiling functionality. Budgie tries to strike a balance between old and new, combining its default dock with a more traditional upper panel. Most users pick up on its quirks and oddities without much trouble.

The recommended way to install Ubuntu Budgie is to download the ISO from its [download website here]("https://ubuntubudgie.org/downloads").

It can also be installed from the command line with:```
sudo apt install budgie-desktop-environment
```

A stripped down desktop consisting of only the Budgie shell can be installed with:```
sudo apt install budgie-desktop
```
[HR][/HR]
[Ubuntu Kylin]("https://www.ubuntukylin.com/")

Though this is an English-language forum, Kylin is included because it is an official Ubuntu flavour. It is designed primarily for use in Chinese language environments. It is a proper Ubuntu flavour and is maintained mainly by the China division of Canonical.

[img]https://i.imgur.com/OCmtAz4.jpg[/img]

The Kylin flavour is not just Ubuntu with language and environmental variables set to the Chinese language—it has its own unique app ecosystem, including Chinese alternatives for utilities and productivity software. Not surprisingly, Kylin hosts its own quite active community and forums. Kylin uses the [UKUI shell]("http://www.ukui.org/development.html"), developed in large part by Canonical's China division, and which is an extension of Ubuntu-MATE.

Note that Kylin is not restricted to only Chinese. Like any of the 'buntus, it can run in any language by simply choosing that language at setup. Additionally, UKUI can be installed on its own as an unofficial Ubuntu DE.

The recommended way to install Ubuntu Kylin is to download the ISO from its [download website here]("http://www.ubuntukylin.com/downloads").

It can also be installed from the command line with:```
sudo apt install ubuntukylin-desktop
```

If you wish to install only UKUI, this is discussed below in the section: [Unofficial Desktop Environments]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848097#post13848097")
[HR][/HR]
[Ubuntu Studio]("https://ubuntustudio.org/")

Studio is designed for A/V professionals and enthusiasts. There isn't much difference between the way Studio looks or works and the average Ubuntu install.

[img]https://i.imgur.com/VvdzMCS.jpg[/img]

While it is perfectly possible to duplicate Studio's extensive software suite in any of the other Ubuntu flavours by just installing the apps, there is little point in doing so when Studio has so conveniently put them together for you.

What is more difficult to duplicate is the fine-tuning in the utilities, the drivers and even the kernel itself that the Studio maintainers have tweaked. For example, Studio uses Jack (for its low latency) instead of Alsa/PulseAudio. Forum members who have tried to install Jack and tune it on their own can attest to how finicky the process is.

The recommended way to install Ubuntu Studio is to download the ISO from its [download website here]("https://ubuntustudio.org/download/").

It can also be installed from the command line with:```
sudo apt install ubuntustudio-desktop
```…but this is not recommended due to the difficult and exacting hand-tuning required.

---

### Post by DuckHook on 2019-03-29
Just because Ubuntu comes in eight "official" flavours doesn't mean that we are restricted to only these eight. There are a number of alternate DEs that can be easily installed through the repositories. However, the following should be noted:

[list]
[*]These are not official flavours, which means that there is no official support or even a commitment to host them on future repos. Therefore, installing these DEs means that the user is on his/her own, must accept the attendant risk and must rely on community support (instead of Launchpad, official bug reports, documentation, etc).
[*]Fewer users will be familiar with these hybrids; therefore, even community support will be less.
[*]"Unofficial" also means "not maintained". Therefore, security holes may very well go unpatched, limited effort will be expended in resolving incompatibilities, the DE may very well wither on the vine, etc.
[*]Though hybrids, many of these desktops are proper Ubuntu offspring and therefore qualify for forum support. For example, Ubuntu with the Cinnamon desktop qualifies as an Ubuntu remix and is not the same as Linux Mint. The former is installed entirely from packages in the repos, whereas Mint is an independent entity with its own developers, policies, maintenance and direction.
[/list]
> Unofficial desktops call for a different installation strategy. While it is possible to simply download DEs onto an exiting installation running, say, vanilla Ubuntu, this might cause system breakage due to conflicting/incompatible configuration files. Therefore, it is better to install either a [minimal "Netboot" image]("http://cdimage.ubuntu.com/netboot/18.04/") or a [server installation]("https://www.ubuntu.com/download/server") (ie. all CLI—no GUI components), and then install the unofficial DE through the command line, thus making it the sole DE on the system.
[HR][/HR]
**Unity**

Unity was developed by Canonical in-house for many years to serve as their common DE for not only the desktop PC, but portable devices as well. Canonical stopped development on Unity as of 17.04 and switched to GNOME3. However, one should not expect Unity to be maintained, though a large enough community of Unity enthusiasts might succeed in doing so unofficially.

[img]https://i.imgur.com/tg6v27Z.jpg[/img]

Many users still prefer the Unity desktop despite it being deprecated and now only maintained by the community. To keep the Unity experience, it is possible to install Unity on Jammy (and later versions). However, be mindful that Unity depends on Compiz, which in turn depends on X.org. Therefore, if you are using Wayland, Unity may prove problematic.

Install Unity with:```
sudo apt install ubuntu-unity-desktop
```
[HR][/HR]
**GNOME**

Although all versions of Ubuntu Artful (17.10) and higher use the GNOME3 shell, some users may prefer the default GNOME layout. This may be more comfortable to those coming from another default GNOME environment like Fedora.

[img]https://i.imgur.com/cSt2JdE.jpg[/img]

There really isn't much difference between default GNOME and Ubuntu except the initial desktop layout. The apps are the same. Most importantly, the underlying operating system structure including libraries, utilities and configurations are practically identical.

Install GNOME with:```
sudo apt install vanilla-gnome-desktop
```

A stripped down desktop consisting of only the GNOME shell can be installed with:```
sudo apt install gnome-core
```
[HR][/HR]
**Cinnamon**

[Cinnamon is a very popular shell]("http://developer.linuxmint.com/projects/cinnamon-projects.html"), made more so by the fact that the largest Ubuntu-based derivative, Linux Mint, uses this shell. Though Mint is an entirely different beast from Ubuntu, the desktop look and feel is similar when running under Cinnamon.

[img]https://i.imgur.com/Qqr4gYv.jpg[/img]

The Cinnamon shell has been around a while and has a significant track record. It is tested and stable, although how long Canonical keeps it in the repos is entirely up to them.

Install Cinnamon with:```
sudo apt install cinnamon-desktop-environment
```

A stripped down desktop consisting of only the cinnamon shell can be installed with:```
sudo apt install cinnamon-core
```
[HR][/HR]
**UKUI**

[UKUI]("http://www.ukui.org/development.html") has already been mentioned as the shell developed for Kylin. It is an extension of MATE, but has its own very different look and feel.

[img]https://i.imgur.com/TihYPwq.jpg[/img]

The UKUI shell in the repositories is quite up-to-date, reflecting perhaps the level of development that Kylin is undergoing. Note that UKUI brings in its own unique tools, like the Peony file manager. It unquestionably marches to the beat of its own drummer.

Install UKUI with:```
sudo apt install ukui-desktop-environment
```

A stripped down desktop consisting of only the UKUI shell can be installed with:```
sudo apt install ukui-desktop-environment-core
```
[HR][/HR]
**Gnome-flashback**

Many users resisted Ubuntu's change to Unity and stayed on the older DE for either aesthetic reasons or because they did not wish to disrupt their old workflow. That predecessor DE has always existed for such users with [GNOME Flashback]("https://wiki.gnome.org/Projects/GnomeFlashback") which uses [GNOME Panel]("https://wiki.gnome.org/Projects/GnomePanel").

[img]https://i.imgur.com/k0wt6JN.jpg[/img]

Note that while the resulting DE resembles MATE, MATE uses GTK 2, whereas GNOME-flashback uses GTK+ 3 which allows it to more easily keep pace with current GNOME development work.

Install GNOME flashback with:```
sudo apt install gnome-session-flashback
```
[HR][/HR]
**Kodi**

[Kodi]("https://kodi.wiki/view/Main_Page") is a specialty DE designed to turn a computer into a TV media centre. It simplifies the desktop layout to allow control through a typical TV remote.

[img]https://i.imgur.com/gWaRjdq.jpg[/img]

Kodi has a large community of developers, is under heavy development and has many add-ons to further enhance its functionality.

Kodi is unusual because it must be installed on top of an existing desktop shell. Any shell will do, so a light one like lxde-core is ideal. After this, Kodi can be installed with:```
sudo apt install kodi
```

---

### Post by DuckHook on 2019-03-29
Many experienced users prefer to forego the bloat of a DE altogether and opt for a very lean graphical environment. These people are natural candidates for more basic Window Manager Environments ("WME"s).

It is not as difficult to transition from a full-fledged DE to a WME as you might imagine. The essential elements are either already present or can be readily installed. Moreover, because they are so light, most WMEs do not drag in many dependencies. However, there's no avoiding the fact that WMEs do require more knowledge of the inner workings of Ubuntu. Moreover, if customizing, much of the work needs to be done on the command line and often involves editing config files, so it is not for everyone. But the sort of users who want to transition to WMEs are usually seasoned users who:

[list]
[*]Have become impatient with the limitations placed on them by DEs,
[*]Desire finer grained control over their user environment,
[*]Want the ability to make broad customizations,
[*]Want to forego pointless frills, bells, whistles, eye-candy and the accompanying bloat,
[*]Want to eke out maximum performance,
[*]Do not like distractions and prefer simplicity in their work environment,
[*]Like to multitask with multiple tiled or stacked windows,
[*]Are keyboard jockeys who hate reaching for the mouse.
[/list]
As you can see, WMEs have many advantages and the people who like them are not the sort to shy away from the command line.

> 
Those unfamiliar with WMEs will find that they work quite differently from DEs. The main thing to remember is that accessing apps and controls is done either through clicking the mouse on the desktop (right or left button click, depending on the WM) or through keyboard shortcuts. Window Managers do not have a "Start" button—although panels or docks can be added and customized to provide a more traditional look and feel.

[HR][/HR]
[**Openbox**]("http://openbox.org/wiki/Main_Page")

The most obvious WME is Openbox. It is obvious in the sense that many users will already have been exposed to it through Lubuntu. It is the WM on which LXQt runs and can be selected at login as an alternative choice instead of Lubuntu. Openbox is highly configurable and is not difficult to learn or understand. An example of a full WME based on openbox is the [bunsenlabs distro]("https://www.bunsenlabs.org/index.html").

[img]https://i.imgur.com/hQeURHi.jpg[/img]

For Lubuntu users, to select Openbox at login, find the Lubuntu icon on the login screen. The button location changes from version to version and depends on your display manager, so a screenshot is not especially helpful. Clicking on this icon should give you three choices: Lubuntu, LXQt and Openbox.

Openbox can be installed by itself without dragging in LXQt or the Lubuntu DE. [This Ubuntu wiki page explains Openbox]("https://help.ubuntu.com/community/Openbox") and contains enough detail to allow users to start seriously customizing Openbox.

To install Openbox:```
sudo apt install openbox
```
[HR][/HR]
[**Enlightenment**]("https://www.enlightenment.org/")

Enlightenment is one of this author's favourite Window Managers. It is under active development and has a core of committed enthusiasts who strive to steadily improve it. It has garnered support from large patrons like Samsung who use it on Tizen (Samsung's proprietary operating system). An example of a full WME based on Enlightenment is the Ubuntu-derived distro, [Bodhi]("https://www.bodhilinux.com/").

[img]https://i.imgur.com/qZfmWjA.jpg[/img]

Enlightenment is one of the prettiest WMs but, because it is a compositing WM, it also uses more resources. It is definitely not one of the lighter WMs (though still lighter than almost any DE). This may be a drawback if you want absolutely minimal resource usage. A further drawback is that the Enlightenment version in the repos depends on X11, which is not the future direction of Ubuntu.

The Enlightenment version in the repos (version .25) is somewhat old, but will give a good idea of Enlightenment's look and feel. [This short Ubuntu wiki page explains Enlightenment]("https://help.ubuntu.com/community/Enlightenment").

To install Enlightenment:```
sudo apt install enlightenment
```
[HR][/HR]
[**fvwm**]("http://www.fvwm.org/")

fvwm has a long track record and goes back to the beginnings of 'nix graphical development (1993!). It is well maintained and very stable. It is the WM used for the charming [Puppy Linux]("http://puppylinux.com/") distro.

[img]https://i.imgur.com/tHBcm8Z.jpg[/img]

fvwm is ultra light and responsive. However, it is also very sparse. In its default state, it isn't pretty, but it is fast. Unlike Openbox and Enlightenment, it doesn't coddle you. One must be proficient with the command line to seriously customize fvwm.

Note that the fvwm version in the repos is not the latest, but still supported and will give you a good indication of its look and feel. [This Ubuntu wiki page explains fvwm]("https://help.ubuntu.com/community/FVWM").

To install fvwm:```
sudo apt install fvwm
```

We can see an example of fvwm customization by installing the fvwm-crystal extension. This extension turns the extremely sparse fvwm into a more sophisticated and reasonably attractive WME. Even a little customization goes a long way.

[img]https://i.imgur.com/EBVqLtG.jpg[/img]

Note that fvwm-crystal is a lightly maintained project with no new release since 2016. It is included here for illustrative purposes.

To install fvwm-crystal:```
sudo apt install fvwm-crystal
```
[HR][/HR]
[**Fluxbox**]("http://fluxbox.org/")**/Blackbox**

Another ancient WM is Fluxbox which—if we think of WMs as already being "lightweight"—can only be described as "featherweight". But Fluxbox is itself derived from Blackbox, which is even lighter. However, Blackbox is so austere that it is difficult conceiving of anyone actually using it. Therefore, the example given is Fluxbox.

[img]https://i.imgur.com/5fKYuhX.jpg[/img]

[This Ubuntu wiki page explains Fluxbox]("https://help.ubuntu.com/community/Fluxbox"). As with all WMEs, be prepared to delve into the obscurity of the command line if you want to seriously customize Fluxbox. The trade-off is that you get a very fast and nimble computing experience that just nibbles at your resources. Combined with carefully selected minimalist apps and you could run a functional system on less than 512 MB of RAM.

To install Fluxbox:```
sudo apt install fluxbox
```
[HR][/HR]
[**Window Maker**]("https://www.windowmaker.org/")

Window Maker's claim to fame is its resemblance to NeXTStep. For the nostalgic, this WM may just bring back distant memories of computing's halcyon garage-hacker roots. It is not heavily developed and, though still active, only generates the odd release every few years. It is included in this survey to give a sense of the variety that can be found within the Ubuntu ecosystem.

[img]https://i.imgur.com/uDLktq8.jpg[/img]

Window Maker does have a few graceful notes. It has an extensive graphical configuration panel that saves having to monkey around with configuration files. It possesses the property that so many users call "intuitive". And it is unquestionably retro.

To install Window Maker:```
sudo apt install wmaker
```
[HR][/HR]
[**Awesome**]("https://awesomewm.org/")

Awesome is a somewhat hubristically named WME that is built around the concept of tiling. Windows can be automatically tiled into a number of different tiling schemes using keyboard controls. Switching window focus is also done through keystrokes. For multi-taskers with large or multiple screens who detest the mouse, this layout can be appealing.

[img]https://i.imgur.com/RmyHahs.jpg[/img]

Awesome is highly configurable and extendable, but doing so requires you to edit LUA files. This is not a trivial exercise. Moreover, as WMs go, it is not one of the leaner ones. So, if you are looking for something ultra lean, you may want to look elsewhere.

To install Awesome:```
sudo apt install awesome
```
[HR][/HR]
[**i3wm**]("https://i3wm.org/")

i3wm is a lean, mean tiling machine. A system running i3wm sips a fraction of the computing resources that even Lubuntu uses, thus making it a good choice for really old hardware. It is another tiling WME that turns computing sessions into no-nonsense simplified productivity environments.

[img]https://i.imgur.com/IqIqwkx.jpg[/img]
*A default i3wm desktop is brutally austere, but once an app or three is launched (and auto-tiled), it's not so bad.*

Like all tiling WMEs, i3wm is an acquired taste. It is highly configurable and its configuration files are plain text files, which make them a bit easier to read, understand, edit and configure. It is also keyboard focused; one can go a whole session without touching the mouse. In fact, this is how it is designed to be used.

To install i3wm:```
sudo apt install i3
```
[HR][/HR]
**A Wealth of WMEs**

There are dozens of WMs in the repos and this brief survey has not even scratched the surface. You are welcome to explore on your own and are encouraged to try them out. [This page provides all of the WMs that work in Jammy]("https://packages.ubuntu.com/jammy/x11/").

> **! CAUTION !**
Most older WMs are not designed to work with Wayland but rather with X11. Although Wayland has some backward compatibility with X11, this is not complete. Running a WM in Wayland may generate display or audio artifacts or other quirky behaviour. Therefore, running a WM may require committing to X11 with all of the future limitations and obsolescence issues that this implies.

---

### Post by DuckHook on 2019-03-29
> I don't want to install test DEs or WMEs on my main OS. What is the best way to try them out?
Where the option exists, run a LiveUSB. Where it does not, try running them in a VM.
[HR][/HR]
> I've installed too many DEs on my main OS. How do I remove some of them?
Unfortunately, the act of installing a DE is a one-way valve. Once installed, they are almost impossible to remove. The concise installation commands offered above actually installs what is called a "meta-package". This is like a box that contains hundreds of parts inside. Deleting the meta-package only deletes the box. The parts are still strewn all over your OS. You would have to remove each of the parts separately, and that is like trying to put Humpty Dumpty back together again. It's another reason why we don't recommend mixing DEs; they are almost impossible to extricate from each other. For a possible (though still problematic) workaround, please see [Tips and Tricks]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848100#post13848100").
[HR][/HR]
> I have installed an ultra-light WME on my old laptop, so why is Firefox still so slow?
Modern heavy-duty browsers like Firefox and Chromium are resource hogs that more than offset whatever resource savings you eke out of your OS. This is why distros designed for lightness do not include mainstream browsers or software suites. Try a lightweight browser like Epiphany, Dillo or Midori instead. If you are really short of resources, try Links2. Warning: Links2 is extremely primitive: no scripting, cookies or HTML5. The upside is that malware won't run on it either.
[HR][/HR]
> How can I reduce resource usage even further?
Other common resource hogs are office suites and graphics apps. Alternatives to the two biggest LibreOffice apps are Abiword and Gnumeric. Alternatives to GIMP are Pinta (which may be too primitive), Krita (more powerful, but primarily a KDE app which will drag in a lot of dependencies if not running Qt) and Shotwell (for simple photo touchup). Unfortunately, the unavoidable trade-off for lightness is functionality.
[HR][/HR]
> How can I install and set up my WM easily?
The easiest way is to first install Ubuntu Server, then a minimal desktop shell like:```
sudo apt install lxqt
```…which automatically sets up things like display managers, audio, networking, graphics, etc but without any extraneous apps or utilities, and finally the WM. Thereafter, choose the WME at login and ignore the DE.
[HR][/HR]
> You advised us to not mix DEs. So why mix a DE and a WM?
[LIST]
[*]WMs are much lighter than DEs, have a small number of dependencies and tend to make few (if any) changes to config files, registries, etc.
[*]They are designed from the outset to replace existing WMs for purposes of customization. Advanced users routinely replace the WM in their DE.
[*]It's a value judgment that trades off a small potential instability for a large real gain in functionality.
[*]That said, careful users will forego the DE, install only the X.org server, then the WM, then start the WM from the command line.
[/LIST]
[HR][/HR]
> What WMs are available for Wayland?
Many of the WMs linked above will be obsolesced once X.org is deprecated, but compositing WMs are being ported to Wayland (including Enlightenment and i3wm among others), so things are moving along. Like all technological progress, there is a period of transition when old tools won't work and new tools are not yet ready for prime time. We simply have to be patient until the new tools are in place.

---

### Post by DuckHook on 2019-03-29
**Recording DE Dependencies**

For those insisting on adding a second DE to an existing one, a possible strategy is to first simulate the install on a GUI terminal by running, for example, ```
sudo apt -s install lubuntu-desktop
```…which will yield something like the following:
```
The following NEW packages will be installed
  blueman bluez bluez-obexd cracklib-runtime evince evince-common fcitx fcitx-bin fcitx-config-common fcitx-config-gtk
  fcitx-config-gtk2 fcitx-data fcitx-frontend-all fcitx-frontend-gtk2 fcitx-frontend-gtk3 fcitx-frontend-qt4 fcitx-frontend-qt5
  fcitx-module-dbus fcitx-module-kimpanel fcitx-module-lua fcitx-module-x11 fcitx-modules fcitx-ui-classic ffmpegthumbnailer
  file-roller fonts-noto-color-emoji galculator giblib1 gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gudev-1.0
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gnome-disk-utility gnome-screenshot gpicview gsettings-ubuntu-schemas gtk2-engines gtklp
  htop indicator-application indicator-application-gtk2 indicator-sound indicator-sound-gtk2 leafpad libavfilter6 libcompfaceg1
  libcrack2 libevdocument3-4 libevview3-3 libfcitx-config4 libfcitx-core0 libfcitx-gclient1 libfcitx-qt5-1 libfcitx-utils0
  libffmpegthumbnailer4v5 libfm-data libfm-extra4 libfm-gtk-data libfm-gtk4 libfm-modules libfm4 libgettextpo0 libido-0.1-0
  libkeybinder0 libmenu-cache-bin libmenu-cache3 libnautilus-extension1a libobrender32v5 libobt2v5 libpisock9 libpresage-data
  libpresage1v5 libpwquality-common libpwquality1 libqt4-dbus libqt4-declarative libqt4-network libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-xml libqt4-xmlpatterns libqtcore4 libqtdbus4 libqtgui4 libtinyxml2.6.2v5 libuniconf4.6
  liburl-dispatcher1 libusb-0.1-4 libwvstreams4.6-base libwvstreams4.6-extras lubuntu-artwork lubuntu-artwork-18-04
  lubuntu-default-session lubuntu-default-settings lubuntu-desktop lubuntu-gtk-core lubuntu-gtk-desktop lubuntu-icon-theme
  lubuntu-lxpanel-icons lxappearance lxappearance-obconf lxde-common lxde-core lxhotkey-core lxhotkey-data lxhotkey-gtk
  lxhotkey-plugin-openbox lxinput lxlauncher lxlock lxmenu-data lxpanel lxpanel-data lxpanel-indicator-applet-plugin lxpolkit
  lxrandr lxsession lxsession-data lxsession-default-apps lxsession-logout lxshortcut lxtask lxterminal mtpaint neofetch obconf
  obsession openbox openbox-lxde-session openbox-menu pcmanfm plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text presage
  pulseaudio-module-bluetooth qdbus qt-at-spi qtchooser qtcore4-l10n scrot sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins
  syslinux-legacy ttf-ubuntu-font-family ubuntu-report usb-creator-common usb-creator-gtk wvdial xfonts-100dpi xpad
```
This output can then be saved as a text file. Should the user decide afterwards that the new DE is not required, this saved list of packages can be used to remove them just as quickly with:```
sudo apt -purge "copy of package list"
```

> :!: **WARNING** :!:
While this procedure might back out the packages that make up the second DE, it will not revert any changes made to configuration files, registries, systemd, etc. More importantly, this tactic might break the dependency structure of dpkg especially if other apps were subsequently installed, resulting in a condition commonly called "dependency hell". Therefore, mixing DEs remains a fraught exercise and is still not recommended.

[HR][/HR]
**Listing all Ubuntu DEs**

A list of all the 'buntu DEs in the repo can be obtained with:```
apt show *-desktop *-desktop-environment
```…which will produce a list of all the DE variants in the repos, including those that depart even slightly from each other.

The resulting list is long and unfortunately mixes in utilities with the same package naming convention (you should ignore these). You can pipe the output to a file to review at your leisure.

Since the apt show command includes a package's dependencies, this is also useful in getting a sense of the size of the download. Note, however, that the listed packages likely have further dependencies of their own. Also, this command only shows packages calling themselves "desktops" and therefore, misses most desktop shells.
[HR][/HR]
**Crafting Highly Customized DEs**

Some power users prefer to install a plain CLI environment initially, then only a minimal desktop shell, then only the apps they want. This results in a highly customized DE that is about as lean as is reasonably achievable.

The best way to get a plain CLI install is to use the [server image]("https://ubuntu.com/download/server").

Since there are so many DEs available and so many personal preferences involved, users can build their own strategies based on the following general example:
[LIST=1]
[*]Install the server image.
[*]```
sudo apt install xfce4
```
[*]```
sudo apt install <desired app pkgs>
```
[/LIST]> Vanilla Ubuntu also offers an option called "Minimal Installation" on its setup screen. This setup option foregoes the apps that are part of a normal installation, but it is not a truly "minimal" DE, because it still uses GNOME3 which is anything but minimal. For a truly minimal DE, it is best to use one of the natively light DEs.
[HR][/HR]

---

