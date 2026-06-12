---
title: "Basic Questions with KDE."
date: 2009-11-24
forum: Desktop Environments
---

### Post by Roasted on 2009-11-24
Long time Gnome user here, ended up setting up my Ubuntu system to dual boot with Kubuntu to try it out. So far - I'm fricken loving KDE. Very smooth, very solid, and very quick. I just might make the full time switch. But before that, I have a few questions I'd like answered.

1 - I have dual monitors. In Gnome I used to just use 1 big wallpaper across both monitors. In KDE it doesn't seem as if I can do that. How can I get wallpapers on both monitors? I can do this by either 1 wallpaper per monitor or 1 large wallpaper to span across both. I just need to know how to do this.

2 - How do I get rid of that bouncing icon whenever I launch an application?

3 - I tried to install the latest Virtualbox from their web site but it errors out when I try to launch the deb. I'm running Jaunty 9.04 64 bit and that's the package I got but it errored out. Any ideas?

4 - Because Karmic had problem with multiple drives in my system when I tried to use Ubuntu Karmic, I didn't even try to use Kubuntu Karmic - So I'm using Kubuntu Jaunty 64 bit. But I'd like the latest KDE version - how do I upgrade KDE in Jaunty to have the latest available?

---

### Post by Zorael on 2009-11-24
1. Hmm. Hit the cashew (top right corner) and Zoom Out. Then pick Configure Plasma and "Different activity for each desktop". That should hopefully do the trick with two screens; it certainly does with multiple desktops.

2. System Settings -> Desktop -> Launch Feedback. The placing is a bit unintuitive.

3. Any interesting error output?

4. There seems to be 4.3.2 packages for Jaunty in the Kubuntu backports ppa ([ppa:kubuntu-ppa/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports?field.series_filter=jaunty)). There doesn't seem to be any 4.3.3 packages, though I guess you could try to add [the Karmic ones](https://launchpad.net/~kubuntu-ppa/+archive/ppa) and see if your package manager accepts them as updates (or throws in the towel because of unresolvable dependencies).

---

### Post by bentoport on 2009-11-24
I'm new to Linux and installed ubuntu 9.10 KK three days ago, all went well, except that when I login choosing kde desktop I have the following problems:

1 - Amarok refuses to play files (located on a windows partition). It recognizes them but when I touch play nothing happens.

2- I don't seem to have all the options with KDE, for ex. in the Settings menu I don't have Appearance as an option.

3- No shutdown or Restart option availabe (in the Leave menu I have Logout, Lock, Swith use, Hibernate and Sleep).

Any ideas why is this happening? Thks.

---

### Post by gastly on 2009-11-24
> **bentoport said:**
> 
1 - Amarok refuses to play files (located on a windows partition). It recognizes them but when I touch play nothing happens.

You need to install **libxine1-ffmpeg**

```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by tuxeee on 2009-11-24
> **Roasted said:**
> Long time Gnome user here, ended up setting up my Ubuntu system to dual boot with Kubuntu to try it out. So far - I'm fricken loving KDE. Very smooth, very solid, and very quick. I just might make the full time switch.  

can you please expand on why you'd switch over to Kubuntu?
whats the pros over gnome? (from your experience)

---

### Post by Roasted on 2009-11-24
I didn't fully switch over. I still actively use Ubuntu with Gnome. You see, my partitions are split from root and home. Originally my disk was:

20gb Root - Ubuntu
380gb - Home

I downsized the 380 to 360 and left the remaining 20gb to Kubuntu, making my disk look like:

20gb Root - Ubuntu
360gb Home
20gb Root - Kubuntu

Both Kubuntu and Ubuntu point to the same home directory. So I literally share the same documents, personal data, music, pictures, etc between both Kubuntu and Ubuntu. This allows me to tinker with Kubuntu knowing I can reboot and be back to Ubuntu if I need more familiar ground.

I guess I came into KDE thinking that what Gnome users say against it were true. That it was bloated, unstable, stupidly laid out, etc. I find that not to be the case. It is unusually fast on my computer. Not faster than Gnome, but no slower than Gnome either. I guess I just really like the way things are laid out, the menu system, the overlay that seems very customizable, etc.

I've been following the development of Gnome Shell and I use it on a spare computer, but I'm just not totally sold on it. Yes it's unfair to judge this early since it's in what, some kind of Alpha stage, but even still, I'm just not sure if it's my cup of tea to have the overlay activated EVERY time I want to access ANYTHING. I like being able to activate the overlay if I need to but not get dizzy when I explore my menu to open a program. This is something that KDE already has that was nice to see. The one thing that bothers me about KDE is the panel being at the bottom. Once you switch the panel to the top, it suddenly felt more familiar to my Gnome roots. Panel at the top - Dock at the bottom - Just like I had it set up in Gnome. I can see how the panel at the bottom would be a little more enticing to making hardcore Windows users feel at home, but thanks to Gnome I prefer the panel at the top - which was the first thing I changed when I booted into KDE. :) 

I love Gnome. It has a special place with me and I'm sure I'll always use it. But KDE is pretty damn robust, and I definitely see why it's a very worthy competitor to Gnome.

---

### Post by bentoport on 2009-11-24
> **gastly said:**
> You need to install **libxine1-ffmpeg**

```
sudo apt-get install libxine1-ffmpeg
```


Thanks ;-)

---

### Post by bobzr on 2009-11-24
> **Roasted said:**
> Panel at the top - Dock at the bottom - Just like I had it set up in Gnome. I can see how the panel at the bottom would be a little more enticing to making hardcore Windows users feel at home, but thanks to Gnome I prefer the panel at the top - which was the first thing I changed when I booted into KDE

I've done exactly the same and I'm also using both gnome and kde, but I still prefer Gnome. I'm searching for a good KDE dock like AWN but I couldn't find yet. (Kooldock, Daisy, etc. they're all unstable).
KDE is better for the available software and I can't find any app like KDEnlive, KeepassX or KMyMoney in Gnome. But it seems like KDE 4 is not yet mature and apps often crash.

---

### Post by Roasted on 2009-11-24
> **bobzr said:**
> I've done exactly the same and I'm also using both gnome and kde, but I still prefer Gnome. I'm searching for a good KDE dock like AWN but I couldn't find yet. (Kooldock, Daisy, etc. they're all unstable).
KDE is better for the available software and I can't find any app like KDEnlive, KeepassX or KMyMoney in Gnome. But it seems like KDE 4 is not yet mature and apps often crash.

Based on what I read (on web sites, forums, etc), KDE 4.2 fixed a lot of bugs. A lot of die hard KDE fans I spoke to blatantly said KDE 4 brought on a lot of bugs while KDE 4.2 fixed a ton. And currently we're at... 4.3.3 or something? 

As far as the apps go, a lot of apps I used were already KDE apps to begin with - Amarok, Ktorrent, etc. Never had a problem in Gnome with them - so far no problems in KDE with them. *knock on wood*

The only times I had KDE crash was on my spare computer. But when I open Google Earth, Google Earth flashes like a high speed white disco scene. Not only that, but my login splash screen for when Ubuntu and Kubuntu are loading, it looks choppy and mixed up as if it was a puzzle gone bad. This suggests I have a serious video card issue. I'm trying to find a spare PCI video card to test this but, I have issues in Ubuntu on that machine too, so seeing them in Kubuntu wasn't too surprising.

Have any users with KDE 4.2+ experienced any problems with stability?

Something kinda funny - I found an article somewhere with Linus Torvalds backing up KDE 100%. It was an interesting read...

---

### Post by Zorael on 2009-11-24
> **Roasted said:**
> Something kinda funny - I found an article somewhere with Linus Torvalds backing up KDE 100%. It was an interesting read...
He's gone back and forth, I think. He doesn't like the way GNOME wants to make things simple, and he detested KDE 4.0 which was inarguably in a pretty poor (and very alpha) state.

2. Appearance isn't there? That's alarming. I'd try reinstalling systemsettings.
```
$ sudo aptitude reinstall systemsettings
```

3. System Settings -> Advanced tab -> Session Manager, check Offer shutdown options.

---

### Post by Roasted on 2009-11-24
> **Zorael said:**
> He's gone back and forth, I think. He doesn't like the way GNOME wants to make things simple, and he detested KDE 4.0 which was inarguably in a pretty poor (and very alpha) state.

2. Appearance isn't there? That's alarming. I'd try reinstalling systemsettings.
```
$ sudo aptitude reinstall systemsettings
```

3. System Settings -> Advanced tab -> Session Manager, check Offer shutdown options.

Yeah, it doesn't seem to be any doubt there that KDE 4.0 was kind of a bust. But hey, at least they tried something new and have it pretty refined now with the later versions of KDE.

I'm curious to see what happens with Gnome Shell. They're rebuilding it a good ways - so they might have the same alpha style final release KDE 4.0 did. *shrug*

---

### Post by Roasted on 2009-11-24
Virtualbox Error - 

"Sorry - An Error Has Occured"

Traceback (most recent call last): File "/usr/lib/python2.6/dist-packages/packagekit/daemonBackend.py", line 109, in run threading.Thread.run(self) File "/usr/lib/python2.6/threading.py", line 477, in run self.__target(*self.__args, **self.__kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 168, in wrapper func(*args, **kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 1263, in doInstallFiles if not deb.checkDeb(): File "/usr/lib/packagekit/debfile.py", line 365, in checkDeb if not self.checkConflicts(): File "/usr/lib/packagekit/debfile.py", line 313, in checkConflicts if self._checkConflictsOrGroup(or_group): File "/usr/lib/packagekit/debfile.py", line 197, in _checkConflictsOrGroup if self.pkgName == pkg.name: AttributeError: 'DebPackage' object has no attribute 'pkgName'

---

### Post by Roasted on 2009-11-24
Also - when I apply a theme to Kubuntu, it only applies to the panel. What's up with this? I want the theme to change EVERYTHING.

EDIT - I also can't seem to set Firefox as my default browser, even though I tried in the default applications section of system settings. When people send me links, Konq still opens. Nothing against Konq - but I want Firefox. :(

---

### Post by Roasted on 2009-11-26
So I'm trying to find a good sound control icon for the panel. I have kmix but uh, that kind of sucks. In Gnome I liked being able to scroll over the icon and that would adjust the volume accordingly. Besides kmix is there any volume controllers out there worthwhile? Or am I perhaps doing something wrong with kmix?

And yes - I checked add-widgets already and didn't notice anything.

---

### Post by Roasted on 2009-11-26
*Up*

Whenever I empty the recycle bin, I get an error that there's a file that doesn't exist in the trash can. The trash can is empty. It has nothing in it. That's good. But I get this error no matter how many times I empty it, saying this file does not exist. Whaaaaat?

---

### Post by Zorael on 2009-11-27
> **Roasted said:**
> Virtualbox Error - 

"Sorry - An Error Has Occured"

Traceback (most recent call last): File "/usr/lib/python2.6/dist-packages/packagekit/daemonBackend.py", line 109, in run threading.Thread.run(self) File "/usr/lib/python2.6/threading.py", line 477, in run self.__target(*self.__args, **self.__kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 168, in wrapper func(*args, **kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 1263, in doInstallFiles if not deb.checkDeb(): File "/usr/lib/packagekit/debfile.py", line 365, in checkDeb if not self.checkConflicts(): File "/usr/lib/packagekit/debfile.py", line 313, in checkConflicts if self._checkConflictsOrGroup(or_group): File "/usr/lib/packagekit/debfile.py", line 197, in _checkConflictsOrGroup if self.pkgName == pkg.name: AttributeError: 'DebPackage' object has no attribute 'pkgName'
That sounds like a PackageKit bug. To the launchpad mobile!

How are you installing it? Via GDebiKDE? Perhaps it'll work if you do it from a command line.

> **Roasted said:**
> Also - when I apply a theme to Kubuntu, it only applies to the panel. What's up with this? I want the theme to change EVERYTHING.

EDIT - I also can't seem to set Firefox as my default browser, even though I tried in the default applications section of system settings. When people send me links, Konq still opens. Nothing against Konq - but I want Firefox. :(
Theming; the system settings module seems to be a tool to import and change themes. But when changing the theme via Desktop settings (right-click the desktop space), it properly themes not only my panel, but my analog clock, notify popups, etc. This is with Karmic's 4.3.3. (edit: FWIW, you can grab the **kdeartwork** package for the official theme bundle.)

As for Firefox; from what app are you opening the links? Depending on the level of KDE integration, they may not listen to KDE's settings but rather the x-www-browser alternative. Pidgin?
```
$ update-alternatives --config x-www-browser
```
Perform it as sudo to make it a system-wide setting.

> **Roasted said:**
> So I'm trying to find a good sound control icon for the panel. I have kmix but uh, that kind of sucks. In Gnome I liked being able to scroll over the icon and that would adjust the volume accordingly. Besides kmix is there any volume controllers out there worthwhile? Or am I perhaps doing something wrong with kmix?

And yes - I checked add-widgets already and didn't notice anything.
I don't think any such exist; I just use the kmix tray icon and my volume up/down keys. It's a thought though, might be worthy of a [brainstorm entry](http://forum.kde.org/brainstorm.php#cat83).

> **Roasted said:**
> *Up*

Whenever I empty the recycle bin, I get an error that there's a file that doesn't exist in the trash can. The trash can is empty. It has nothing in it. That's good. But I get this error no matter how many times I empty it, saying this file does not exist. Whaaaaat?
I'm not sure I understand. I'd try manually clearing the Trash directory and see if that helps.
```
$ rm -rf ~/.local/share/Trash/*
```

---

### Post by Roasted on 2009-11-27
It must be a bug with KPackageKit or something, because I can install the package just fine with GDebi Package Installer. It's just KPackageKit was my default, so that's what I ran with and that's when I got the error.

Has anybody used KPackageKit to install a .deb package and have this error in Kubuntu 9.04 with KDE 4.3.2? In particular, has anybody done with with the VirtualBox deb from the web site?

EDIT - The above was explained to me in this thread. I figured I'd link it here for learning purposes in case anybody else digs up this thread with the same problem.

[http://ubuntuforums.org/showthread.php?t=1338877](http://ubuntuforums.org/showthread.php?t=1338877)

---

### Post by ac7ss on 2009-11-29
> **Roasted said:**
> I didn't fully switch over. I still actively use Ubuntu with Gnome. You see, my partitions are split from root and home. Originally my disk was:

20gb Root - Ubuntu
380gb - Home

I downsized the 380 to 360 and left the remaining 20gb to Kubuntu, making my disk look like:

20gb Root - Ubuntu
360gb Home
20gb Root - Kubuntu

Both Kubuntu and Ubuntu point to the same home directory. So I ...

I don't understand the separate Root systems. My main machine (Family use) is "Ubuntu" as installed with the Gnome login screen, but from there the system diverges. I use KDE primarily and my wife uses Gnome. At any login, I can choose Fluxbox, XFCE, Gnome, Blackbox or KDE depending on what I am going to do. With the separate root systems you are inviting trouble if you upgrade on one side to a new version of a software package that may use a new file format, and the other root system won't have the newer software. Not to mention password file trouble.

I favor KDE most of the time.

---

### Post by Roasted on 2009-11-29
> **ac7ss said:**
> I don't understand the separate Root systems. My main machine (Family use) is "Ubuntu" as installed with the Gnome login screen, but from there the system diverges. I use KDE primarily and my wife uses Gnome. At any login, I can choose Fluxbox, XFCE, Gnome, Blackbox or KDE depending on what I am going to do. With the separate root systems you are inviting trouble if you upgrade on one side to a new version of a software package that may use a new file format, and the other root system won't have the newer software. Not to mention password file trouble.

I favor KDE most of the time.

Honestly, I don't know why I use them like that either.

You see, I have a spare computer here I do a lot of testing and messing around with. I set up Ubuntu on it and installed KDE, and it backfired.

I didn't want to put my main system through that since I also have several services running on it that I like to keep running. Plus I wanted to start clean with a fresh install of Kubuntu to really see what people were talking about.

Later I found out my spare computer has some problems with the video card anyway, so I think some of my issues may have been related to that since I was having severe video issues.

Overall, I'm glad I did a fresh install of Kubuntu and tried it. I'm hooked on it now.

Gnome - I love you, but I'm stickin with KDE. I find there's a lot more features in the GUI level (despite the fact I'm a terminal junkie) and things are laid out in a manner I prefer. Good work!

---

### Post by Dullstar on 2009-11-30
> **Roasted said:**
> Something kinda funny - I found an article somewhere with Linus Torvalds backing up KDE 100%. It was an interesting read...

Is [_this_](http://www.desktoplinux.com/news/NS8745257437.html) what you are thinking of?  The article mentioned KDE once, but it was in a question towards readers.  Linus, as far as we can tell from this article, said nothing about KDE here.

---

### Post by Roasted on 2009-11-30
> **Dullstar said:**
> Is [_this_](http://www.desktoplinux.com/news/NS8745257437.html) what you are thinking of?  The article mentioned KDE once, but it was in a question towards readers.  Linus, as far as we can tell from this article, said nothing about KDE here.

That was one of them. I recognize that picture of the guy there. I read a total of 2 or 3 web sites that suggested that while Linus has bounced between KDE and Gnome before, that he has spoken out before and mentioned that KDE is his sweet spot.

---

### Post by Nanday on 2009-11-30
I have also made the switch to KDE a few days ago... KDE4 is now really shining in my PC, but since I'm a newcomer, I cannot find just one thing that I loved about Compiz/Beryl... Where is the Zoom? I mean, compiz (desktop effects in Ubuntu Gnome) made Win+Mouse Scroll Wheel zoom in. It was a really lovely feature, that I cannot find in Kubuntu (KWin). Any help here?

---

### Post by Zorael on 2009-11-30
> **Nanday said:**
> I have also made the switch to KDE a few days ago... KDE4 is now really shining in my PC, but since I'm a newcomer, I cannot find just one thing that I loved about Compiz/Beryl... Where is the Zoom? I mean, compiz (desktop effects in Ubuntu Gnome) made Win+Mouse Scroll Wheel zoom in. It was a really lovely feature, that I cannot find in Kubuntu (KWin). Any help here?
Wouldn't that be the Zoom effect in System Settings -> Desktop -> Desktop Effects -> All Effects? I don't have a mouse on this machine so I can't see if it will react to scrolling, but it works if I bind it to keys, at least.

---

### Post by Roasted on 2009-11-30
> **Nanday said:**
> I have also made the switch to KDE a few days ago... KDE4 is now really shining in my PC, but since I'm a newcomer, I cannot find just one thing that I loved about Compiz/Beryl... Where is the Zoom? I mean, compiz (desktop effects in Ubuntu Gnome) made Win+Mouse Scroll Wheel zoom in. It was a really lovely feature, that I cannot find in Kubuntu (KWin). Any help here?

Yeah, I hear you there. It was so confusing to go to KDE. But not because it was hard. Because it was too logical in the manner it was laid out. For example, it took me forever to understand what was happening when I was looking for a new theme. Oh wait, you mean KDE links you to KDE-Look.org right there within the themes window within the OS without having to go to the web site? Sounds like an easy concept, but it took me a couple minutes to figure out what was happening!

Glad you're enjoying it. I know I am. Cheers!

---

### Post by Nanday on 2009-11-30
> **Zorael said:**
> Wouldn't that be the Zoom effect in System Settings -> Desktop -> Desktop Effects -> All Effects? I don't have a mouse on this machien so I can't see if it will react to scrolling, but it works if I bind it to keys, at least.

Yep, it is there, but I can't assign to the scroll wheel + win as I got used to... I don't know why, the scroll wheel works flawlessly, but when I try to reassign the default combination, it just don't "see" the scrolling. In fact, there are some combinations that it doesn't react to.

---

### Post by wipmonkey on 2010-05-14
I have a workaround. It will map Super+mouse scroll to the default kde zoom in/out "meta+=/-"

first we need to install xautomation and xbindkeys
Atl-F2
```

kpackagekit --install-package-name xautomation --install-package-name xbindkeys

```

create/edit a file called ~/.xbindkeysrc
this can be done with:

Alt+F2 

```
kate ~/.xbindkeysrc
```


```

"xte 'keydown Super_R' 'key equal'"
   Mod4 + Super_L  + b:4

"xte 'keydown Super_R' 'key minus'"
   Mod4 + Super_L  + b:5

"xte 'keydown Super_R' 'key 0'"
   Mod4 + Super_L  + b:2


```
that last block is optional it bind the middle button to zoom reset "meta+0".
the b:# is the mouse number and it corresponds with xev output.


Start xbindkeys with the config we just made:
Alt+F2

```
xbindkeys
```

now to make it start xbindkeys every time KDE starts we will create a static link to xbindkeys in the KDE Autostart folder in our home directory. 

Alt+F2
```
ln -s /usr/bin/xbindkeys ~/.kde/Autostart/xbindkeys

```

---

### Post by Linuxratty on 2012-11-17
> **wipmonkey said:**
> I  workaround. It will map Super+mouse scroll to the default kde zoom in/out "meta+=/-"


[SIZE="2"]Holy cow!!!!  I have been so wanting to do this with KDE!!! THANK YOU SO MUCH!![/SIZE]:)

---

### Post by wildmanne39 on 2012-11-17
Old thread closed.

---

