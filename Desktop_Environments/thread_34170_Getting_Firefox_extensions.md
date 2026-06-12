---
title: "Getting Firefox extensions"
date: 2005-05-13
forum: Desktop Environments
---

### Post by snaga on 2005-05-13
I just installed Hoary on a new system. I wanted to get adblock into Firefox. I clicked on 'Get Extensions' in the extensions window. I was met with a page telling me that I must upgrade to version 1.04 before I can get extensions. This seems like a new addition to the firefox site.

Is there somewhere else I can go?

dm

---

### Post by fluideye on 2005-05-13
That extension may only work with Firefox 1.04.  That's the first thing I would check out.

---

### Post by NeoChaosX on 2005-05-13
fluideye: No. Adblock is a pretty popular extension, it wouldn't only work on the latest version. The extension installation problem is something I've had for awhile, too - for some reason, the copy of Firefox installed with Ubuntu won't let you install extensions at all, even from Mozilla's own sites at least from my experience. I've found that upgrading Firefox, either through Ubuntu Backports, or installing a version from mozilla.org over the current install, will get extension installation working.

---

### Post by not_yet on 2005-05-13
you should update to Firefox 1.04 as this is a maintenance release to take care of  a possible vulnerability

---

### Post by banjobacon on 2005-05-13
[http://www.extensionsmirror.nl/](http://www.extensionsmirror.nl/)
[http://extensionroom.mozdev.org/](http://extensionroom.mozdev.org/)

---

### Post by Burgundavia on 2005-05-13
The fix for this is incoming, from the official repos.

Corey

---

### Post by jodef on 2005-05-13
1.04 is to fix a critical security flaw in Firefox 1.03 I guess Mozilla was trying to ensure everyone upgrades.

---

### Post by ubuntu_demon on 2005-05-14
just wait for the official repo's .. they will "backport" any security fixes from 1.0.4 into 1.0.2

If you need 1.0.4 for the features you can wait untill jdong has stabalized the backport.

---

### Post by schneiko on 2005-05-15
I had this problem, too. Fixing the Firefox 1.0.2 would probably still forbid the user to enter the Mozilla Extensions page, because the Mozilla website checks, if the latest Firefox (today 1.0.4) is beeing used. If not - no access to the download area.

Fixing Firefox 1.0.2 is important, but it is also important for a user who is new to Linux, to be able to use Firefox with all the extensions available.

---

### Post by banjobacon on 2005-05-15
[QUOTE=demon666_nl]just wait for the official repo's .. they will "backport" any security fixes from 1.0.4 into 1.0.2.[/QUOTE]

But unfortunately, the browser still identifies itself as 1.0, so access to the extensions site is not granted. Sure, you can change the UA string manually to bypass the Firefox update page, but that doesn't seem like the proper way to do it.

---

### Post by ubuntu_demon on 2005-05-16
[QUOTE=banjobacon]But unfortunately, the browser still identifies itself as 1.0, so access to the extensions site is not granted. Sure, you can change the UA string manually to bypass the Firefox update page, but that doesn't seem like the proper way to do it.[/QUOTE]
 here's the solution :

[http://www.ubuntuforums.org/showpost.php?p=172105&postcount=30](http://www.ubuntuforums.org/showpost.php?p=172105&postcount=30)

---

### Post by Crad on 2005-05-16
What's the issue with updating the repository with the current version of Firefox?  I'd like to be running 1.0.4 myself.

---

### Post by snaga on 2005-05-16
[QUOTE=demon666_nl]here's the solution :

[http://www.ubuntuforums.org/showpost.php?p=172105&postcount=30](http://www.ubuntuforums.org/showpost.php?p=172105&postcount=30)[/QUOTE]


Well, this works. I would prefer to use 1.0.4, but I will wait until an official ubuntu version comes out.

---

### Post by jodef on 2005-05-16
[QUOTE=snaga]Well, this works. I would prefer to use 1.0.4, but I will wait until an official ubuntu version comes out.[/QUOTE]As far as I understand the development process and please correct me if am wrong, they're going to incorporate the security fixes into Firefox 1.02 no new version of apps are introduced into official repos just security fixes. You can get the [Firefox 1.04 Backport](http://www.ubuntuforums.org/showthread.php?t=34099)

---

### Post by stevenyu on 2005-05-21
I have already updated my Firefox to the latest 1.04 through apt-get upgrade with Ubuntu Backport, but when I try to get extension from [www.mozilla.org](www.mozilla.org) I still getting the same error message regarding to upgrade to 1.04, anyone got any ideas? :-?

---

### Post by lorap on 2005-05-22
hi friend!
let's work it out.
first of all it'd be great for you to upgrade firefox but there're some important things.
it'd be better if you make it with me.
so don't open the file with file-roller but just save it on the desktop.
now that you've the file saved on the desktop do the next.
place the mice over the file, press the right button and choose the option "extract here". after you have the file extracted delete the compressed file. double click on the just created directory. there would be inside it another directory. place the mice over that directory and press right button choosing "cut" option. then "paste" this directory on the desktop. after this the first directory became an empty. delete it also :-) now when you open the directory you just have pasted on the desktop you'll see the file "install script" or something like this, but it should be installation script.
open terminal window and write next :

sudo sh

after what place the mice over the install script press the small button and just grab it to the terminal. remember there should be an empty place between "sh" and "install script". then press enter.
after the installation process's begun you'll be prompted to choose the installation directory!
CHOOSE THE "CUSTOM" OPTION!
NOW WRITE THIS:

/usr/lib/mozilla-firefox

(IF YOU LOOK INSIDE THE /USR/LIB YOU'LL SEE HOW TO WRITE IT IN THE PROPER WAY I'M NOT AT MY PC SO YOU'LL NEED TO CHECK IT YOURSELF, BUT REMEMBER YOU'RE GONNA OVERRITE THAT DIRECTORY!!!!!!!!!!!!!!!!!!!!!!!!!!!!)
so check it (mozilla-firefox or firefox-mozilla)

then you'll be asked to delete the old directory or not, choose to delete.
that'd completely overrite your old firefox.
now you can enjoy it!
for additional questions:

[email]prianfamily@gmail.com[/email]

pavel

---

### Post by angrykeyboarder on 2005-05-22
[QUOTE=jodef]As far as I understand the development process and please correct me if am wrong, they're going to incorporate the security fixes into Firefox 1.02 no new version of apps are introduced into official repos just security fixes. You can get the [Firefox 1.04 Backport]("http://www.ubuntuforums.org/showthread.php?t=34099")[/QUOTE]

Or you could dump Ubuntu and switch to Fedora Core. They released their Firefox 1.04 package on 16 May....

http://download.fedora.redhat.com/pub/fedora/linux/core/updates/3/i386/firefox-1.0.4-1.3.1.i386.rpm

My point being, Fedora, like Ubuntu, only does security updates of it's packages between releases. The difference is, Fedora has the common sense to release a new package to reflect the security update.  Therefore the version number changes like it's supposed to....

I can't imagine why Ubuntu makes this more difficult than it has to.

Oh well, at least Ubuntu repositories have more packages than Fedora does (offical I'm talking here).

---

### Post by angrykeyboarder on 2005-05-22
[QUOTE=snaga]Well, this works. I would prefer to use 1.0.4, but I will wait until an official ubuntu version comes out.[/QUOTE]

Do like I did, download the ```
mozilla-firefox_1.0.4~5.04ubp1+1.0.2-0ubuntu1_i386.deb
``` package from Ubuntu Backports. It is truly v1.04 however......

you'll need to change the string as mentioned in that bugzilla post since Backports is following Ubuntu convention and not "officially" changing the version number.....

At least you have a safe, bug-free, working and current version.  I do anyway (that is, till Mozilla discovers another bug...).

---

### Post by nuopus on 2005-05-22
[QUOTE=Crad]What's the issue with updating the repository with the current version of Firefox? I'd like to be running 1.0.4 myself.[/QUOTE]

This is a crap policy set forth in the Debian world. Even if 1.0.3 or 1.0.4 has been tested to be the most secure thing on the planet and can even create its own bomb shelter in case of nuclear attack .... they will still not upgrade to it until breezy.

If it were not for Ubuntu Hoary backports I would still be with ArchLinux as they do not have such an anal policy. Dont get me wrong, Ubuntu is still a great distro ... its Debian politics that should be put to rest.

At any rate, go to the [Ubuntu Backports]("http://backports.ubuntuforums.org/") project to get started. May as well because FireFox 1.1 is coming soon ... before the next Breezy release probably, and one of the fixes are in the rendering code that fixes lots of web pages that do not load inline. Things like this will not be "backported" to 1.02 ... just the security fixes. So if you like new "features" in recently released software ... go with the backports project.

Yes yes there are people that hate the backports and will flame me for suggesting it, but for some reason these are people who tend to hate going to new software. This is why Debian itself is dying .... I just hope Ubuntu doesnt get farther and farthe behind because the wanted policies of a few morons dictate the development of this fine distro.

---

### Post by auburn on 2005-05-22
I ran into the same problems getting my extensions, but I just went to [http://extensionsmirror.nl](http://extensionsmirror.nl) and [http://extensionroom.mozdev.org](http://extensionroom.mozdev.org) to get them. Extensionsmirror.nl is the mac-daddy of repositories anyway. (I suggest you visit, it's awesome.)

---

### Post by nuopus on 2005-05-22
[QUOTE=auburn]I ran into the same problems getting my extensions, but I just went to [http://extensionsmirror.nl]("http://extensionsmirror.nl") and [http://extensionroom.mozdev.org]("http://extensionroom.mozdev.org") to get them. Extensionsmirror.nl is the mac-daddy of repositories anyway. (I suggest you visit, it's awesome.)[/QUOTE]

The fact that we have to resort to going elsewhere JUST BECAUSE policy dictates upgrades should not happen is cheap. Use the backports.

---

### Post by auburn on 2005-05-29
I just uninstalled the backported 1.0.4 and reinstalled ubuntu's stock 1.0.2. I was getting crashes whenver I hit the purchase item button on the newegg site. I tried using a default profile without improvement. The 1.02 works.

---

### Post by angrykeyboarder on 2005-05-29
[QUOTE=Burgundavia]The fix for this is incoming, from the official repos.

Corey[/QUOTE]

I wonder what they are waiting for........

---

### Post by jarrett.wold on 2005-05-31
Step 1: Launch Firefox 1.0.4
Step 2: type in about:config in the address bar
Step 3: set general.useragent.vendorSub to 1.0.4

Redundant I know, but some *I predict*, will not go to comment 3 in the bug report linked off of this forum, and the splash page that is brought up in Firefox.

---

