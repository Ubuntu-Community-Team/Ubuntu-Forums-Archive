---
title: "Update has destroyed KDE"
date: 2008-05-09
forum: Desktop Environments
---

### Post by ProbablyX on 2008-05-09
Hello!

I just updated to backlogs for kubuntu, which seems to have been a bad move as I no longer can use KDE4...

I had 4.0.3 before working fine, but after I upgraded to 4.0.4 kdm no longer has a background image, it's just gray. Also when I login to KDE4 it just shows a "starting command" cursor and does nothing at all. It does however manage after like 2 minutes to launch yakuake (which is a KDE3 app). If I try to open Konqueror or Kopete I can do so, but theres no titlebar, that is theres no kwin and the About box still says its KDE 4.0.3. 

If I try to start kwin4 manually the command isnt found, even though kdewin-kde4 is installed.
I've tried "apt-get install kubuntu-kde4-desktop" but it's already installed.
I've checked in adept and my packages are version 4.0.4..
Im currently on KDE 3.5 and it's working fine.
However, I'd like to get back to KDE4 as Ive gotten used to it =/

Thankful for any help!

---

### Post by Zorael on 2008-05-09
You could try to rename/delete **~/.kde4** from a terminal/KDE3 session to make sure your settings aren't messing things up.

Failing that, I'd try completely removing any package containing 'kde4' in its name and then reinstalling either **kubuntu-kde4-desktop** if you want the whole package (with games and everything), or **kde4-core** if you just want the environment and basic utilities, like konsole-kde4. Graphical way would be to open up Adept Manager, search for kde4, tag everything for **purging**. It shouldn't remove anything quintessential to your kde3 setup; they're made to be separate.

Terminal way:
```
$ sudo aptitude purge ~nkde4
```

Then reinstall.
```
$ sudo aptitude install kde4-core              # skeletal installation
$ sudo aptitude install kubuntu-kde4-desktop   # whole bunch of more stuff
```

---

### Post by mutzinet on 2008-05-09
I did get the exact same problem. Gray background of kdm (still unsolved), and corrupted kwin once logged in. Symptoms were: No frames on the windows, only one virtual desktop, and no switching between windows (i.e. keyboard active only in the first window that popped up, skype in my case. 

I got out of this strange situation with Alt+F2, and since the keyboard wouldn't focus on the "run command" window, I had to use the drop down menu next to the command bar to find older commands. And eventually among the commands I had already used was: "kwin --replace". This made everything come back and since then everything is fine (except the background of kdm, as mentionned before, and the "About" windows that all still show "4.0.3" instead of 4.0.4).

---

### Post by Zorael on 2008-05-09
Please try the purge/reinstallation procedure detailed above, then.

As for kdm breakage; opinion, but I'd suggest you stick with the normal kdm; it works just as well, and there doesn't seem to be any immediate benefits.

---

### Post by RJARRRPCGP on 2008-05-09
Is KDE 4x broken? 

Will all Kubuntu users that have KDE 4x get this problem?

Anyone else, please report.

---

### Post by ProbablyX on 2008-05-09
> **Zorael said:**
> You could try to rename/delete **~/.kde4** from a terminal/KDE3 session to make sure your settings aren't messing things up.

Failing that, I'd try completely removing any package containing 'kde4' in its name and then reinstalling either **kubuntu-kde4-desktop** if you want the whole package (with games and everything), or **kde4-core** if you just want the environment and basic utilities, like konsole-kde4. Graphical way would be to open up Adept Manager, search for kde4, tag everything for **purging**. It shouldn't remove anything quintessential to your kde3 setup; they're made to be separate.

Terminal way:
```
$ sudo aptitude purge ~nkde4
```

Then reinstall.
```
$ sudo aptitude install kde4-core              # skeletal installation
$ sudo aptitude install kubuntu-kde4-desktop   # whole bunch of more stuff
```

I logged into KDE3, removed the backports repo, did all that and KDE4 is still dead (KDM4 still has a gray BG, then I open a context menu and close it the "Kubuntu bg" shows for the part where the context menu was...)

UPDATE: If I do login to KDE4 (nothings changed about the above, ive reinstalled kdm etc and its BG is still grayish) and open the menu the image of it is first "wrong" and then goes "right" adding that KDM's background also is gray - but does show parts of the real BG when I open and close a context menu (it redraws the background where the context menu was) - could this be a missing gfx lib or sumt?

---

### Post by ProbablyX on 2008-05-09
never mind this post, just me missing sumt

---

### Post by ProbablyX on 2008-05-09
OK!

I fixed it all by myself, hehhe...

This if how I did it:

```

$ cd /usr/lib/kde4/etc/kde4/kdm
$ sudo mv kdmrc kdmrc.bak
$ sudo /usr/lib/kde4/bin/genkdmconf
$ cd ~
$ mv .kde4 .kde4.bak

```

As youve messed with KDE4 and different versions of it, its folder most likely wont work (didnt for me) thats why Im moving it there in the last lines.

After that restart X and it will work :)

EDIT: Added "sudo" to the needed lines

---

### Post by ProbablyX on 2008-05-10
Ok... So now when I started this morning KDE is back-to-not-working, can it be something with the session loading thats messed up?

---

### Post by takowl on 2008-05-10
I see the same grey background to the kdm login screen, but window decorations and so forth still seem to work for me.

(Kubuntu-KDE4 8.04 with KDE 4.0.4, on ATI graphics with proprietary fglrx driver)

---

### Post by Zorael on 2008-05-10
Curious. I installed [FONT="Courier New"]kde4-core[/FONT] yesterday to see if 4.04 had fixed the ugly redrawing (which it hadn't), and it worked great with the normal kdm.

You could hunt down any stray files so as to *completely* empty your system of stuff even rhyming with kde4.
```
$ sudo aptitude purge ~nkde4
$ rm -r ~/.kde4
$ sudo updatedb -u
$ locate *kde4*
*<commence witch-hunt>*
```

---

### Post by ProbablyX on 2008-05-10
OK so now when I open KDE it's factory-reset, not to Kubuntu but to KDE settings like Konqueror asks me if I want to save cookiess or reject them and I have four desktops, so that's good I suppose.

However I still have a graphics flaw when I open my K-menu, that is its first "scattered" and then renders. Also, apps says they are version 4.0.3. Except for that I *think* it's working, haven't tried to relogin yet.

But should the applications, like Konqueror think they're under 4.0.3 or is this a package mess-up (I ran aptitude clean and autoclean before install)

---

### Post by Zorael on 2008-05-10
I've been getting the rendering issues (garbled graphics when kmenu/desktop rightclick popup/etc is drawn for the first time) since 4.0.1, I guess it's a Qt issue, and I'd hoped they'd fixed it by now. Alas.

---

### Post by ProbablyX on 2008-05-10
OK so I logged out, and in again and now KDE is back to it's non-working state (I also noticed the four desktops have gone to a single one) =/

---

### Post by cleb on 2008-05-14
I have almost exactly the same problem after updating to 4.0.4 (grey kdm background), but my KDE4 starts. The panel is a little messed up, but the strangest thing about it is, that all KDE programs claim (in help->about kde) that I am running KDE 4.0.3. Adept manager however says that I have 4.0.4. Could this be the problem? Is it possible, that the update did not finnish properly and that we now all have an ugly mix of different KDE4 versions? That would explain the problems.

---

### Post by evel_keneevel on 2008-05-15
i'm having the same problem, the output of dpkg for a package is```
dpkg -s kdelibs5
Package: kdelibs5
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 22364
Maintainer: Kubuntu Developers <kubuntu-devel@ubuntu.com>
Architecture: i386
Source: kde4libs
Version: 4:4.0.4-0ubuntu1~hardy1 ......
```ok so far, and then kde4-config gives : ```
$ kde4-config --version
Qt: 4.4.0
KDE: 4.0.3 (KDE 4.0.3)
kde4-config: 1.0
```Why is that?? did i miss a package or something? I removed & reinstalled the related kde4 packages twice, but still, no dice
I use these repositories
```
deb http://archive.ubuntu.com/ubuntu hardy main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu hardy-updates main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu hardy-security main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu hardy-proposed main multiverse restricted universe

deb http://archive.ubuntu.com/ubuntu hardy-backports main multiverse restricted universe
```Actually, i couldn't wait to try kde4 so i did a clean install, installing the KDE 4.0.0 version of gutsy when it came out 5 months ago, and now i upgraded to Hardy using the repositories... maybe a clean install with a Hardy-kde4 version wouldn't have these problems, or am i wrong??

---

### Post by cleb on 2008-05-15
What if the two problems (the version info and the rendering problems) are each caused by something else? The version info may be wrong just because someone forgot to change it to 4.0.4 before building the .deb package.
The rendering problems could be caused by QT 4.4, which installed at about the same time. This version kde is linked against QT 4.3, maybe it is not fully backwards compatible. Is there a way to "downgrade" back to QT 4.3?

---

### Post by rexstuff on 2008-05-15
I, too, have been having this problem.

Behold! An ugly ugly workaround!

ln -s /usr/lib/kde4/bin/kwin ~/.kde4/Autostart/kwin

This causes kwin to be manually loaded -after- everything else has been loaded. Suffice to say, the desktop is completely unusable until that point. Furthermore, the pager never seems to remember your desktop configuration, and will need to be told (through right-clicking) that you want, say, a 2x2 layout.

I wonder if the problem has something to do with hardware acceleration. First time I encountered this problem, I had already installed the restricted drivers, then upgraded to 4.0.4. After this problem, I reinstalled Kubuntu, then installed 4.0.4, and everything seemed to be working (granted, I didn't give it a full workout). Then, I installed the proprietary nvidia drivers, nvidia-glx-new, and boom, back to square one.

Anyone else find that graphics drivers are related? What sort of card do you have? (I have an 8600M GT in my new Macbook Pro)

A proper fix to this problem would be greatly appreciated (hint hint). Anyone?

---

### Post by evel_keneevel on 2008-05-15
Well, i don't think the version of kde that i get ( 4.0.3 that is, instead of 4.0.4 ) is because someone forgot to change something when he was building the .deb package. I'm no expert, but i guess that doing something like that means tweaking the source files from which you build the .deb package, and i don't think that's what happened here. As for the drivers, no, I'm not having any issues recently or in the past. I installed drivers for my Geforce 6150 laptop card using the Nvidia installer, downloaded from their website. But, yesterday i did get a weird behaviour for the first time: 1 or 2 days after installing the latest kde4.0.4 packages, and for no apparent reason, X server didn't start, and i had to login using the failsafe option, from the kde4 login screen. When i did that, i got a message like "blah blah ... check that dcopserver is running". I guess I'll blame KDE for that one too!

---

### Post by malachias on 2008-05-15
I have the same issue, although mine came up in a slightly different way:
after some update, aptitude insisted that kwin was no longer needed and would be removed. Fine, I said, and everything still worked fine. After yet another update, everything broke as people have been describing. I reinstalled kwin, and found that I could "fix" things by running kwin on login as others have

I've been searching through config file after config file and script after script... nothing =\

---

### Post by phyjcowl on 2008-05-17
I've been having the exact same problems. I tried an experiment where I created a new user, logged on as that user to see if I could find some difference between my existing settings and the new user's settings. 

The new user worked fine (with the kwin starting normally). As soon as I enabled the desktop effects for the new user all the borderless window problems, single desktop problems, slow app start problems, etc. began again. So I went back to my old user account, disabled desktop effects, and it works perfectly fine now. 

Of course, this isn't a solution because it means I do not have the nice KDE4 desktop effects that worked on the previous versions. It also doesn't solve the issue with the grey background at the KDM login screen. But it makes me think maybe Rexstuff's comment about the video drivers is heading in the right direction.

---

### Post by phyjcowl on 2008-05-17
Ok, seems I was mistaken in my previous post and disabling desktop effects didn't make any difference. However, whether the effects are turned on or not, when I go to System Settings > Advanced > Session Manager and then change the On Login section to say "Start with an empty session" everything does work fine for me--even with desktop effects turned on. I guess this still isn't a fix because now it won't remember what I had going on in my previous session but at least I don't have run kwin --replace or the other fixes.

---

### Post by malachias on 2008-05-17
I just booted up about 3 minutes ago and everything worked... o_O I have no idea why. I am glad it works, but I do hate it when things fix themselves with no updates or anything. It makes me feel terribly odd.

---

### Post by Starlight on 2008-05-17
I have the same problem after the upgrade... kdm has a very strange flickering gray background, kde4 loads without kwin so I need to run it using Alt+F2, and about boxes say that I still have kde 4.0.3... I hope they fix it soon :)

---

### Post by ProbablyX on 2008-05-18
Lol, I switched back to KDE3 after my last post. Works fine for me, there was a KDE4 (or partial) upgrade of Kopete and a few other packs, and Qt today.
However 1st login (after rm -rf ~./kde) worked fine, then I got one-desktop issues etc =/

Please post here when it works again LOL! 
I have a friend who uses Debian though, who's installed KDE 4.1 alpha, he says it's way more stable than 4.0 - and much better feature-wise etc.
Is it possible to install 4.1 alpha in Kubuntu I ask?

---

### Post by Mr. Swiveller on 2008-05-19
> **phyjcowl said:**
> Ok, seems I was mistaken in my previous post and disabling desktop effects didn't make any difference. However, whether the effects are turned on or not, when I go to System Settings > Advanced > Session Manager and then change the On Login section to say "Start with an empty session" everything does work fine for me--even with desktop effects turned on. I guess this still isn't a fix because now it won't remember what I had going on in my previous session but at least I don't have run kwin --replace or the other fixes.

I can confirm that this works. KDE 4.04 now runs faster on my system than did 4.03.

* Swiveller *

---

### Post by kgeekworking on 2008-05-20
I have the same issue.

For me kwin is inconsistent.  Without making any changes at all and kwin will run about 50% of the time.  People posting that they *fixed* the issue only to post again that it is not fixed appears to echo what I am seeing.  

I just changed the session manager setting to start with a clean session.  I have gone through 10 power off cold boots and kwin has come up every time.  I am hesitant to declare it as fixed, but it is good so far.

---

### Post by Zorael on 2008-05-21
Does anyone experience graphical corruption upon first drawing windows with the proprietary nvidia driver, or is it just me? Like, pop up the new kmenu first time after login.

---

### Post by Mr. Swiveller on 2008-05-22
> **Zorael said:**
> Does anyone experience graphical corruption upon first drawing windows with the proprietary nvidia driver, or is it just me? Like, pop up the new kmenu first time after login.

This happens with the ATI proprietary drivers too. It appears to be a QT4 problem; may have been fixed in the new version which they used for KDE 4.1 (alpha).

* Swiveller *

---

### Post by aos101 on 2008-06-17
> **Mr. Swiveller said:**
> This happens with the ATI proprietary drivers too. It appears to be a QT4 problem; may have been fixed in the new version which they used for KDE 4.1 (alpha).

* Swiveller *
I had this problem with 4.03 (that came with Hardy), and it's still there with the 4.1 Beta 1 packages for Kubuntu.  I'm running the nvidia proprietary driver, so it sounds like it's not just an nvidia specific issue.

---

### Post by ProbablyX on 2008-06-17
The solution for me was to switch to KDE 4.1 beta (installation procedure can be found on kubuntu's homepage). 
KDE 4.1 still has issues but they are very VERY milder than KDE 4.0...

---

