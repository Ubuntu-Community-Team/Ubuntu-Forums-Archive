---
title: "Extremely disappointed with KUNBUTU 8.04"
date: 2008-04-27
forum: Desktop Environments
---

### Post by oobuntoo on 2008-04-27
I've been using Kubuntu (KDE) exclusively, release after release, and noticed that things are getting worse. I had to look around for work-arounds for alot of things, and I'm just tired of doing that at this point. There are serveral things that have annoyed since Gutsy and is getting worse in Hardy. I'm just gonna list ONE here and see if anyone can find a solution for this:

In Hardy, one of the first things I have to change is the font size. The default size (10) is just too big, I changed it to 7. It's all good, except all programs that run as sudo will not respect this change; they still use font size of 10. In fact, this applies to not only fonts but themes and colors as well. There is no way to change settings for programs that run as sudo. I've tried sudo kcontrol, sudo systemsettings, and sudo any kcontrol module, then make changes to fonts, colors, or style but nothing works.

Programs that runs in sudo mode (adept, synaptic, etc,...) will use what ever the defaut settings are and there is no way to change them (easily).:confused:

---

### Post by unoodles on 2008-04-27
If you cannot stand KDE, try using regular ubuntu, or even xubuntu

---

### Post by oobuntoo on 2008-04-29
I've been using Ubuntu(Gnome)on my laptop. Gnome is a nice desktop, but I use a lot of Qt-based applications and I prefer to use them in their native environment. I've been thinking of trying other debian-based KDE distro, but haven't found one that has good cleartype-like font rendering, like Ubuntu, out of the box.

---

### Post by sstusick on 2008-04-29
The default font on Kubuntu? I think it's fine if set at 9pt, the default is 10, but 7 is way too small.

---

### Post by lewisskinner on 2008-04-29
> **oobuntoo said:**
> I've been using Ubuntu(Gnome)on my laptop. Gnome is a nice desktop, but I use a lot of Qt-based applications and I prefer to use them in their native environment. I've been thinking of trying other debian-based KDE distro, but haven't found one that has good cleartype-like font rendering, like Ubuntu, out of the box.

Have you thought about Linux Mint?  It's based on Ubuntu, but is supposed to work better out of the box.

---

### Post by oobuntoo on 2008-04-30
> **sstusick said:**
> The default font on Kubuntu? I think it's fine if set at 9pt, the default is 10, but 7 is way too small.

I have a 24-inch screen. It's huge. I'm not bragging. ;)
7pt looks good on it.

---

### Post by oobuntoo on 2008-04-30
> **lewisskinner said:**
> Have you thought about Linux Mint?  It's based on Ubuntu, but is supposed to work better out of the box.

I tried KDE Mint. It's has the same problems as Kubuntu. That wasn't surprising, considering it was based on Kubuntu. It's just has different default themes and apps. 

I'll probably give Debian Lenny a try.

---

### Post by Zorael on 2008-04-30
Root has its own KDE configuration, so you theoretically could theme root's windows one way and theme your own another. Obviously, this carries over to fonts, their size and antialiasing settings, too. So what you want to do is open kconfig or systemsettings *as* root, then set things up as you want them.
```
$ kdesu kcontrol
```

Anyway.
[list][*]Can't change desktop path, workaround is to change it via settings first and then edit ~/.config/user-dirs.dirs and remove the [$E] added to the end of some entries
[*]Compiz not liking the logout fade, workaround is to disable it by adding the following to ~/.kde/share/config/ksmserverrc
```
[Logout]
doFancyLogout=1
doFancyLogoutFadeTime=0
doFancyLogoutFadeBackTime=0
```
[*]Compiz giving me 16x16 desktops instead of 4x1, workaround is to make a script that launches it with the --ignore-desktop-hints argument, or use fusion-icon to do it for you
[*]Compiz messing up adept_notifier, workaround is to make the above mentioned script kill it just before starting compiz and restarting it a few seconds later
```
#!/bin/bash
################## uncomment one
# fusion-icon &
# compiz --replace --ignore-desktop-hints &
################################
killall adept_notifier
sleep 7
adept_notifier &
```
[*]kdmrc not importing distro default settings from /etc/default/kdm.d/20_kubuntu_default_settings after you change the background in the Login Manager settings. Workaround is not to. If you managed to anyway, edit /etc/kde3/kdm/backgroundrc, find the Wallpaper= line and restore it to 'Wallpaper=default_blue.jpg'
[*]PulseAudio not installed by default! Rarr! Workaround is to install it; [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup). Grab the OSS version of Skype to get preliminary Skype support, but beware, it sucks[/list]

I guess that's it.

---

### Post by oobuntoo on 2008-05-03
> **Zorael said:**
> Root has its own KDE configuration, so you theoretically could theme root's windows one way and theme your own another. Obviously, this carries over to fonts, their size and antialiasing settings, too. So what you want to do is open kconfig or systemsettings *as* root, then set things up as you want them.
```
$ kdesu kcontrol
```

Anyway.
[list][*]Can't change desktop path, workaround is to change it via settings first and then edit ~/.config/user-dirs.dirs and remove the [$E] added to the end of some entries
[*]Compiz not liking the logout fade, workaround is to disable it by adding the following to ~/.kde/share/config/ksmserverrc
```
[Logout]
doFancyLogout=1
doFancyLogoutFadeTime=0
doFancyLogoutFadeBackTime=0
```
[*]Compiz giving me 16x16 desktops instead of 4x1, workaround is to make a script that launches it with the --ignore-desktop-hints argument, or use fusion-icon to do it for you
[*]Compiz messing up adept_notifier, workaround is to make the above mentioned script kill it just before starting compiz and restarting it a few seconds later
```
#!/bin/bash
################## uncomment one
# fusion-icon &
# compiz --replace --ignore-desktop-hints &
################################
killall adept_notifier
sleep 7
adept_notifier &
```
[*]kdmrc not importing distro default settings from /etc/default/kdm.d/20_kubuntu_default_settings after you change the background in the Login Manager settings. Workaround is not to. If you managed to anyway, edit /etc/kde3/kdm/backgroundrc, find the Wallpaper= line and restore it to 'Wallpaper=default_blue.jpg'
[*]PulseAudio not installed by default! Rarr! Workaround is to install it; [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup). Grab the OSS version of Skype to get preliminary Skype support, but beware, it sucks[/list]

I guess that's it.

Thank, Zorael.

I'll give these suggestions a try, when I get a chance.

---

### Post by Igtenio on 2008-05-03
Also, if you're like me, where you prefer KDE over Gnome but hate Kubuntu itself, you could install KDE-Core through Synaptic or Apt-get. That'll install the basic KDE packages without any sort of Kubuntu branding or customization.

If you want a really sleek system, and can get away with it, you could also just install a Command-line System from the Alternate CD, and then execute;

```
sudo apt-get install xorg kde-core kdm
```

To get a system based on the fundamentals of Ubuntu, but without Gnome cluttering it. I usually include Synaptic, despite it being a GTK+ Application, and that can be achieved by just adding "synaptic" to the list of programs in the line. The upside about installing synaptic is that it also installs many of the libraries for Gnome applications, so if you ever need to install another one, you won't need to wait for many of them then. Obviously, if you don't have any Gnome applications to use, or you dislike Synaptic, this can be easily skipped.

I'm planning on trying to do it on my machine at some point, but I have a wireless adapter which would be a pain to setup in a no-frills command-line environment, so I've put it off for the moment.

---

### Post by Zorael on 2008-05-03
Addendum to the login manager not importing distro-specific settings.

> **Zorael said:**
> Opinion, but I would suggest you leave kdmrc alone and instead edit **/etc/default/kdm.d/20_kubuntu_default_settings**; upon start of the login manager, it'll import the settings defined there which override duplicate settings in that kdmrc file. Makes things more legilible.

DO NOTE that, for the import to work, the **Theme=** line under the **[X-*-Greeter]** heading in /etc/kde3/kdm/kdmrc *must* say:
```
Theme=@@@ToBeReplacedByDesktopBase@@@
```
And likewise, the **Wallpaper=** line in **/etc/kde3/kdm/backgroundrc** *must* say:
```
Wallpaper=default_blue.jpg
```

Explanation: **/etc/init.d/kdm** checks for these lines in the mentioned files (kdmrc and backgroundrc in /etc/kde3/kdm/), and if the Wallpaper and Theme settings differ, it doesn't import the kubuntu-specific settings under **/etc/default/kdm.d/**.

This means that if you at any point try to change wallpaper in the Login Manager section in system settings, it'll change the Wallpaper= line, which'll break the importing. If you at any point wish to change the wallpaper, make the appropriate changes to backgroundrc *as well as* the .xml file in the theme you're using, which are usually located in **/usr/share/apps/kdm/themes/**.
I didn't like the Kubuntu Hardy wallpaper, so I copied the one from Gutsy (which is, in my opinion, largely superior), and edited both **/etc/default/kdm.d/backgroundrc** as well as **/usr/share/apps/kdm/themes/kubuntu/kubuntu.xml**, adding references to **/usr/share/wallpapers/***<filename of wallpaper, in my case **kubuntu-wallpaper-gutsy.png**>*.

I also like the *Emotion* wallpaper from the KDE4 contest.
Preview: [http://files.ruphy.org/2007/11/vladstudio.jpg](http://files.ruphy.org/2007/11/vladstudio.jpg)
Link to zip with all contest winner 'papers: [http://xtravagant.exif.ro/wp-content/uploads/2008/01/kde4-wallpapers.zip](http://xtravagant.exif.ro/wp-content/uploads/2008/01/kde4-wallpapers.zip)

---

### Post by Xiong Chiamiov on 2008-05-03
> **oobuntoo said:**
> Extremely disappointed with KUNBUTU 8.04

Just a side note.

We're (mainly) just users, like you, not developers, so we can only help you do something, not change the way the release is.  And besides, it's a good thing to remember that you didn't pay for Kubuntu (or KDE).  When you're using a commercial Windows product, you can threaten (and in fact, often have to) to stop using it and tell all your friends about how terrible it is because they rely on people buying it to support themselves.  When you're discussing FOSS (free and open source software), you'll find that people only work on something if they think it's worthwhile.  If you're the only one wanting something changed, they'll just say, "We're not going to change it.  Get over it or use something else."

I guess what I'm trying to say is, don't try to get us in a panic to help you by throwing around phrases like "extremely disappointed".  I couldn't care less whether or not you used KDE, *buntu, or Linux.  Most of us here want to help people who want it, but are just having a hard time getting there.  We're just volunteers, so we don't have to put up with all the crap tech support does.

[SIZE="1"]some ideas taken from the excellent article "[Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")", especially section 3a[/SIZE]

---

### Post by Zorael on 2008-05-03
Pah, I was just about to link to that site. :>

"I'd demand a refund if I were you" cracks me up each time I read it, heh.

---

### Post by Kokopelli on 2008-05-03
> **oobuntoo said:**
> I've been using Kubuntu (KDE) exclusively, release after release, and noticed that things are getting worse. I had to look around for work-arounds for alot of things, and I'm just tired of doing that at this point. There are serveral things that have annoyed since Gutsy and is getting worse in Hardy. I'm just gonna list ONE here and see if anyone can find a solution for this:

In Hardy, one of the first things I have to change is the font size. The default size (10) is just too big, I changed it to 7. It's all good, except all programs that run as sudo will not respect this change; they still use font size of 10. In fact, this applies to not only fonts but themes and colors as well. There is no way to change settings for programs that run as sudo. I've tried sudo kcontrol, sudo systemsettings, and sudo any kcontrol module, then make changes to fonts, colors, or style but nothing works.

Programs that runs in sudo mode (adept, synaptic, etc,...) will use what ever the defaut settings are and there is no way to change them (easily).:confused:


I would be inclined to ignore this but curiosity got the better of me.
1) Alt-F2 => kcontrol
2) Appearance and Themes => fonts => Adjust all fonts.  Set to 7.
3) open terminal
4) sudo adept_manager
Mercy Me!!! The font changed.
repeat for font size 12 and confirmed.  Switch back to 7 and confirmed again.
Then for good measure repeated this on 3 other Hardy Kubuntu installs and one Gutsy Kubuntu.  I am not sure what the problem with adept is for you, but I do not think it is Kubuntu. 

Now for Synaptic I grant you will either need to change the default font for Gnome (do recall Synaptic is a Gnome program) or simply set a custom font for synaptic.  I realize it is an inconvenience but I would hardly call it a major one.  Even if you do consider it a problem that a Gnome program does not pick up the default font for KDE this is hardly a Kubuntu problem (Hardy or otherwise).  It is either a KDE or Gnome problem at best, not something specific to Kubuntu.  Personally I do not call it a problem at all but different strokes.

So can you describe your next problem?  And perhaps try and recall we are here to help not to listen to people gripe.

---

### Post by oobuntoo on 2008-05-11
I don't feel too bad any more. I'm not the only one who has this problem.

[http://ubuntuforums.org/showthread.php?t=637729]("http://ubuntuforums.org/showthread.php?t=637729")

[https://bugs.launchpad.net/ubuntu/+bug/200612]("https://bugs.launchpad.net/ubuntu/+bug/200612")

[http://bugs.kde.org/show_bug.cgi?id=146779]("http://bugs.kde.org/show_bug.cgi?id=146779")

---

### Post by oobuntoo on 2008-05-11
> **Igtenio said:**
> Also, if you're like me, where you prefer KDE over Gnome but hate Kubuntu itself, you could install KDE-Core through Synaptic or Apt-get. That'll install the basic KDE packages without any sort of Kubuntu branding or customization.

If you want a really sleek system, and can get away with it, you could also just install a Command-line System from the Alternate CD, and then execute;

```
sudo apt-get install xorg kde-core kdm
```



That's what I did when I was using Gutsy. I did the same thing with Hardy, but the problem of changing the look and feel of root applications is still there. I do prefer Synaptic over Adept. I have Ubuntu (the gnome-centric one) installed for now. I'll retry Kubuntu again on my spare machine when have time.

---

### Post by Christmas on 2008-05-11
I recommend you Debian Lenny with KDE. Kubuntu was a good KDE distro when 6.06 was released, but after that I switched too. I think it's lack of developers on KDE, and Mark Shuttleworth mainly focuses on Ubuntu (GNOME). Debian Lenny will come with 3.5.9 (guessing you don't want KDE 4.0 at the moment?) and will probably be the most stable KDE 3.5 up to date. Just give it a try. Good luck!

---

### Post by Zorael on 2008-05-11
KDE 3.5.9 is the same KDE 3.5.9 whichever distro you pick. There will be some minor differences in default settings, of course, but the major ones would be installed applications, as well as services running behind the scenes, below the graphical interface. grub/lilo/gfxgrub, usplash/splashy/fbcondecor, apparmor/selinux equavilence. Not to mention debian/slackware/gentoo (?) base.

One mustn't forget that Canonical and Ubuntu does *not* equal the Linux and Unix developer- and userbase as a whole. There are plenty of developers devoted to making KDE better. This - and the *buntu distro lineage - are just Gnome-centric. As such, *Kubuntu* receives less attention, but *KDE* does not.

As far as I've read, KDE even has a slightly larger userbase than Gnome has. Opinion, but I'd agree with KDE 3.5.9 being rock stable, and there's a whole lot of interesting stuff coming with KDE 4. Make that 4.1.

So no need to worry that KDE is "falling behind." In many ways, it's in its second wind. As for who's "in the lead", that's opinion. (*KDE! :>*)

I'm not completely innocent in the Neverending War either. See the first link in my sig.

---

