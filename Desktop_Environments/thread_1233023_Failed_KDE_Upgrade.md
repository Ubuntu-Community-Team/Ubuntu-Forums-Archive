---
title: "Failed KDE Upgrade"
date: 2009-08-06
forum: Desktop Environments
---

### Post by john@ukgillies.com on 2009-08-06
Hello everyone,

I fear I have made a pig's ear of my KDE environment.

I'm running a 64 bit Kubuntu with the KDE 4.3 desktop.

I upgraded the installation on Monday - lots of upgrades for KDE!

Now I cannot get to my desktop.

The PC boots up to the Welcome Screen and I am presented with Username and Password as usual.

The list under Session Type only has default and Failsafe. 

Failsafe gets me to a small command prompt window at the top left of the screen. This seems to work. Exit from here reboots the PC.

default then logging in with my Username/Password gets a black screen with a mouse pointer and nothing else.
At this black screen I can get to a command prompt tty2-6 using the CtrlAlt F2-6.

Can anyone help on how to..... 

Either Rewind the installation that has failed.
Get me Back to a KDE Desktop.

..............before I panic??

Many thanks,

John

---

### Post by barnex on 2009-08-06
In your failsafe terminal, you could install gnome or xfce, so you have at least some graphical shell to work from. From there, I would recommend disabling the experimental repositories so you can get kde 4.2 back instead of 4.3. by removing and reinstalling kde (kubuntu-deskop package, i think).

---

### Post by McNils on 2009-08-06
Use the virtual consoles to access yor account. Try to clear kde configuration.

Try to clear the plasma configuration.
Move thease file to an other location. And try to login again.
~/.kde/share/config/plasma-desktop-appletsrc
~/.kde/share/config/plasma-desktoprc
~/.kde/share/config/plasmoidviewer-appletsrc
~/.kde/share/config/plasmarc
~/.kde/share/config/plasma-appletsrc

If this fails rename your ~/.kde folder and login again

---

### Post by McNils on 2009-08-06
Forgett my previous post. It was tottally off. :confused:

Use recovery-mode or console login tho find out what you have installed.

List all kde packages installed.
```
dpkg -l | grep kde
``` 
Install kubuntu-desktop
```
sudo apt-get install kubuntu-desktop
```

---

### Post by john@ukgillies.com on 2009-08-06
Thanks for the help.

I tried to do as you said - but still issues.

The output for the install kubuntu-desktop is shown below

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: dragonplayer but it is not going to be installed
                   Depends: kdebase-workspace-bin but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kdepim-wizards but it is not going to be installed
                   Recommends: kdeplasma-addons but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: knotes but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: konqueror-plugin-searchbar but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed


Any further thoughts?

Thanks

John

---

### Post by McNils on 2009-08-06
I usu aptitude to resolve this kind of problem. Log in a console/recovery mode and start **sudo aptitude**. Press u,U,g and start to resolve your dependency problems. It says something about pressing one key to resolve.

---

### Post by Zorael on 2009-08-06
> **McNils said:**
> I usu aptitude to resolve this kind of problem. Log in a console/recovery mode and start **sudo aptitude**. Press u,U,g and start to resolve your dependency problems. It says something about pressing one key to resolve.

'**sudo aptitude install -f**' should start the same (dependency resolving) procedure without entering the interface, if that's of interest.

'**sudo aptitude full-upgrade**' starts a full upgrade, in the sense that it will try to upgrade EVERY upgrade available, and if not possible, it'll stop and ask you what you want to do. It's an aggressive approach, equavilent to apt-get dist-upgrade. If nothing else it's a good way to find out what's stopping things, instead of just having apt-get tell you stuff "isn't going to be installed". full-upgrade can remove and downgrade packages to make ends meet.

'**sudo aptitude safe-upgrade**' is basically equavilent to apt-get upgrade. It won't remove/downgrade packages; if stuff can't be easily and safely upgraded, they'll be held back until they can.


While on the topic of aptitude-fu (and general terminal package management knowhow), if there is an update to the imaginary package ***packagename*** (which you can divine by entering '**apt-cache policy *packagename***') then installing it (when it's already installed) with '**sudo aptitude install *packagename***' *will **upgrade** it*. If it in turn depends on a newer version of another package to which there's also an update, it will suggest you upgrade it at the same time. So if you have upgrades to Firefox and KDE's plasma and you only want to upgrade Firefox right now, just do '**sudo aptitude install firefox**'. Then it might say you need to also upgrade some other libraries that the new Firefox depends on, which in turn depend on some other new versions, and you get a neat little upgrade bundle that still doesn't upgrade plasma. Unless, of course, something Firefox depended on also depends on that new plasma version. In that case the newer Firefox (that you want to upgrade to) and the current plasma (that you want to keep) are mutually exclusive.

If you want to install a specific version of a package available from repositories, you can pass the version number to aptitude like '**sudo aptitude install *packagename*=*version***'. Again, to list available versions of a package, do '**apt-cache policy *packagename***'. Noteworthy is that it will upgrade to the newer package at the next upgrading opportunity, so this is a temporary solution.
```
zorael@sunspire:~$ **apt-cache policy [COLOR="DeepSkyBlue"]smplayer[/COLOR]**
[COLOR="DeepSkyBlue"]smplayer[/COLOR]:
  Installed: **[COLOR="Red"]0.6.8-1~jaunty2[/COLOR]**
  Candidate: **[COLOR="Red"]0.6.8-1~jaunty2[/COLOR]**
  Version table:
 *** **[COLOR="Red"]0.6.8-1~jaunty2[/COLOR]** 0
        500 http://ppa.launchpad.net jaunty/main Packages
        100 /var/lib/dpkg/status
     **[COLOR="Lime"]0.6.7-1[/COLOR]** 0
        500 http://se.archive.ubuntu.com karmic/multiverse Packages

*<oh hey I want to downgrade to **[COLOR="Lime"]0.6.7-1[/COLOR]**>*

zorael@sunspire:~$ **sudo aptitude install [COLOR="DeepSkyBlue"]smplayer[/COLOR]**=**[COLOR="Lime"]0.6.7-1[/COLOR]**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages will be ***DOWNGRADED***:
  [COLOR="DeepSkyBlue"]smplayer[/COLOR]
The following NEW packages will be installed:
  smplayer-translations{a}
0 packages upgraded, 1 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 2691kB of archives. After unpacking 1188kB will be freed.
Do you want to continue? [Y/n/?] ofc lol
```

You can hold a package at its current version with '**sudo aptitude hold *packagename***', and *forbid* a version available as an upgrade to that package with '**sudo aptitude forbid-version *packagename***' (add **=*version*** if you have several upgrade candidates and you only want to forbid one of them - again, see **apt-cache policy *packagename***). It only works for aptitude itself though, so apt-get and other packaging tools will ignore this setting and upgrade nonetheless.

If it complains about a package being broken and that you'd need to reinstall it, there is a **reinstall** operation to aptitude. So '**sudo aptitude reinstall *packagename***'.

If a package stops working for whatever reason, you can attempt to *reconfigure* it (read: let it run its installation script again) by calling '**sudo dpkg-reconfigure *packagename***'. If the package was *never configured* (read: was never allowed to run its installation script; something interrupted it after it extracted its files), the command is '**sudo dpkg --configure *packagename***'. In that case, consider just reinstalling it in the way mentioned earlier.

If a package fails to install and complains about stuff like file duplicates (*"file **X** is also part of package **Y** so cannot continue"*), you can **force** **dpkg** to install it nevertheless, but depending on what the cause of the error was you could be doing some nasty damage, too. apt-get/aptitude/Synaptic/etc are *frontends* to dpkg; dpkg takes care of the actual extracting of packages' files and running their installation/removal scripts, while the frontends take care of downloading stuff and acting as the general interface to the user. So you would "just" be bypassing those (*at your peril*). The analogy would be that you take the worker's tools and do the job yourself. Now, packages downloaded via apt-get/aptitude/etc are saved in **/var/cache/apt/archives/** (some in the **partial/** subdirectory), so if you navigate there and find the .deb of a given package that was downloaded and failed to install, you can then force dpkg to install it. 
```
zorael@sunspire:/var/cache/apt/archives$ **dpkg --force-help**
dpkg forcing options - control behaviour when problems found:
  warn but continue:  --force-<thing>,<thing>,...
  stop with error:    --refuse-<thing>,<thing>,... | --no-force-<thing>,...
 Forcing things:
  all [!]                Set all force options
  downgrade [*]          Replace a package with a lower version
  configure-any          Configure any package which may help this one
  hold                   Process incidental packages even when on hold
  bad-path               PATH is missing important programs, problems likely
  not-root               Try to (de)install things even when not root
  overwrite              Overwrite a file from one package with another
  overwrite-diverted     Overwrite a diverted file with an undiverted version
  bad-verify             Install a package even if it fails authenticity check
  depends-version [!]    Turn dependency version problems into warnings
  depends [!]            Turn all dependency problems into warnings
  confnew [!]            Always use the new config files, don't prompt
  confold [!]            Always use the old config files, don't prompt
  confdef [!]            Use the default option for new config files if one
                         is available, don't prompt. If no default can be found,
                         you will be prompted unless one of the confold or
                         confnew options is also given
  confmiss [!]           Always install missing config files
  breaks [!]             Install even if it would break another package
  conflicts [!]          Allow installation of conflicting packages
  architecture [!]       Process even packages with wrong architecture
  overwrite-dir [!]      Overwrite one package's directory with another's file
  remove-reinstreq [!]   Remove packages which require installation
  remove-essential [!]   Remove an essential package

WARNING - use of options marked [!] can seriously damage your installation.
Forcing options marked [*] are enabled by default.

zorael@sunspire:/var/cache/apt/archives$ **sudo dpkg -i *--force-overwrite* packagefile_inthisdirectory_.deb**
```

---

### Post by john@ukgillies.com on 2009-08-22
:P
Many many thanks to all of you who helped here. Apologies for delay in sending this - I have been away. 

Your input has moved my understanding along a whole lot. And my KDE4.3 desktop is back in all its glory. I am not sure that I totally understand why yet, but I'm learning all the time.

What a great help you have been.

John.

---

