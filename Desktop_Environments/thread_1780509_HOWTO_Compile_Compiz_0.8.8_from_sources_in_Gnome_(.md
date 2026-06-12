---
title: "HOWTO Compile Compiz 0.8.8 from sources in Gnome (Lucid)"
date: 2011-06-12
forum: Desktop Environments
---

### Post by dentaku65 on 2011-06-12
Due to the fact that there is not Official or PPA available for the new stable Compiz 0.8.8 announced on 30th March 2011 [http://wiki.compiz.org/](http://wiki.compiz.org/), here is a guide to compile it from the sources.

This guide works for Gnome env only; I wasn't able to compile the KDE part 
This procedure has been tested on Ubuntu Lucid and Maverick.

Create a backup of your active compiz settings:
```
cp -a $HOME/.config/compiz $HOME/.config/compiz.bak
```

Install the dependencies (Lucid):
```
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-dev python-pyrex libprotobuf-dev libprotobuf5 protobuf-compiler python-sexy wget libfuse-dev
```

Install the dependencies (Maverick):
```
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-dev python-pyrex libprotobuf-dev libprotobuf6 protobuf-compiler wget libfuse-dev
```

Not all components of Compiz has been released on 0.8.8; here the list of the releases (and the order of compile/install):
[LIST=1]
[*]compiz 0.8.8
[*]bcop 0.8.8
[*]libcompizconfig 0.8.8
[*]compizconfig-python 0.8.4
[*]ccsm 0.8.4
[*]compiz-plugins-main 0.8.8
[*]compiz-plugins-extra 0.8.8
[*]compiz-plugins-unsupported 0.8.8
[*]compizconfig-backend-gconf 0.8.8
[*]emerald 0.8.8
[/LIST]

Create working folder:
```
mkdir $HOME/sourcecompiz
```

compiz 0.8.8
```
cd $HOME/sourcecompiz
wget http://releases.compiz.org/0.8.8/compiz-0.8.8.tar.gz
tar xvzf compiz-0.8.8.tar.gz
cd compiz-0.8.8
./configure --prefix=/usr --disable-kde
make
sudo make install
```

bcop 0.8.8
```
cd $HOME/sourcecompiz
wget http://releases.compiz.org/0.8.8/compiz-bcop-0.8.8.tar.gz
tar xvzf compiz-bcop-0.8.8.tar.gz
cd compiz-bcop-0.8.8
./configure --prefix=/usr
make
sudo make install
```

libcompizconfig 0.8.8
```
cd $HOME/sourcecompiz
wget http://releases.compiz.org/0.8.8/libcompizconfig-0.8.8.tar.gz
tar xvzf libcompizconfig-0.8.8.tar.gz
cd libcompizconfig-0.8.8
./configure --prefix=/usr
make
sudo make install
```

compizconfig-python 0.8.4
```
cd $HOME/sourcecompiz
wget http://releases.compiz.org/0.8.4/compizconfig-python-0.8.4.tar.gz
tar xvzf compizconfig-python-0.8.4.tar.gz
cd compizconfig-python-0.8.4
./configure --prefix=/usr
make
sudo make install
```

ccsm 0.8.4
```
cd $HOME/sourcecompiz
wget http://releases.compiz.org/components/ccsm/ccsm-0.8.4.tar.gz
tar xvzf ccsm-0.8.4.tar.gz
cd ccsm-0.8.4
sudo python setup.py install
```

compiz-plugins-main 0.8.8
```
cd $HOME/sourcecompiz
wget http://releases.compiz.org/0.8.8/compiz-plugins-main-0.8.8.tar.gz
tar xvzf compiz-plugins-main-0.8.8.tar.gz
cd compiz-plugins-main-0.8.8
./configure --prefix=/usr
make
sudo make install
```

compiz-plugins-extra 0.8.8
```
cd $HOME/sourcecompiz
wget http://releases.compiz.org/0.8.8/compiz-plugins-extra-0.8.8.tar.gz
tar xvzf compiz-plugins-extra-0.8.8.tar.gz
cd compiz-plugins-extra-0.8.8
./configure --prefix=/usr
make
sudo make install
```

compiz-plugins-unsupported 0.8.8
```
cd $HOME/sourcecompiz
wget http://releases.compiz.org/0.8.8/compiz-plugins-unsupported-0.8.8.tar.gz
tar xvzf compiz-plugins-unsupported-0.8.8.tar.gz
cd compiz-plugins-unsupported-0.8.8
./configure --prefix=/usr
make
sudo make install
```

compizconfig-backend-gconf 0.8.8
```
cd $HOME/sourcecompiz
wget http://releases.compiz.org/0.8.8/compizconfig-backend-gconf-0.8.8.tar.gz
tar xvzf compizconfig-backend-gconf-0.8.8.tar.gz
cd compizconfig-backend-gconf-0.8.8
./configure --prefix=/usr
make
sudo make install

```
emerald 0.8.8
```
cd $HOME/sourcecompiz
wget http://releases.compiz.org/0.8.8/emerald-0.8.8.tar.gz
tar xvzf emerald-0.8.8.tar.gz
cd emerald-0.8.8
./configure --prefix=/usr
make
sudo make install
```

Reboot your box

Check the compiz version; on a console type:
```
compiz --version
```

See the output:
```
compiz 0.8.8
```
Remove the working folder if you wish:
```
rm -r -f $HOME/sourcecompiz
```

Done!

* Added Maverick

---

### Post by BryanFRitt on 2011-06-29
In Ubuntu 11.04 64bit I tried to compile compiz 0.8.8 into /opt/compiz0.8.8 

replacing the `./configure` lines with this

```
./configure --prefix=/opt/compiz0.8.8/ PKG_CONFIG_PATH=/opt/compiz0.8.8/lib/pkgconfig:/opt/compiz0.8.8/lib64/pkgconfig:/opt/compiz0.8.8/share/pkgconfig::$PKG_CONFIG_PATH LD_LIBRARY_PATH=/opt/compiz0.8.8/lib:/opt/compiz0.8.8/lib64:/opt/compiz0.8.8/lib32:$LD_LIBRARY_PATH
```

and the `python setup.py install` lines with
```
sudo python setup.py install --prefix=/opt/compiz0.8.8
```

Every thing compiled but the 'compiz-plugins-extra-0.8.8' one.
However, nothing in '/opt/compiz0.8.8/' seams to work. :(

---

### Post by agrawalmohit1989 on 2011-06-29
still getting 0.8.6???

---

### Post by dentaku65 on 2011-07-02
> **BryanFRitt said:**
> 
...
However, nothing in '/opt/compiz0.8.8/' seams to work. :(

Just a question: is compiz in 11.04 under /opt?
If so, I think the prefix should be:
> --prefix=/opt
instead of:
> --prefix=/opt/compiz0.8.8

---

### Post by BryanFRitt on 2011-07-03
> Just a question: is compiz in 11.04 under /opt?
type `which compiz` in a terminal and you can see where compiz is starting from if you don't add a path for it.

AFAIK the '--prefix=' should be in empty directory, or one the distro sets for it. For 'manually' compiled sources it's usually '/opt/something' replacing the word something with whatever you'd like, like compiz0.8.8. 
p.s. The script I found for git compiz0.9.x does it this way, '--prefix=/opt/compiz++'.

I don't know what it does about "trailing '/'" like /opt/compiz0.8.8 vs /opt/compiz0.8.8/ 

> still getting 0.8.6??? 
Did you put in the full path to the version of compiz you're testing the version of?
Like `/opt/compiz0.8.8/bin/compiz --version`?

[maybe I should have described "not working" better last time] 
I deleted the directories, installed the ppa for 8.6 and everything in it, and tried to compile 0.8.8 again, basically same results:
Everything compiled/installed but 'compiz-plugins-extra-0.8.8',
`/opt/compiz0.8.8/bin/compiz --replace` the decorations go away, and none of the compiz effects work.
`/opt/compiz0.8.8/bin/emerald --replace` will cause the decorations to become emerald decorations when the ppa's compiz is running, but not when I'm trying out the `/opt/compiz0.8.8/bin/compiz` compiz.
-
Is there a script for installing compiz 0.8.x out there I can download?

---

### Post by BryanFRitt on 2011-07-04
I found a git* script, and tried it out.

It works, but has some issues:
[LIST]
[*]It replaces the repository version (at least by default) so you won't have access to that version.
[*]ALL SETTINGS FROM ALL INSTALLS OF COMPIZ GETS DELETED. Back up your ALL of your compiz profiles. One way to backup the ccsm profile is to go to CCSM -> Preferences(bottom left corner) -> Profile & Backend tab -> Profile section -> Export -> ... and be sure to add .profile to the end of the file name.
[*]*(Update: uninstall of '[FONT="Courier New"]libnotify-dev[/FONT]' fixed this)* A few fail to compile, like '[FONT="Courier New"]compiz-plugins-extra[/FONT]', and the '[FONT="Courier New"]extra-animations[/FONT]' ones. 
[*]The '[FONT="Courier New"]compizconfig-backend[/FONT]' ones get a '[FONT="Courier New"]fatal: The remote end hung up unexpectedly[/FONT]'... '[FONT="Courier New"]No such file or directory[/FONT]', and get skipped. (I didn't want to use the '[FONT="Courier New"]compizconfig-backend[/FONT]' ones anyway, so I'm okay with that.)
[*]This is the full git version, so it install could install some plugins that are buggy. Hint: typically the ones with '?' tend to be the more buggy ones? (and might be too many options/plugins for some people)
[*](Update:This can be fixed by CCSM->General->General Options->General->'unredirect Fullscreen Windows) Full screen videos flicker back and forth between images (compiz 0.9.2.1 doesn't have this problem, update: see update at beginning of this line)
[*]The directions on the page are missing a `[FONT="Courier New"]cd stable[/FONT]`(0.8.x) or a `[FONT="Courier New"]cd dev[/FONT]`(0.9.x)**, I used `[FONT="Courier New"]cd stable[/FONT]`.
[*]Edit the [FONT="Courier New"]git-compiz-def[/FONT] file, in the lines that start with '[http://sites.google.com/site/gitcompiz08/Home/](http://sites.google.com/site/gitcompiz08/Home/)' (around lines 124-126), remove everything after the first tar.gz. (?attredirects=0%writeto%...) If you've already run the script, you'll have to delete the corresponding files/folders (they'll be empty files/folders in the script directory), and rerun the script.
[*]Be sure to logout-login after finishing, to start the new compiz. 
[/LIST]

Maybe that's just my experience, if you're willing to take a risk and try this git version, here it is.
[http://forum.compiz.org/viewtopic.php?f=85&t=7744](http://forum.compiz.org/viewtopic.php?f=85&t=7744)

p.s.
If all the icons in ccsm are the same, or you can't edit shortcuts, try this:
in the source ccsm directory,
[FONT="Courier New"]sudo python setup.py clean[/FONT]
[FONT="Courier New"]sudo python setup.py install[/FONT]
followed by a 
[FONT="Courier New"]./git-compiz --rebuild=ccsm[/FONT]
in the 'stable' directory.

*git versions tend to be less stable than numbered released versions?

**When I was trying 0.9.x I was using a different script, I don't know how this does with 0.9.x.

---

### Post by dentaku65 on 2011-07-04
> **BryanFRitt said:**
> type `which compiz` in a terminal and you can see where compiz is starting from if you don't add a path for it.

AFAIK the '--prefix=' should be in empty directory, or one the distro sets for it. For 'manually' compiled sources it's usually '/opt/something' replacing the word something with whatever you'd like, like compiz0.8.8. 
p.s. The script I found for git compiz0.9.x does it this way, '--prefix=/opt/compiz++'.



...well compiz on Lucid and Maverick is under /usr 
If you install compiz from the repo or ppa is landing there... do not exist a "rule" for manually compiled source to install the compiled one under /opt and, as far as I know, there is not any reason.
compiz 0.9 is another story, is a dev release and not stable release as 0.8.8; out of scope for this guide.

> 
I don't know what it does about "trailing '/'" like /opt/compiz0.8.8 vs /opt/compiz0.8.8/ 

No difference

> 
Did you put in the full path to the version of compiz you're testing the version of?
Like `/opt/compiz0.8.8/bin/compiz --version`?


If you istall compiz in the correct path (as indicated /usr), compiz app it's already in the path; so compiz --version works as exposed

> 
[maybe I should have described "not working" better last time] 
I deleted the directories, installed the ppa for 8.6 and everything in it, and tried to compile 0.8.8 again, basically same results:
Everything compiled/installed but 'compiz-plugins-extra-0.8.8',
`/opt/compiz0.8.8/bin/compiz --replace` the decorations go away, and none of the compiz effects work.
`/opt/compiz0.8.8/bin/emerald --replace` will cause the decorations to become emerald decorations when the ppa's compiz is running, but not when I'm trying out the `/opt/compiz0.8.8/bin/compiz` compiz.


As you can see the compiz 0.8.6 installed from ppa resides under /usr 
If you compile as described on #1 the 0.8.8 will overwrite the current installation of compiz (this was my situation too)

For Emerald I'm able to use it only via Flat File Configuration Backend and not via Gconf Backend

bye

---

### Post by BryanFRitt on 2011-07-04
> **dentaku65 said:**
> ...well compiz on Lucid and Maverick is under /usr

I think it's under /usr in Natty too. That's why I _did not_ want to put it there. I wanted to be able to switch back to the Ubuntu version, if the compile didn't work good enough for me, etc... If I put it where Ubuntu put's there files, it'll have to take the place of the Ubuntu files, and won't have access to the Ubuntu version anymore.

Also, if I try to switch from one version to another(uninstall one(if possible), then install the other one), having the locally compiled version put it in the same directory as the Ubuntu version, the files from the locally compiled version might affect the Ubuntu version, and vice versa, or at least I'd think it might.

Having the locally compiled version in a separate folder allows easy deletion of the compiled version, just delete the folder. I suppose I could do a 'checkinstall', but that's more work.

For some reason the script didn't work so well when I tried to give it a path, it at least seamed to half way do it there, some of the plugins that compiled didn't show up under ccsm, although I guess it's possible I messed up somewhere on doing that.

So far, the compiled git version seams to working out for me, even with it being in /usr, taking the place of where my Ubuntu compiled version was.
Note: I uninstalled everything Compiz, before installing the dependencies, running the script, etc...

misc:
ccsm stands for Compiz Config Settings Manager

---

### Post by dentaku65 on 2011-07-05
> **BryanFRitt said:**
> I think it's under /usr in Natty too. That's why I _did not_ want to put it there. I wanted to be able to switch back to the Ubuntu version, if the compile didn't work good enough for me, etc... If I put it where Ubuntu put's there files, it'll have to take the place of the Ubuntu files, and won't have access to the Ubuntu version anymore.

:confused:

You are able to switch back in any time to the original version, just reinstall compiz via apt or aptitude, something like;
```
sudo apt-get --reinstall install compiz compiz-fusion-plugins-main compizconfig-backend-gconf compizconfig-settings-manager python-compizconfig compiz-dev compiz-plugins compiz-core
```

---

### Post by BryanFRitt on 2011-07-06
> **dentaku65 said:**
> You are able to switch back in any time to the original version, just reinstall compiz via apt or aptitude, something like;
```
sudo apt-get --reinstall install compiz compiz-fusion-plugins-main compizconfig-backend-gconf compizconfig-settings-manager python-compizconfig compiz-dev compiz-plugins compiz-core
```

That's a lot of work to go back and forth between the two versions. If the locally compiled version were it's own directory, it'd be as easy as switching which one was running. `/usr/bin/compiz --replace &`, `/opt/compiz0.8.8/bin/compiz --replace &`. (and probably there's less possibilities of the two versions messing with each other, except for settings?)

To autostart it under KDE, Kmenu->Settings->System Settings->Workspace Appearance and Behavior->Window Manager->Use a different _w_indow manager:->  Compiz for the Ubuntu one, or compiz-kde-launcher for the locally compiled one.(look it up on how to use it)

```
#!/bin/bash
# located in /usr/bin/compiz-kde-launcher OR ~/bin/compiz-kde-launcher ?
# remember to `chmod +x` this file
/opt/compiz0.8.8/bin/compiz --replace &
```

For a GNOME autostart make/edit this file
/usr/share/applications/compiz.desktop
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Compiz
Exec=/opt/compiz0.8.8/bin/compiz ccp  #Make sure ccp is included so that Compiz loads your previous settings.
NoDisplay=true
# name of loadable control center module
X-GNOME-WMSettingsModule=compiz
# autostart phase
##-> the folloing line cause gnome-session warning and slow startup, so try not to enable this
# X-GNOME-Autostart-Phase=WindowManager 
X-GNOME-Provides=windowmanager
# name we put on the WM spec check window
X-GNOME-WMName=Compiz
# back compat only
X-GnomeWMSettingsLibrary=compiz
```

Source:
[https://wiki.archlinux.org/index.php/Compiz](https://wiki.archlinux.org/index.php/Compiz)

---

### Post by dentaku65 on 2011-07-06
> **BryanFRitt said:**
> That's a lot of work to go back and forth between the two versions. If the locally compiled version were it's own directory, it'd be as easy as switching which one was running. `/usr/bin/compiz --replace &`, `/opt/compiz0.8.8/bin/compiz --replace &`. (and probably there's less possibilities of the two versions messing with each other, except for settings?)


Well... it depends, if you do an upgrade, normally, you'll stay with the upgraded version; you don't need to continuously back and forward from a version to another... but this is my opinion.

You'll need to go back just in case of fail or simply dislike the upgrade

Back to post #1, this is a guide for "upgrade" compiz from 0.8.6 (officially available from repositories) with  0.8.8 released as stable and not available from repositories (at least yet); the configuration of both versions are 100% compatible, no issues from there.

If you wish to install in to another path with different rules, you can do it but I have no idea how to solve the issues that you have indicated and I do not understand your approach or doubt of replace/upgrade as posted here.

---

### Post by BryanFRitt on 2011-07-10
My apologies for inadvertently hijacking the thread.
---
Filesystem Hierarchy Standard for /opt/ quotes:
---
[http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES](http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES)

> ...
Programs to be invoked by users must be located in the directory /opt/<package>/bin or under the /opt/<provider> hierarchy.
...
Distributions may install software in /opt, but must not modify or delete software installed by the local system administrator without the assent of the local system administrator.
...
The minor restrictions on distributions using /opt are necessary because conflicts are possible between distribution-installed and locally-installed software
...
---
[http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/3/html/Reference_Guide/s1-filesystem-fhs.html](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/3/html/Reference_Guide/s1-filesystem-fhs.html)

> 3.2.1.7. The /opt/ Directory

The /opt/ directory provides storage for large, static application software packages.

A package placing files in the /opt/ directory creates a directory bearing the same name as the package. This directory, in turn, holds files that otherwise would be scattered throughout the file system, giving the system administrator an easy way to determine the role of each file within a particular package.

For example, if sample is the name of a particular software package located within the /opt/ directory, then all of its files are placed in directories inside the /opt/sample/ directory, such as /opt/sample/bin/ for binaries and /opt/sample/man/ for manual pages.

Large packages that encompass many different sub-packages, each of which accomplish a particular task, are also located in the /opt/ directory, giving that large package a way to organize itself. In this way, our sample package may have different tools that each go in their own sub-directories, such as /opt/sample/tool1/ and /opt/sample/tool2/, each of which can have their own bin/, man/, and other similar directories.
---
See also:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html#opt](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html#opt)
...

---

### Post by Allmighty_Lulala on 2011-08-02
Hi,

I used your guide to install new compiz0.8.8 but it ruined my old compiz and the new one is not working properly (missing window borders and decorations, cannot move windows etc etc.)

Is there any way how to get it working? Or better, get rid off all compiz and install it again  -"the microsoft way"?

(using 10.10, graphic card Intel HD - core i3)

---

### Post by dentaku65 on 2011-08-04
> **Allmighty_Lulala said:**
> Hi,
Is there any way how to get it working? Or better, get rid off all compiz and install it again  -"the microsoft way"?

(using 10.10, graphic card Intel HD - core i3)

Hi,
maybe you must use Flat-File-configuration as backend

1 open ccsm and choose Preferences
2 Export the default profile and Import As.. (you name it)
3 Change the Backend from Gconf to Flat File

Or, if you want to remove it, use uninstall command 
```
sudo make uninstall
```
on every components on source directory; then reinstall compiz from Ubuntu repository.

by

---

### Post by BryanFRitt on 2011-08-08
> **Allmighty_Lulala said:**
> Hi,

I used your guide to install new compiz0.8.8 but it ruined my old compiz and the new one is not working properly (missing window borders and decorations, cannot move windows etc etc.)

Is there any way how to get it working? Or better, get rid off all compiz and install it again  -"the microsoft way"?

(using 10.10, graphic card Intel HD - core i3)

[edit]Make sure the *CCSM->Effects->Window Decoration* plugin is enabled first then [/edit]
Try messing with 
*CCSM->Effects->Window Decoration->General->Command*
Depending on your setup, try something like
[FONT="Courier New"]compiz-decorator[/FONT], or [FONT="Courier New"]kwin[/FONT], or [FONT="Courier New"]gtk-window-decorator[/FONT], or [FONT="Courier New"]emerald[/FONT], or [FONT="Courier New"]kde4-window-decorator[/FONT], or something like that with a path, or just blank, etc... with or without a [FONT="Courier New"]--replace[/FONT]
You might have to start compiz again, 
`[FONT="Courier New"]compiz --replace &[/FONT]`
or equivalent in a 'run dialog' for your setup.

You probably still can move your windows around try
[edit]Make sure the CCSM->Window Management->Move Window plugin is enabled first then[/edit]
*CCSM->Window Management->Move Window->General->Initiate Window Move*
Defaults to *<Alt>Button1*, and *<Alt>F7*
To move a window with the mouse, press the mouse binding with the mouse pointer over the window you want to move, or to move the window with the keyboard make the window the 'active' window and press the '*Initiate Window Move*' keyboard binding, then use the keyboard arrow keys.

---

### Post by Drone4four on 2011-12-26
If you use make, make install, you can't uninstall compiz 0.8.8.    Wouldn't it be better practices to create deb packages and install them that way? Would anyone know where we could find deb packages for 0.8.8?

---

### Post by BryanFRitt on 2012-01-01
> **Drone4four said:**
> If you use make, make install, you can't uninstall compiz 0.8.8.

> **Drone4four said:**
> Wouldn't it be better practices to create deb packages and install them that way? Would anyone know where we could find deb packages for 0.8.8?

You can try `[[FONT="Courier New"]checkinstall[/FONT]]("https://help.ubuntu.com/community/CheckInstall")`, but read the `[[FONT="Courier New"]checkinstall[/FONT]]("https://help.ubuntu.com/community/CheckInstall")` warning first (links added):

> [CheckInstall]("https://help.ubuntu.com/community/CheckInstall") is not designed to produce packages suitable for distribution. Do not use it to produce packages intended for the [Ubuntu archive]("http://archive.ubuntu.com/") or [PPAs]("https://launchpad.net/ubuntu/+ppas"). Instead, follow the [Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide/Complete").

How to start using `[[FONT="Courier New"]checkinstall[/FONT]]("https://help.ubuntu.com/community/CheckInstall")` instead of `[FONT="Courier New"]make install[/FONT]`
[FONT="Courier New"]
first install `[[FONT="Courier New"]checkinstall[/FONT]]("https://help.ubuntu.com/community/CheckInstall")`
sudo apt-get install checkinstall[/FONT]
Then go to the source code directory and run
[FONT="Courier New"]auto-apt run ./configure
make
sudo checkinstall[/FONT]

---

### Post by skrite on 2012-08-09
hey, wanted to stop by here and post a quick thank you for this procedure. I installed with a mini iso and used your outline to install compiz. All went smooth. Great work

---

### Post by Gh0zt36 on 2013-05-10
too bad half the repositories dont work anymore and most of my tools are too outdated to compile this.

---

