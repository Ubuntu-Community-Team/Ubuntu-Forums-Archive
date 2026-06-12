---
title: "App Launcher Removal"
date: 2018-02-08
forum: Desktop Environments
---

### Post by arc- on 2018-02-08
How do I remove this, I do not recall installing it, so I want it removed. 
I have found in my /usr/share/applications/ App Lanucher, and I want to know how to remove it? 
I can not find it. I have changed dir in the command line to /usr/share/applications$ and did "ls" and I don't see "App Lanucher" anywhere, 
what am I doing wrong and how do I find it and remove it?
Xubuntu 16.04 Newly installed

---

### Post by vasa1 on 2018-02-08
> I do not recall installing it, so I want it removed. 
That may not be a valid reason! We don't install most software ourselves. They're part of the distro.
> "ls" and I don't see "App Lanucher" anywhere,That's because the filename as seen by "ls" *maybe* different than the filename you and I see in our file manager! The name in the file manager is supposed to be friendlier. So something like gedit (technical name) maybe seen as "text editor" or something.

If you want to see the technical name for App Launcher, right-click on the appropriate icon in your file manager and choose to open it with a plain text editor. Look at the Exec= line.

---

### Post by arc- on 2018-02-08
Thanks, because the last time i tried to check it out, I clicked on it, and it went to my "panel" and it would not come off, I tried to "right click" and nothing. I tried to "right click on it" in Whiskers menu, nothing. So I am getting concerned. I just want it gone. I will try to right click and see what happens, I post a photo of what I see, But really just want it gone. Is there another way to find out what it belongs to, and just remove that?

---

### Post by vasa1 on 2018-02-08
Until it's clear what the Exec= line is, I wouldn't be in favor of removing it.

Meanwhile, edit your first post to tell people exactly which version of Linux you're using.

---

### Post by arc- on 2018-02-08
When I right click in Whiskers, I have 3 choices, add to favorites, desktop or panel.

---

### Post by arc- on 2018-02-08
> **arc- said:**
> When I right click in Whiskers, I have 3 choices, add to favorites, desktop or panel.

I right clicked on it, in the /usr/share/applications/ and this is what I  saw, and what concerns me the most is the owner "root" not sure what  that means, could use some help. See attached. Thanks. [ATTACH=CONFIG]278477[/ATTACH][ATTACH=CONFIG]278478[/ATTACH][ATTACH=CONFIG]278479[/ATTACH][ATTACH=CONFIG]278480[/ATTACH]

Let me know what you think?

---

### Post by arc- on 2018-02-08
I just checked the exe line and this is what I see:

[Desktop Entry]
Name=App Launcher
Comment=Panel based Application Launcher
Exec=mb-applet-menu-launcher
Type=PanelApp
Icon=mbmenu.png
Categories=Panel;Utility;MB

---

### Post by arc- on 2018-02-08
I found this site [https://www.apt-browse.org/browse/debian/wheezy/main/i386/matchbox-panel/0.9.3-8/](https://www.apt-browse.org/browse/debian/wheezy/main/i386/matchbox-panel/0.9.3-8/) 
It looks like something called "matchbox" I have never installed that, and never heard of it. So how do I get rid of it?

---

### Post by arc- on 2018-02-08
I found this, in "apt-cache search matchbox panel"
matchbox-panel - desktop panel for resource-limited systems
matchbox-panel-manager - panel manager for matchbox-panel
So now my question is:
How did this get on my comp, as I did not or do not remember installing it.
What's the best way to get rid of it?
Is it attached to something else I installed?
Can I just remove and purge it?
Thanks again for your help.

---

### Post by again? on 2018-02-08
You've most likely installed it somewhere along the line as a dependency
What does this tell you...
```
apt policy *matchbox*
```

The "App Launcher" is installed by matchbox-panel.
```
**[COLOR="#006400"]glen@Xubarty:~$[/COLOR] dpkg -S /usr/share/applications/mb-applet-menu-launcher.desktop**
matchbox-panel: /usr/share/applications/mb-applet-menu-launcher.desktop
```

Uninstall matchbox-panel.
```
sudo apt remove matchbox-panel
```
Then cleanup...
```
sudo apt update
sudo apt autoremove
```

---

### Post by vasa1 on 2018-02-08
Please wait until a Xubuntu user comes along before removing anything.

I have Xubuntu 16.04.3 in a KVM and I don't have any "App Launcher". So it's clearly non-standard, and installed by you or by someone with admin access to your system.

Just because something is owned by *root* isn't reason to panic. Check out the ownership of other applications.

---

### Post by vasa1 on 2018-02-08
```
zgrep -i matchbox /var/log/dpkg.log*
```may show when it was installed if you have a relatively new system.

By the way, it doesn't seem to be anything nasty:```
$ apt show matchbox
Package: matchbox
Version: 1:5
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Moray Allan <moray@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 27.6 kB
Depends: matchbox-common, matchbox-window-manager, matchbox-desktop, matchbox-panel, matchbox-panel-manager, matchbox-keyboard
...
Description: base X environment for resource-limited systems

$ 

```

---

### Post by arc- on 2018-02-08
It was installed on 2 Feb, and it was half-installed, then unpacked, and then half-configured, then installed.

---

### Post by arc- on 2018-02-08
> **vasa1 said:**
> Please wait until a Xubuntu user comes along before removing anything.

I have Xubuntu 16.04.3 in a KVM and I don't have any "App Launcher". So it's clearly non-standard, and installed by you or by someone with admin access to your system.

Just because something is owned by *root* isn't reason to panic. Check out the ownership of other applications.

Thanks, I'll wait,

---

### Post by arc- on 2018-02-08
> **guber2 said:**
> You've most likely installed it somewhere along the line as a dependency
What does this tell you...
```
apt policy *matchbox*
```

The "App Launcher" is installed by matchbox-panel.
```
**[COLOR=#006400]glen@Xubarty:~$[/COLOR] dpkg -S /usr/share/applications/mb-applet-menu-launcher.desktop**
matchbox-panel: /usr/share/applications/mb-applet-menu-launcher.desktop
```

Uninstall matchbox-panel.
```
sudo apt remove matchbox-panel
```
Then cleanup...
```
sudo apt update
sudo apt autoremove
```

I see this, not sure what it means.

apt policy matchbox
matchbox:
  Installed: (none)
  Candidate: 1:5
  Version table:
     1:5 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe i386 Packages

What does "installed (none)" mean?

---

### Post by again? on 2018-02-09
> **arc- said:**
> I see this, not sure what it means.

apt policy matchbox
matchbox:
  Installed: (none)
  Candidate: 1:5
  Version table:
     1:5 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe i386 Packages

What does "installed (none)" mean?

"Installed:" shows what version is installed. If it is not installed it will show "(none)".
"Candidate:" shows what version is available to install
If you run the original command with the included asterisks it will search for all packages with matchbox in the name.

```
apt policy *matchbox*
```
If you prefer a GUI, use synaptic where it may be clearer.
When you choose to install the package matchbox it installs other packages as dependencies... including matchbox-panel which contains the "App Launcher" file.
[ATTACH=CONFIG]278483[/ATTACH] [ATTACH=CONFIG]278484[/ATTACH]

When you uninstall the package "matchbox", the other packages installed as dependencies remain installed.
There is no harm to leave these packages but it is considered good house keeping to every now and then run....
```
sudo apt autoremove
```

From man apt
> **autoremove** 
autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now no longer needed
as dependencies changed or the package(s) needing them were removed in the meantime.

---

### Post by arc- on 2018-02-09
> **guber2 said:**
> "Installed:" shows what version is installed. If it is not installed it will show "(none)".
"Candidate:" shows what version is available to install
If you run the original command with the included asterisks it will search for all packages with matchbox in the name.

```
apt policy *matchbox*
```
If you prefer a GUI, use synaptic where it may be clearer.
When you choose to install the package matchbox it installs other packages as dependencies... including matchbox-panel which contains the "App Launcher" file.
[ATTACH=CONFIG]278483[/ATTACH] [ATTACH=CONFIG]278484[/ATTACH]

When you uninstall the package "matchbox", the other packages installed as dependencies remain installed.
There is no harm to leave these packages but it is considered good house keeping to every now and then run....
```
sudo apt autoremove
```

From man apt

I re-ran it with quotes and it was the same.
I have a question, if you look at the attached photos, It looks like it is on the system, somehow.
So does this mean that it is not installed, but only or maybe part installed.

```
2018-02-02 09:54:25 install libmatchbox1:amd64 <none> 1.9-osso8-3.1
2018-02-02 09:54:25 status half-installed libmatchbox1:amd64 1.9-osso8-3.1
2018-02-02 09:54:25 status unpacked libmatchbox1:amd64 1.9-osso8-3.1
2018-02-02 09:54:25 status unpacked libmatchbox1:amd64 1.9-osso8-3.1
2018-02-02 09:54:25 install matchbox-common:all <none> 0.9.1-5
2018-02-02 09:54:25 status half-installed matchbox-common:all 0.9.1-5
2018-02-02 09:54:25 status unpacked matchbox-common:all 0.9.1-5
2018-02-02 09:54:25 status unpacked matchbox-common:all 0.9.1-5
2018-02-02 09:54:26 install matchbox-panel:amd64 <none> 0.9.3-8.1
2018-02-02 09:54:26 status half-installed matchbox-panel:amd64 0.9.3-8.1
2018-02-02 09:54:26 status half-installed matchbox-panel:amd64 0.9.3-8.1
2018-02-02 09:54:26 status unpacked matchbox-panel:amd64 0.9.3-8.1
2018-02-02 09:54:26 status unpacked matchbox-panel:amd64 0.9.3-8.1
2018-02-02 09:54:26 install matchbox-panel-manager:amd64 <none> 0.1-6
2018-02-02 09:54:26 status half-installed matchbox-panel-manager:amd64 0.1-6
2018-02-02 09:54:26 status half-installed matchbox-panel-manager:amd64 0.1-6
2018-02-02 09:54:26 status unpacked matchbox-panel-manager:amd64 0.1-6
2018-02-02 09:54:26 status unpacked matchbox-panel-manager:amd64 0.1-6
2018-02-02 09:54:28 configure libmatchbox1:amd64 1.9-osso8-3.1 <none>
2018-02-02 09:54:28 status unpacked libmatchbox1:amd64 1.9-osso8-3.1
2018-02-02 09:54:28 status half-configured libmatchbox1:amd64 1.9-osso8-3.1
2018-02-02 09:54:28 status installed libmatchbox1:amd64 1.9-osso8-3.1
2018-02-02 09:54:28 configure matchbox-common:all 0.9.1-5 <none>
2018-02-02 09:54:28 status unpacked matchbox-common:all 0.9.1-5
2018-02-02 09:54:28 status half-configured matchbox-common:all 0.9.1-5
2018-02-02 09:54:28 status installed matchbox-common:all 0.9.1-5
2018-02-02 09:54:28 configure matchbox-panel:amd64 0.9.3-8.1 <none>
2018-02-02 09:54:28 status unpacked matchbox-panel:amd64 0.9.3-8.1
2018-02-02 09:54:28 status half-configured matchbox-panel:amd64 0.9.3-8.1
2018-02-02 09:54:29 status installed matchbox-panel:amd64 0.9.3-8.1
2018-02-02 09:54:29 configure matchbox-panel-manager:amd64 0.1-6 <none>
2018-02-02 09:54:29 status unpacked matchbox-panel-manager:amd64 0.1-6
2018-02-02 09:54:29 status half-configured matchbox-panel-manager:amd64 0.1-6
2018-02-02 09:54:29 status installed matchbox-panel-manager:amd64 0.1-6
```

```
zgrep -i matchbox /var/log/dpkg.log
```

---

### Post by again? on 2018-02-09
If "**apt policy *matchbox***" shows "(none)" for all packages then nothing is installed and you should no longer have "App Launcher" in your menu.

I see similar output for "zgrep -i matchbox /var/log/dpkg.log" where I have been installing and uninstalling matchbox packages while testing.
```
glen@Xubarty:~$ zgrep -i matchbox /var/log/dpkg.log
2018-02-09 11:41:27 install libmatchbox1:amd64 <none> 1.9-osso8-4
2018-02-09 11:41:27 status half-installed libmatchbox1:amd64 1.9-osso8-4
2018-02-09 11:41:27 status unpacked libmatchbox1:amd64 1.9-osso8-4
2018-02-09 11:41:27 status unpacked libmatchbox1:amd64 1.9-osso8-4
2018-02-09 11:41:27 install matchbox-common:all <none> 0.9.1-6
2018-02-09 11:41:27 status half-installed matchbox-common:all 0.9.1-6
2018-02-09 11:41:27 status unpacked matchbox-common:all 0.9.1-6
2018-02-09 11:41:27 status unpacked matchbox-common:all 0.9.1-6
2018-02-09 11:41:27 install matchbox-panel:amd64 <none> 0.9.3-9
2018-02-09 11:41:27 status half-installed matchbox-panel:amd64 0.9.3-9
2018-02-09 11:41:27 status half-installed matchbox-panel:amd64 0.9.3-9
2018-02-09 11:41:27 status unpacked matchbox-panel:amd64 0.9.3-9
2018-02-09 11:41:27 status unpacked matchbox-panel:amd64 0.9.3-9
2018-02-09 11:41:27 install matchbox-panel-manager:amd64 <none> 0.1-7
2018-02-09 11:41:27 status half-installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 11:41:27 status half-installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 11:41:27 status unpacked matchbox-panel-manager:amd64 0.1-7
2018-02-09 11:41:27 status unpacked matchbox-panel-manager:amd64 0.1-7
2018-02-09 11:41:28 configure matchbox-common:all 0.9.1-6 <none>
2018-02-09 11:41:28 status unpacked matchbox-common:all 0.9.1-6
2018-02-09 11:41:28 status half-configured matchbox-common:all 0.9.1-6
2018-02-09 11:41:28 status installed matchbox-common:all 0.9.1-6
2018-02-09 11:41:28 configure matchbox-panel-manager:amd64 0.1-7 <none>
2018-02-09 11:41:28 status unpacked matchbox-panel-manager:amd64 0.1-7
2018-02-09 11:41:28 status half-configured matchbox-panel-manager:amd64 0.1-7
2018-02-09 11:41:28 status installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 11:41:28 configure libmatchbox1:amd64 1.9-osso8-4 <none>
2018-02-09 11:41:28 status unpacked libmatchbox1:amd64 1.9-osso8-4
2018-02-09 11:41:28 status half-configured libmatchbox1:amd64 1.9-osso8-4
2018-02-09 11:41:28 status installed libmatchbox1:amd64 1.9-osso8-4
2018-02-09 11:41:28 configure matchbox-panel:amd64 0.9.3-9 <none>
2018-02-09 11:41:28 status unpacked matchbox-panel:amd64 0.9.3-9
2018-02-09 11:41:28 status half-configured matchbox-panel:amd64 0.9.3-9
2018-02-09 11:41:28 status installed matchbox-panel:amd64 0.9.3-9
2018-02-09 11:55:24 status installed matchbox-panel:amd64 0.9.3-9
2018-02-09 11:55:25 remove matchbox-panel:amd64 0.9.3-9 <none>
2018-02-09 11:55:25 status half-configured matchbox-panel:amd64 0.9.3-9
2018-02-09 11:55:25 status half-installed matchbox-panel:amd64 0.9.3-9
2018-02-09 11:55:25 status half-installed matchbox-panel:amd64 0.9.3-9
2018-02-09 11:55:25 status config-files matchbox-panel:amd64 0.9.3-9
2018-02-09 11:55:25 status config-files matchbox-panel:amd64 0.9.3-9
2018-02-09 11:55:25 status config-files matchbox-panel:amd64 0.9.3-9
2018-02-09 11:55:25 status not-installed matchbox-panel:amd64 <none>
2018-02-09 12:25:24 status installed libmatchbox1:amd64 1.9-osso8-4
2018-02-09 12:25:24 remove libmatchbox1:amd64 1.9-osso8-4 <none>
2018-02-09 12:25:24 status half-configured libmatchbox1:amd64 1.9-osso8-4
2018-02-09 12:25:24 status half-installed libmatchbox1:amd64 1.9-osso8-4
2018-02-09 12:25:25 status config-files libmatchbox1:amd64 1.9-osso8-4
2018-02-09 12:25:25 status config-files libmatchbox1:amd64 1.9-osso8-4
2018-02-09 12:25:25 status config-files libmatchbox1:amd64 1.9-osso8-4
2018-02-09 12:25:25 status not-installed libmatchbox1:amd64 <none>
2018-02-09 12:25:25 status installed matchbox-common:all 0.9.1-6
2018-02-09 12:25:25 remove matchbox-common:all 0.9.1-6 <none>
2018-02-09 12:25:25 status half-configured matchbox-common:all 0.9.1-6
2018-02-09 12:25:25 status half-installed matchbox-common:all 0.9.1-6
2018-02-09 12:25:25 status config-files matchbox-common:all 0.9.1-6
2018-02-09 12:25:25 status config-files matchbox-common:all 0.9.1-6
2018-02-09 12:25:25 status installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 12:25:25 remove matchbox-panel-manager:amd64 0.1-7 <none>
2018-02-09 12:25:25 status half-configured matchbox-panel-manager:amd64 0.1-7
2018-02-09 12:25:25 status half-installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 12:25:25 status half-installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 12:25:25 status config-files matchbox-panel-manager:amd64 0.1-7
2018-02-09 12:25:25 status config-files matchbox-panel-manager:amd64 0.1-7
2018-02-09 12:25:25 status config-files matchbox-panel-manager:amd64 0.1-7
2018-02-09 12:25:25 status not-installed matchbox-panel-manager:amd64 <none>
2018-02-09 14:18:22 install libmatchbox1:amd64 <none> 1.9-osso8-4
2018-02-09 14:18:22 status half-installed libmatchbox1:amd64 1.9-osso8-4
2018-02-09 14:18:22 status unpacked libmatchbox1:amd64 1.9-osso8-4
2018-02-09 14:18:22 status unpacked libmatchbox1:amd64 1.9-osso8-4
2018-02-09 14:18:22 install matchbox-common:all 0.9.1-6 0.9.1-6
2018-02-09 14:18:22 status half-installed matchbox-common:all 0.9.1-6
2018-02-09 14:18:22 status unpacked matchbox-common:all 0.9.1-6
2018-02-09 14:18:22 status unpacked matchbox-common:all 0.9.1-6
2018-02-09 14:18:22 install matchbox-window-manager:amd64 <none> 1.2-osso21-2
2018-02-09 14:18:22 status half-installed matchbox-window-manager:amd64 1.2-osso21-2
2018-02-09 14:18:22 status unpacked matchbox-window-manager:amd64 1.2-osso21-2
2018-02-09 14:18:22 status unpacked matchbox-window-manager:amd64 1.2-osso21-2
2018-02-09 14:18:22 install matchbox-desktop:amd64 <none> 2.0-5
2018-02-09 14:18:22 status half-installed matchbox-desktop:amd64 2.0-5
2018-02-09 14:18:23 status unpacked matchbox-desktop:amd64 2.0-5
2018-02-09 14:18:23 status unpacked matchbox-desktop:amd64 2.0-5
2018-02-09 14:18:23 install matchbox-panel:amd64 <none> 0.9.3-9
2018-02-09 14:18:23 status half-installed matchbox-panel:amd64 0.9.3-9
2018-02-09 14:18:23 status half-installed matchbox-panel:amd64 0.9.3-9
2018-02-09 14:18:23 status unpacked matchbox-panel:amd64 0.9.3-9
2018-02-09 14:18:23 status unpacked matchbox-panel:amd64 0.9.3-9
2018-02-09 14:18:23 install matchbox-panel-manager:amd64 <none> 0.1-7
2018-02-09 14:18:23 status half-installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 14:18:23 status half-installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 14:18:23 status unpacked matchbox-panel-manager:amd64 0.1-7
2018-02-09 14:18:23 status unpacked matchbox-panel-manager:amd64 0.1-7
2018-02-09 14:18:23 install matchbox-keyboard:amd64 <none> 0.1+svn20080916-11
2018-02-09 14:18:23 status half-installed matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 14:18:23 status half-installed matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 14:18:23 status unpacked matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 14:18:23 status unpacked matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 14:18:23 install matchbox:all <none> 1:6
2018-02-09 14:18:23 status half-installed matchbox:all 1:6
2018-02-09 14:18:23 status unpacked matchbox:all 1:6
2018-02-09 14:18:23 status unpacked matchbox:all 1:6
2018-02-09 14:18:23 install matchbox-keyboard-im:amd64 <none> 0.1+svn20080916-11
2018-02-09 14:18:23 status half-installed matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 14:18:23 status unpacked matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 14:18:23 status unpacked matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 14:18:24 configure matchbox-common:all 0.9.1-6 <none>
2018-02-09 14:18:24 status unpacked matchbox-common:all 0.9.1-6
2018-02-09 14:18:24 status half-configured matchbox-common:all 0.9.1-6
2018-02-09 14:18:24 status installed matchbox-common:all 0.9.1-6
2018-02-09 14:18:24 configure matchbox-panel-manager:amd64 0.1-7 <none>
2018-02-09 14:18:24 status unpacked matchbox-panel-manager:amd64 0.1-7
2018-02-09 14:18:24 status half-configured matchbox-panel-manager:amd64 0.1-7
2018-02-09 14:18:24 status installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 14:18:24 configure matchbox-keyboard-im:amd64 0.1+svn20080916-11 <none>
2018-02-09 14:18:24 status unpacked matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 14:18:24 status half-configured matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 14:18:24 status installed matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 14:18:24 configure matchbox-desktop:amd64 2.0-5 <none>
2018-02-09 14:18:24 status unpacked matchbox-desktop:amd64 2.0-5
2018-02-09 14:18:24 status half-configured matchbox-desktop:amd64 2.0-5
2018-02-09 14:18:24 status installed matchbox-desktop:amd64 2.0-5
2018-02-09 14:18:24 configure matchbox-keyboard:amd64 0.1+svn20080916-11 <none>
2018-02-09 14:18:24 status unpacked matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 14:18:24 status half-configured matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 14:18:24 status installed matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 14:18:24 configure libmatchbox1:amd64 1.9-osso8-4 <none>
2018-02-09 14:18:24 status unpacked libmatchbox1:amd64 1.9-osso8-4
2018-02-09 14:18:24 status half-configured libmatchbox1:amd64 1.9-osso8-4
2018-02-09 14:18:24 status installed libmatchbox1:amd64 1.9-osso8-4
2018-02-09 14:18:24 configure matchbox-panel:amd64 0.9.3-9 <none>
2018-02-09 14:18:24 status unpacked matchbox-panel:amd64 0.9.3-9
2018-02-09 14:18:24 status half-configured matchbox-panel:amd64 0.9.3-9
2018-02-09 14:18:24 status installed matchbox-panel:amd64 0.9.3-9
2018-02-09 14:18:24 configure matchbox-window-manager:amd64 1.2-osso21-2 <none>
2018-02-09 14:18:24 status unpacked matchbox-window-manager:amd64 1.2-osso21-2
2018-02-09 14:18:24 status unpacked matchbox-window-manager:amd64 1.2-osso21-2
2018-02-09 14:18:24 status half-configured matchbox-window-manager:amd64 1.2-osso21-2
2018-02-09 14:18:24 status installed matchbox-window-manager:amd64 1.2-osso21-2
2018-02-09 14:18:24 configure matchbox:all 1:6 <none>
2018-02-09 14:18:24 status unpacked matchbox:all 1:6
2018-02-09 14:18:24 status half-configured matchbox:all 1:6
2018-02-09 14:18:24 status installed matchbox:all 1:6
2018-02-09 15:35:55 status installed matchbox:all 1:6
2018-02-09 15:35:56 remove matchbox:all 1:6 <none>
2018-02-09 15:35:56 status half-configured matchbox:all 1:6
2018-02-09 15:35:56 status half-installed matchbox:all 1:6
2018-02-09 15:35:56 status config-files matchbox:all 1:6
2018-02-09 15:35:56 status config-files matchbox:all 1:6
2018-02-09 15:35:56 status config-files matchbox:all 1:6
2018-02-09 15:35:56 status not-installed matchbox:all <none>
2018-02-09 15:36:32 status installed matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 remove matchbox-keyboard:amd64 0.1+svn20080916-11 <none>
2018-02-09 15:36:32 status half-configured matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status half-installed matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status half-installed matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status config-files matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status config-files matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status config-files matchbox-keyboard:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status not-installed matchbox-keyboard:amd64 <none>
2018-02-09 15:36:32 status installed matchbox-panel:amd64 0.9.3-9
2018-02-09 15:36:32 remove matchbox-panel:amd64 0.9.3-9 <none>
2018-02-09 15:36:32 status half-configured matchbox-panel:amd64 0.9.3-9
2018-02-09 15:36:32 status half-installed matchbox-panel:amd64 0.9.3-9
2018-02-09 15:36:32 status half-installed matchbox-panel:amd64 0.9.3-9
2018-02-09 15:36:32 status config-files matchbox-panel:amd64 0.9.3-9
2018-02-09 15:36:32 status config-files matchbox-panel:amd64 0.9.3-9
2018-02-09 15:36:32 status config-files matchbox-panel:amd64 0.9.3-9
2018-02-09 15:36:32 status not-installed matchbox-panel:amd64 <none>
2018-02-09 15:36:32 status installed matchbox-desktop:amd64 2.0-5
2018-02-09 15:36:32 remove matchbox-desktop:amd64 2.0-5 <none>
2018-02-09 15:36:32 status half-configured matchbox-desktop:amd64 2.0-5
2018-02-09 15:36:32 status half-installed matchbox-desktop:amd64 2.0-5
2018-02-09 15:36:32 status config-files matchbox-desktop:amd64 2.0-5
2018-02-09 15:36:32 status config-files matchbox-desktop:amd64 2.0-5
2018-02-09 15:36:32 status config-files matchbox-desktop:amd64 2.0-5
2018-02-09 15:36:32 status not-installed matchbox-desktop:amd64 <none>
2018-02-09 15:36:32 status installed matchbox-common:all 0.9.1-6
2018-02-09 15:36:32 remove matchbox-common:all 0.9.1-6 <none>
2018-02-09 15:36:32 status half-configured matchbox-common:all 0.9.1-6
2018-02-09 15:36:32 status half-installed matchbox-common:all 0.9.1-6
2018-02-09 15:36:32 status config-files matchbox-common:all 0.9.1-6
2018-02-09 15:36:32 status config-files matchbox-common:all 0.9.1-6
2018-02-09 15:36:32 status installed matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 remove matchbox-keyboard-im:amd64 0.1+svn20080916-11 <none>
2018-02-09 15:36:32 status half-configured matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status half-installed matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status config-files matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status config-files matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status config-files matchbox-keyboard-im:amd64 0.1+svn20080916-11
2018-02-09 15:36:32 status not-installed matchbox-keyboard-im:amd64 <none>
2018-02-09 15:36:32 status installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 15:36:32 remove matchbox-panel-manager:amd64 0.1-7 <none>
2018-02-09 15:36:32 status half-configured matchbox-panel-manager:amd64 0.1-7
2018-02-09 15:36:32 status half-installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 15:36:32 status half-installed matchbox-panel-manager:amd64 0.1-7
2018-02-09 15:36:32 status config-files matchbox-panel-manager:amd64 0.1-7
2018-02-09 15:36:32 status config-files matchbox-panel-manager:amd64 0.1-7
2018-02-09 15:36:32 status config-files matchbox-panel-manager:amd64 0.1-7
2018-02-09 15:36:32 status not-installed matchbox-panel-manager:amd64 <none>
```

This is just an apt log and not sure but things like "status half-configured" "status half-installed" may just be logs of the install process while waiting for other dependencies to install.
Bottom line is if ...
```
apt policy matchbox-panel
```
shows "(none)" then matchbox-panel is not installed and "App Launcher" should not be showing in your xfce menu.

The replies have been a bit long winded to give you some understanding of the process
rather than just tell you to run a couple of commands.

---

### Post by arc- on 2018-02-09
Thank you for helping and explaining, I have learned more about the command line.

---

