---
title: "KDE4.1 beta 2 released!"
date: 2008-06-24
forum: Desktop Environments
---

### Post by Naegling23 on 2008-06-24
Thoughts?

I'll download and run this when I get home today, is anyone already running it?

---

### Post by Zorael on 2008-06-24
Awesome! Hopefully packages'll show up on kubuntu.org soonish.

If/when you try it, please report. That is all. Carry on. :>

---

### Post by Naegling23 on 2008-06-24
Im a little confused about if its out for kubuntu or not.  kubuntu.org does not have a notice about it, but kde.org says it should be available.

Well, i'll let you know if its there when I get home, if not, I'll play the waiting game.

---

### Post by jlacroix on 2008-06-24
For me, some of 4.1 beta 2 is in the repositories, but some packages haven't been updated yet and are held back. I guess this means any time now when the dependencies are all updated we'll have beta 2. Here's hoping.

---

### Post by rolandixor on 2008-06-24
well, if I'm right, the updates are not working yet. two packages are complaining...

> E: /var/cache/apt/archives/kde-window-manager_4%3a4.0.83-0ubuntu1~hardy1~ppa5_i386.deb: trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.docbook', which is also in package kdebase-runtime-data
E: /var/cache/apt/archives/kdebase-workspace-data_4%3a4.0.83-0ubuntu1~hardy1~ppa5_all.deb: trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/screensaver/index.docbook', which is also in package kdebase-runtime-data



---

### Post by rolandixor on 2008-06-24
I hope this doesn't mean a long wait until I can fix that...

---

### Post by jlacroix on 2008-06-24
Me too, I'm VERY excited for Beta 2, I use the daily live image (which is slow) but it's quite a bit different from Beta 1. Beta 2 is just amazing. You guys won't be dissapointed, I just hope all the changes that are in the live edition right now make it into Beta 2.

---

### Post by Naegling23 on 2008-06-24
im really hoping beta2 does it for me.  I was pleased with the functionality, but there were some plasma crashes and bugs that made it not suitable for everyday use.  Im very excited to start the transition to kde4...I really like what I've seen so far.  Im hoping that panel hiding is added in this go around, but it wont kill me if I have to wait a little while longer.

I'm back at home and downloading the updates now.  Im also getting the package error, so I guess the packages are in the process of making it to the repositories at the current time?

I'll try again a little later.  Keep posting updates so we know when its good to go.

I noticed that kubuntu-kde4-desktop was not one of the updated packages, and that is the meta kde4 package, so Im going to assume not everything is in the repositories yet.

---

### Post by rolandixor on 2008-06-24
MAJOR UPDATE, there is a page on kubuntu.org on the new release!
not all the packages have been built yet, and I'm going to wait till the servers cool a bit.

---

### Post by jlacroix on 2008-06-24
> **rolandixor said:**
> MAJOR UPDATE, there is a page on kubuntu.org on the new release!
not all the packages have been built yet, and I'm going to wait till the servers cool a bit.

I don't see it on Kubuntu.com or Kubuntu.org...

---

### Post by Naegling23 on 2008-06-24
> **rolandixor said:**
> MAJOR UPDATE, there is a page on kubuntu.org on the new release!
not all the packages have been built yet, and I'm going to wait till the servers cool a bit.

hmm, not seeing the announcement.

If your talking about this link
[http://kubuntu.org/announcements/kde-4.1beta2.php](http://kubuntu.org/announcements/kde-4.1beta2.php)
then im not too sure, I have been seeing that link all day, but the top of the page mentions beta1, so I think that page is just a placeholder or a mistake as of now.

---

### Post by rolandixor on 2008-06-24
not really, KDE.org mentioned it...
I'll find the links in a moment...

---

### Post by rolandixor on 2008-06-24
[http://kubuntu.org/announcements/kde-4.1beta2.php](http://kubuntu.org/announcements/kde-4.1beta2.php)
[http://kde.org/info/4.0.83.php](http://kde.org/info/4.0.83.php)

if you click on these, your ubuntu install will be wiped, and you will get windows 95 instead... muhahahaha! long live MacOS T!!!

just kidding.

---

### Post by jlacroix on 2008-06-24
The Kubuntu announcement is just a place holder right now, it mentions Beta 1 in the text.

---

### Post by kde4-core-user on 2008-06-24
Hi!

Now, the Beta2 is ready to Install for Kubuntuusers. Looks really great, but I miss the folderview-plasmoid. I hope I get it back, tomorrow or whenever....

---

### Post by Spudgy on 2008-06-24
kmail-kde4 is hosed for me atm.

kmail: symbol lookup error: /usr/lib/kde4/lib/libkdepim.so.4: undefined symbol: _ZN13KRichTextEdit17mouseReleaseEventEP11QMouseEvent

The update for gwenview also wants to uninstall digikam.

---

### Post by Naegling23 on 2008-06-24
um...why is gwenview trying to remove digikam?

edit: sorry, spudgy beat me to it.

---

### Post by Spudgy on 2008-06-24
It looks like it's because of libkipi.

gwenview wants to install libkipi5 and uninstall libkipi0, which digikam depends on. Why both versions of the library can't be installed I have no idea.

---

### Post by jlacroix on 2008-06-24
Kubuntu.com now advertises the Beta 2 packages on the front page. When you click on it though it still references Beta 1 in the text which is probably a typo.

---

### Post by jlacroix on 2008-06-24
I updated to it just now, and I need help fixing some problems.

1.) The "Show Desktop" plasmoid is missing completely.

2.) Same with Folder View, that's gone too.

3.) My "Computer" menu on the Kickoff applications menu is blank. I need those entries back, some of them are impossible to recreate by just making shortcuts, for example, Samba shares is missing, as is Trash and the File System. How do I regenerate the Computer menu?

Edit: MAJOR thumbs down to whomever compiled these packages, the missing Show Desktop and Folder View widgets is not an issue on the live daily image.

---

### Post by TheUnabeefer on 2008-06-25
> **jlacroix said:**
> Edit: MAJOR thumbs down to whomever compiled these packages, the missing Show Desktop and Folder View widgets is not an issue on the live daily image.


Yeah, wtf? :confused:  I use those both constantly... well... used.

---

### Post by isaacj87 on 2008-06-25
I just updated a couple of hours ago. Seems okay to me, but I'm not liking the new "Panel Settings" It's not very intuitive. I also seem to have lost my system sounds...Any solution for that?

---

### Post by jlacroix on 2008-06-25
I'm wondering where I need to file bug reports at, the problems I'm experiencing aren't because of bugs in KDE 4.1, rather bugs with the compiling of Beta 2 specific to Ubuntu. I don't think there's a place to file PPA bugs, is there?

---

### Post by viikinki on 2008-06-25
I upgraded my laptop to KDE 4.1 beta2 yesterday. After the upgrade I could not log in any more. I got the error message "could not start kstartupconfig4". 

Has anyone else run into this problem? Any suggestion how to solve this?

---

### Post by ollesbrorsa on 2008-06-25
> **viikinki said:**
> I upgraded my laptop to KDE 4.1 beta2 yesterday. After the upgrade I could not log in any more. I got the error message "could not start kstartupconfig4". 

Has anyone else run into this problem? Any suggestion how to solve this?

I am experiencing the exact same problem. No luck on a remedy yet. Am currently away from my kubuntu laptop so I can't really try anything until I get back home.

Will follow this thread though...

Br,
ollesbrorsa

---

### Post by ponkarthik on 2008-06-25
Hi,

  I updated to 4.1 beta 2 but am missing folder view applet and many other plasmoids. Folder view is completely missing from the list. Most other plasmoids even though found in the list of plasmoids don't work. There is just a black circle placeholder coming up !! 

  Are these packages being rebuilt. If anybody has them working please let me know.

Thanks
Karthik

---

### Post by gaboo on 2008-06-25
Same problem here, on two different computers. And it's a packaging issue as I've no problem with a recent self built svn trunk version.

I think we just need to wait till the packages are fixed, this is an obvious bug.

---

### Post by Naegling23 on 2008-06-25
well, I installed it, but I didnt have a chance to try it out, I got stuck running errands all night...the wife decided I needed pants....I left of gwenview because im not ready to throw digikam to the curb if I have to still use 3.5 for the time being.  It sounds like the packages just have not all been uploaded yet.  Hopefully by the end of today everything will be fixed.  I'll post what I find (and hopefully on kde 4.1) later today.

---

### Post by viikinki on 2008-06-25
> **viikinki said:**
> I upgraded my laptop to KDE 4.1 beta2 yesterday. After the upgrade I could not log in any more. I got the error message "could not start kstartupconfig4". 

Has anyone else run into this problem? Any suggestion how to solve this?

UPDATE: I made a complete mess of my previous installation while trying to fix it (newbie mistake) so I needed to reinstall everything. Now everything works like a charm... KDE 4.1 Beta2 is brilliant!

---

### Post by jlacroix on 2008-06-25
> **viikinki said:**
> UPDATE: I made a complete mess of my previous installation while trying to fix it (newbie mistake) so I needed to reinstall everything. Now everything works like a charm... KDE 4.1 Beta2 is brilliant!

So your folder view and etc works fine? Did you just reinstall or remove everything first?

If I have to uninstall everything first, is there a way I can export some sort of text file that contains a list of all *kde4 packages I have installed? I installed several of them beyond the default configuration that I wouldn't be able to remember off the top of my head.

---

### Post by ponkarthik on 2008-06-25
Hi,

  Is folder view working for anyone ? Do we have to install or kdeplasmoids or extragear plasma ? 

Dolphin was crashing like mad but after further updates in the evening seems to be stable now.

Karthik

---

### Post by kde4-core-user on 2008-06-25
FolderView is in kdebase, but it`s still missing on my Beta2-Installation. I hope it comes back soon with another Update.

The extragear-package from Beta1 is now "kdeplasmoids" in Beta2 !

---

### Post by viikinki on 2008-06-25
> **jlacroix said:**
> So your folder view and etc works fine? Did you just reinstall or remove everything first?

If I have to uninstall everything first, is there a way I can export some sort of text file that contains a list of all *kde4 packages I have installed? I installed several of them beyond the default configuration that I wouldn't be able to remember off the top of my head.

Sorry for late reply. I installed kubuntu 8.04 (KDE4.0.1) from cd and then upgraded to KDE4.1 Beta2. 

The plasma fun is nowadays in kdeplasmoids package. However the folder view is basically the only one missing (but did not notice it because I am not using it, sorry!)

---

### Post by jlacroix on 2008-06-25
In that case I guess we're probably going to have to wait until RC1 for these issues to be fixed. Since I don't know where to report bugs on these packages, there's no way to inform anyone that there's a problem. I hope just like everyone else that someone notices these problems and fixes them but without a way of reporting bugs I don't see that happening.

I'm bummed out right now, KDE 4.1 Beta 2 is amazing but you wouldn't notice it from these terrible packages. Does anyone test these things anymore, or am I just old fashioned?

Apt is also complaining about kdesdk missing a dependency so I have a package that is being held back without any idea on when or if its dependency will ever be released.

---

### Post by Rede on 2008-06-25
Really missing my Folder View plasmoid!

---

### Post by telex4 on 2008-06-25
> **Spudgy said:**
> kmail-kde4 is hosed for me atm.

kmail: symbol lookup error: /usr/lib/kde4/lib/libkdepim.so.4: undefined symbol: _ZN13KRichTextEdit17mouseReleaseEventEP11QMouseEvent

I have the same problem with all KDE PIM apps (unsurprisingly). Looking forward to an updated package...

---

### Post by jlacroix on 2008-06-25
I created a bug report:

[https://bugs.launchpad.net/ubuntu/+source/kdebase-kde4/+bug/243062](https://bugs.launchpad.net/ubuntu/+source/kdebase-kde4/+bug/243062)

Everyone: If you have any of those or similar problems, please comment on that bug report so we can show them that this is a widespread problem and add anything new you may have found to help them.

---

### Post by jlacroix on 2008-06-25
Now when I try to dist-upgrade it wants to remove kdebase-kde4 and other packages I'm pretty sure are required. Anyone else having that problem?

---

### Post by Sokraates on 2008-06-25
I'm using KDE4.1 beta2 on Hardy and am extremely pleased. I've been using KDE4 since KDE4.0 Beta1, so I know what to compare it to. :)

The only gripe I have is that I had to delete my ~/.kde4-folder to make KDE4 start. It was no big loss, since I've switched back to KDE3 after 4.0.4, but it's still annoying. Though I can't rule out that this was due to a packaging problem, which was fixed afterwards.

I use a mixed setup with GTK+ and KDE3-apps thrown in between and they all work very well. The only problem I experience are glitches with the theming for GTK+-apps but it's not very noticable. At least for Firefox, the [Mozilla theme]("https://addons.mozilla.org/de/firefox/addon/7574") works wonders.

Configurability is finally back. Adding actions to the screen edges makes compositing really useful now. The only option I'm missing is to have the panel autohide. A bug has already been filed on this subject long ago. I also notice that I can't move icons on the panel. IIRC this should be possible in this Beta, so I assume a packaging bug. Personally, I don't miss this feature though, so I don't mind.

The one and only feature that made my jaw drop (and it's been a long time since a piece of software did that) was the startup. While the fading-in icons in the splash looked nice, it was stunned when the desktop appeared. First you only see the wallpaper, then the panel and icons fade in extremely smoothly, just slowly enough for you to notice the effect but fast enough so that you don't have the feeling of wasting time on this effect. It's a brilliant little addition that gives a great first impression.

I've used KDE4.1 Beta2 heavily the past day and haven't experienced a single crash or any other kind of error. So I think that I've finally found my new main DE.

---

### Post by Rede on 2008-06-25
Folder View is back after a package was fixed and:

```
sudo apt-get install kdebase-plasma-kde4
```

---

### Post by Sokraates on 2008-06-25
> **jlacroix said:**
> Now when I try to dist-upgrade it wants to remove kdebase-kde4 and other packages I'm pretty sure are required. Anyone else having that problem?

I just checked and I don't have any problem.

---

### Post by Naegling23 on 2008-06-25
I realize that this is actually a kde 4.1 beta 1 question, but what ever happened to the wallpaper that came with 4.0?

I kind of liked some of the pictures.

---

### Post by TheUnabeefer on 2008-06-25
Okay, don't know if anyone else has mentioned this, but aside from the extragear packages being switched to kdeplasmoids (you have to remove extragear and then install kdeplasmoids manually... well, I had to at least) 

the FOLDER VIEW (caps only to draw attention for those of us who were missing said plasmoid) plasmoid is under a SEPERATE package called "kdebase-plasma-kde4"

I installed that and the kdeplasmoids, and now my Folder View works wonderfully, as well as now having a "Show Dashboard" plasmoid in addition to "Show Desktop"  One actually shows the desktop devoid of plasmoids [edit]oops, not devoid of plasmoids, just not dashboardy[/edit], the other shows the dashboard as before.

Neat. :guitar:

---

### Post by jlacroix on 2008-06-25
Thanks you guys, I'll try that stuff tonight and check to see what's going on. Two questions remain though that I'm hoping one of you can help me out with:

1.) The wallpaper that appears when KDE4 is starting up is really sweet. I want it. It's not in the wallpaper list in the desktop settings. I was hoping someone may know where it is so I can use it as wallpaper?

2.) Once I get everything set up correctly, I'd like to export a text file containing a list of all the KDE4 packages I have installed so I can easily duplicate it on another box. I did it once but can't remember how, I think it had something to do with the cat command.

---

### Post by edvar on 2008-06-25
I can't find this package:

apt-get install kdebase-plasma-kde4
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kdebase-plasma-kde4

________________________

Nevermind... forgot to do an "apt-get update" before...
I'll test it when I get home. Thanks!

---

### Post by jlacroix on 2008-06-25
Installing the two packages mentioned here fixed it for me. Thanks everyone!

---

### Post by Sokraates on 2008-06-26
> **Naegling23 said:**
> I realize that this is actually a kde 4.1 beta 1 question, but what ever happened to the wallpaper that came with 4.0?

I kind of liked some of the pictures.

You can find them in kdewallpapers-kde4 or kde-workspace-wallpapers (I have both installed). There you find all of them.

@Unabeefer: Thanks for the info. The devs seem to have fixed the issue of missing folderview by adding an extra package for that plasmoid only. I don't think we'll be seeing that package again in the next release. ;)


QUESTION (just to get everyone's attention): Is there a way to bind "Show Dasboard" (Ctrl+F12) to a screen corner/edge? I remember there was a "Plasma" option in Systemsettings, but it seems to be gone now. Thanks in advance.

---

### Post by Arathorn on 2008-06-26
This new beta works very well, but I have three problems.
1. The new startup-splash is nice, but I'd like an option to let it use the wallpaper that I use on the desktop as background.
2. Ever since using KDE 4 I've had the problem that I can't find a way to use Systemsettings in root mode without starting it with sudo or kdesu systemsettings. The help file mentions an "Administrator Mode" button, but either I'm blind or it isn't there.
3. When I've started systemsettings as root and try to configure KDM's background, I get an error when I want to pick a file to use that systemsettings can't communicate with KLauncher and I can't browse any files. Anyone else having these problems?

---

### Post by jlacroix on 2008-06-26
If I type "sudo apt-get autoremove" it wants to remove the following packages:

> automoc cervisia-kde4 kapptemplate-kde4 kbugbuster-kde4 kcachegrind-kde4
  kde4-core kdebase-workspace kdelibs5-dev kdepimlibs5-dev kdesdk-kde4
  kdesdk-kio-plugins-kde4 kdesdk-misc-kde4 kdesdk-scripts-kde4
  kdesdk-strigi-plugins-kde4 kompare-kde4 ksysguardd-kde4 kuiviewer-kde4
  libboost-dev libenchant-dev libgif-dev libgpgme11-dev libkeyutils-dev
  libkonq5-dev libldap2-dev libphonon-dev libplasma-dev libpoppler-qt4-2
  libpth-dev libqimageblitz-dev libsmbclient-dev libsoprano-dev
  libstreamanalyzer-dev libstreams-dev libusb-dev libxkbfile-dev libxtst-dev
  poxml-kde4 umbrello-kde4 x11proto-record-dev


Is that safe? kdebase-workspace and kde4-core I would think would be necessary, and I know I don't want to get rid of ksysguardd unless it was given a replacement.

---

### Post by Arathorn on 2008-06-26
You'd better not use auto-remove when you're in the middle or short after a massive upgrade such as this one. Two days ago apt-get also wanted to remove ksysguardd for me, but that package was still needed for Ksysguard. If you don't need the extra space now, don't do it.

---

### Post by Naegling23 on 2008-06-26
hmm, I tried some gaming just to see what the performance was.

I fired up doom3 (I have the effects enabled, wobbly windows, and tranceparency, but I turned off shadows)

Very choppy/slow.  Performance appears to be well behind kde3.5 in that department.  Is this something that is going to be fixed?  Is there a konsole command that I can use to turn off all effects and back on again when the game is done (sort of like --kwin replace/--compiz replace)?  Or is this due to beta status?

Im surprised, I heard performance was improved, but thats not what I'm seeing.

---

### Post by JGT on 2008-06-26
> **jlacroix said:**
> Me too, I'm VERY excited for Beta 2, I use the daily live image (which is slow) but it's quite a bit different from Beta 1. Beta 2 is just amazing. You guys won't be dissapointed, I just hope all the changes that are in the live edition right now make it into Beta 2.

Hi

Is that a Kubuntu daily live image? Where do you download that from?

Thanks

John

---

### Post by jlacroix on 2008-06-26
> **JGT said:**
> Hi

Is that a Kubuntu daily live image? Where do you download that from?

Thanks

John

[http://etotheipiplusone.com/kde4daily/docs/kde4daily.html](http://etotheipiplusone.com/kde4daily/docs/kde4daily.html)

---

### Post by jlacroix on 2008-06-26
> **Arathorn said:**
> You'd better not use auto-remove when you're in the middle or short after a massive upgrade such as this one. Two days ago apt-get also wanted to remove ksysguardd for me, but that package was still needed for Ksysguard. If you don't need the extra space now, don't do it.

I need to know how to stop it from wanting to remove all that stuff. It wanting to autoremove needed programs tells me that something is missing in my set up.

---

### Post by rolandixor on 2008-06-26
I've upgraded all my packages, and it's singing a lovely tune. Looks like it could do with a little work still but it's getting closer to a really usable desktop

---

### Post by isaacj87 on 2008-06-26
Hey everyone,

Did anyone else's KDM get screwed up after the update? I'm using Kubuntu-Members-KDE4 PPA. It doesn't look how it used to on 4.0.4.

Can anybody help me out?

Thanks!

---

### Post by Naegling23 on 2008-06-26
well, yesterday I played around a bit, moved some stuff around, and started to set up my desktop to my liking.

today I logged in, and was greeted with the black desktop of doom that plagued me in beta 1 (I think its a plasma crash).  I know I can get rid of it by deleting my .kde4 folder, but that defeats the whole purpose of customizing my desktop.

Guess im waiting for RC1, sorry kde4, your still not ready.

---

### Post by rolandixor on 2008-06-26
> **jlacroix said:**
> I updated to it just now, and I need help fixing some problems.

1.) The "Show Desktop" plasmoid is missing completely.

2.) Same with Folder View, that's gone too.

3.) My "Computer" menu on the Kickoff applications menu is blank. I need those entries back, some of them are impossible to recreate by just making shortcuts, for example, Samba shares is missing, as is Trash and the File System. How do I regenerate the Computer menu?

Edit: MAJOR thumbs down to whomever compiled these packages, the missing Show Desktop and Folder View widgets is not an issue on the live daily image.

these are included in some other packages which probably have yet to install. Refresh your packages and check for anything new in the repositories.

---

