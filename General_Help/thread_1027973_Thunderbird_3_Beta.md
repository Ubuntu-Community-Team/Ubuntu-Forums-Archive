---
title: "Thunderbird 3 Beta"
date: 2009-01-01
forum: General Help
---

### Post by Dgurion on 2009-01-01
I was wondering how I would install the Thunderbird 3 Beta.. Is there a .deb file I can get? Any help would be appreciated..

---

### Post by caro on 2009-01-01
double post :redface:

---

### Post by caro on 2009-01-01
Check out this link:  [http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/")  This will let you keep FF and Thunderbird updated if they release a version update after the most recent version of Ubuntu is released.  It may be able to be used with the beta versions too but I haven't tried.

---

### Post by Loosewheel on 2009-01-01
Here is a link to the Ubuntu documentation for installing software.
[https://help.ubuntu.com/8.04/add-applications/C/install-file.html#tarballs](https://help.ubuntu.com/8.04/add-applications/C/install-file.html#tarballs)

---

### Post by nanotube on 2009-01-02
> **caro said:**
> Check out this link:  [http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/")  This will let you keep FF and Thunderbird updated if they release a version update after the most recent version of Ubuntu is released.  It may be able to be used with the beta versions too but I haven't tried.

hi, ubuntuzilla only works with official releases, not with betas.

---

### Post by Loosewheel on 2009-01-02
> **Dgurion said:**
> I was wondering how I would install the Thunderbird 3 Beta.. Is there a .deb file I can get? Any help would be appreciated..

Dgurion, did you get this resolved?
I downloaded the .tar.bz2, extracted it in my home folder on an older machine running PCLinuxOS, (didn't want to mess up my main Ubuntu system), typed 'cd thunderbird' and './thunderbird' in a console...and it came up.

---

### Post by OrelEagle on 2009-02-25
Hi,

I wrote a how-to last week-end for testing Thunderbird 3 in the tips section, but it seems it's still blocked in the moderation process... As I don't know how long it will take, I'm posting it here:

-----------------------------------------------------------------------
Hello,

After reading [a thread in the French Ubuntu forum]("http://forum.ubuntu-fr.org/viewtopic.php?id=238976"), I decided to try the new features brought by Thunderbird 3. And since I find it really cool, I'd like to share how to install it (in parallel with Thunderbird 2) and contribute to the tests. This tutorial will be divided into 3 parts:

[LIST]
[*]Part I: install process
[*]Part II: Create a new profile
[*]Part III: Contribute to the tests
[/LIST]

Please remember that Thunderbird 3 is still in beta version and could (although very unlikely) harm your data (emails, contacts). For this reason I strongly recommend to use non critical email accounts and create a specific profile for this purpose (read part II for more information).

**Part I: install process**

The install process is very simple:
[LIST=1]
[*]Download the file
[*]Extract the archive
[*]Move the thunderbird folder to /opt
[*]Create a link to run it easily
[/LIST]

1. Download the file

You can download the most recent public release from Thunderbird's website:
[http://www.mozillamessaging.com/en-US/thunderbird/early_releases/](http://www.mozillamessaging.com/en-US/thunderbird/early_releases/)

2. Extract the archive

Go to the folder where you downloaded the file (should be a .tar.bz2) and extract it (right click -> extract here). Alternatively, you can also use the tar command.

3. Move the thunderbird folder to /opt

You will need sudo rights to move the file to /opt. You can either start Nautilus in root mode and move the folder graphically or use this command, assuming you are working in the folder where you extracted the archive.

```
sudo mv thunderbird /opt
```4. Create a link to run it easily

You will create a link to the executable and put it in /usr/bin, this way you simply have to use this link to run the testing version, for example using the "run application" dialog (Alt+F2). I called it "thunderbird3" to make it clear.

```
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird3
```**Part II: Create a new profile**

Now that you have installed Thunderbird 3, you don't want it to mess up with your data. For this you will create a new profile. Simply start Thunderbird 3 with the profile manager:

```
thunderbird3 -P
```In this dialog bow, click on "Create Profile...". Follow the instructions from the wizards and chose a name for this profile. Let's call it testProfile. Now you can select testProfile in the profile manager and start testing! When you want to use your normal profile, simply start the profile manager again and select it in the list.

**Part III: Contribute to the tests**

To make Thunderbird a high quality application, the mozilla team needs your help! The first thing to do is to subscribe to the [Thunderbird-testers]("https://mail.mozilla.org/listinfo/thunderbird-testers") mailing list. You will then receive instructions about how to test the new features of Thunderbird.

I also recommend to read the wiki page about how you can help.[https://wiki.mozilla.org/Thunderbird:Testing](https://wiki.mozilla.org/Thunderbird:Testing)

Edit: the how-to has been accepted: [http://ubuntuforums.org/showthread.php?t=1076624](http://ubuntuforums.org/showthread.php?t=1076624)

---

### Post by ben2talk on 2009-11-12
> **Dgurion said:**
> I was wondering how I would install the Thunderbird 3 Beta.. Is there a .deb file I can get? Any help would be appreciated..

You should add the repo for Ubuntu Mozilla Daily PPA
You can then install 'Shredder' (Thunderbird-3.0) and will also see Firefox 3.5,3.6 and 3.7 previews.

They're lovely ;)

---

### Post by sonofzell on 2010-01-29
> **OrelEagle said:**
> Hi,

I wrote a how-to last week-end for testing Thunderbird 3 in the tips section, but it seems it's still blocked in the moderation process... As I don't know how long it will take, I'm posting it here:

-----------------------------------------------------------------------
Hello,

After reading [a thread in the French Ubuntu forum]("http://forum.ubuntu-fr.org/viewtopic.php?id=238976"), I decided to try the new features brought by Thunderbird 3. And since I find it really cool, I'd like to share how to install it (in parallel with Thunderbird 2) and contribute to the tests. This tutorial will be divided into 3 parts:

[LIST]
[*]Part I: install process
[*]Part II: Create a new profile
[*]Part III: Contribute to the tests
[/LIST]

Please remember that Thunderbird 3 is still in beta version and could (although very unlikely) harm your data (emails, contacts). For this reason I strongly recommend to use non critical email accounts and create a specific profile for this purpose (read part II for more information).

**Part I: install process**

The install process is very simple:
[LIST=1]
[*]Download the file
[*]Extract the archive
[*]Move the thunderbird folder to /opt
[*]Create a link to run it easily
[/LIST]

1. Download the file

You can download the most recent public release from Thunderbird's website:
[http://www.mozillamessaging.com/en-US/thunderbird/early_releases/](http://www.mozillamessaging.com/en-US/thunderbird/early_releases/)

2. Extract the archive

Go to the folder where you downloaded the file (should be a .tar.bz2) and extract it (right click -> extract here). Alternatively, you can also use the tar command.

3. Move the thunderbird folder to /opt

You will need sudo rights to move the file to /opt. You can either start Nautilus in root mode and move the folder graphically or use this command, assuming you are working in the folder where you extracted the archive.

```
sudo mv thunderbird /opt
```4. Create a link to run it easily

You will create a link to the executable and put it in /usr/bin, this way you simply have to use this link to run the testing version, for example using the "run application" dialog (Alt+F2). I called it "thunderbird3" to make it clear.

```
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird3
```**Part II: Create a new profile**

Now that you have installed Thunderbird 3, you don't want it to mess up with your data. For this you will create a new profile. Simply start Thunderbird 3 with the profile manager:

```
thunderbird3 -P
```In this dialog bow, click on "Create Profile...". Follow the instructions from the wizards and chose a name for this profile. Let's call it testProfile. Now you can select testProfile in the profile manager and start testing! When you want to use your normal profile, simply start the profile manager again and select it in the list.

**Part III: Contribute to the tests**

To make Thunderbird a high quality application, the mozilla team needs your help! The first thing to do is to subscribe to the [Thunderbird-testers]("https://mail.mozilla.org/listinfo/thunderbird-testers") mailing list. You will then receive instructions about how to test the new features of Thunderbird.

I also recommend to read the wiki page about how you can help.[https://wiki.mozilla.org/Thunderbird:Testing](https://wiki.mozilla.org/Thunderbird:Testing)

Edit: the how-to has been accepted: [http://ubuntuforums.org/showthread.php?t=1076624](http://ubuntuforums.org/showthread.php?t=1076624)

_@ OrelEagle_

Brilliant tutorial!  Very helpful for an enthusiastic newbie like myself!!!

---

