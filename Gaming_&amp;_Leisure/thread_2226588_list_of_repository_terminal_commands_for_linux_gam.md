---
title: "list of repository terminal commands for linux game emulators?"
date: 2014-05-28
forum: Gaming &amp; Leisure
---

### Post by freewarelover on 2014-05-28
**Sorry I solved issue during creation of this thread it was due to mis-spelling of terminal command. But I have another question anyway**  Is there a list anywhere of repository terminal commands for all linux video game emulators? (As well as having commands for there repositories and themselves) (e.g. I can't seem to get the repository for visualboyadvance despite I thread I found from here on it because none of the exact repositories work. I'd post the link but can't seem to paste.

Thanks.

---

### Post by m_duck on 2014-05-28
The command you are probably after is **apt-cache search**. E.g. to find the visual boy advance package:```
$ apt-cache search visual boy advance
```This will give an output of something like:```
user@ubuntu:~$ apt-cache search visual boy advance
vbaexpress - Front-End for VisualBoyAdvance
visualboyadvance - full featured Game Boy Advance emulator
visualboyadvance-gtk - GTK+ front-end to VisualBoyAdvance emulator
```
It shows a list of packages and a short decription. You could then install it with a GTK GUI using (visualboyadvance is a dependency of visualboyadvance-gtk so it will be installed as well):```
sudo apt-get install visualboyadvance-gtk
```
You can also use [packages.ubuntu.com]("http://packages.ubuntu.com") to browse for packages and see their dependencies etc.

To get dependency etc. information on the command line, use **apt-cache show**:```
user@ubuntu:~$ apt-cache info visualboyadvance-gtk
E: Invalid operation info
user@ubuntu:~$ man apt-cache
user@ubuntu:~$ apt-cache show visualboyadvance-gtk
Package: visualboyadvance-gtk
Priority: extra
Section: universe/games
Installed-Size: 1355
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Games Team <pkg-games-devel@lists.alioth.debian.org>
Architecture: amd64
Source: visualboyadvance
Version: 1.8.0.dfsg-2
Depends: **visualboyadvance **(= 1.8.0.dfsg-2), libatkmm-1.6-1 (>= 2.22.1), libc6 (>= 2.14), libgcc1 (>= 1:4.1.1), libglademm-2.4-1c2a (>= 2.6.0), libglib2.0-0 (>= 2.16.0), libglibmm-2.4-1c2a (>= 2.33.13), libgtk2.0-0 (>= 2.8.0), libgtkmm-2.4-1c2a (>= 1:2.24.0), libpng12-0 (>= 1.2.13-4), libsdl1.2debian (>= 1.2.11), libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6 (>= 4.6), zlib1g (>= 1:1.1.4)
Filename: pool/universe/v/visualboyadvance/visualboyadvance-gtk_1.8.0.dfsg-2_amd64.deb
Size: 493254
MD5sum: 4d1516110723583de89a561830ae3d68
SHA1: b7ded67c785a4f46add8998ba2da321acb6c59d9
SHA256: eb439274d4d2554be2a7a8083e42e817f95d0cd3359febbbd4305d53062e8b55
Description-en: GTK+ front-end to VisualBoyAdvance emulator
 VisualBoyAdvance is a Game Boy Advance emulator that works with
 many ROMs that are publically available. It features save states
 (like those that are available in ZSNES), full screen support,
 joystick support, the all-important 'speedup emulation' key for
 impatient gamers, and a lot more.
 .
 It also contains many useful tools for Game Boy Advance developers,
 such as powerful GDB and gprof integration.
 .
 This package contains a version of VisualBoyAdvance with GTK+ support.
Description-md5: 28ed7c00adf7420c1e3f3412d973486a
Homepage: http://sourceforge.net/projects/vba
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

For other emulators, use the above **apt-cache search**.
```
user@ubuntu:~$ apt-cache search playstation emulator
libupse-dev - unix playstation sound emulator - library development files
libupse2 - unix playstation sound emulator - library
**pcsxr - Sony PlayStation emulator**
pcsxr-dbg - Sony PlayStation emulator (debug)
upse123 - commandline player based on libupse
```

---

### Post by freewarelover on 2014-05-28
Thanks it worked for visual boy advance but doesn't work for things where the repository isn't already there. Is there a repository version of that command? Btw cool avatar.

---

### Post by Bucky Ball on 2014-05-28
Hi. I have changed the name of your thread to reflect your question.

In future, better to mark the thread as solved and start a new thread with a descriptive title. You have little chance of getting help posting a support issue which has absolutely nothing whatsoever to do with the title of the thread. Help us help you.

Good luck. ;)

---

### Post by deadflowr on 2014-05-28
>  I can't seem to get the repository for visualboyadvance despite I  thread I found from here on it because none of the exact repositories  work.

I don't know what this means, but most of your game emulators will be in one repository.
That would be the universe repository.
Emulators which aren't included within the Ubuntu repo system would either need their repos added, or the emulators debian installation file downloaded and installed from.

But something like visualboyadvanced has been in the universe repo for years, so if you can't find it, then either you have spelled it wrong, or you need to enable that repo. Or make sure it is enabled.
Just my thought.

---

### Post by freewarelover on 2014-05-29
> **Bucky Ball said:**
> Hi. I have changed the name of your thread to reflect your question.

In future, better to mark the thread as solved and start a new thread with a descriptive title. You have little chance of getting help posting a support issue which has absolutely nothing whatsoever to do with the title of the thread. Help us help you.

Good luck. ;)
Ok sorry I thought it be better because I thought if I did that you'd mad a me for flooding the forum.

---

### Post by freewarelover on 2014-05-29
> **deadflowr said:**
> I don't know what this means, but most of your game emulators will be in one repository.

Really? Dolphin seemed to have it's own repository called glennric. ```
 ppa:glennric/dolphin-emu
``` is what I had to type to get it loaded. Is the universe repository fully preloaded because I was able to get visualboyadvance loaded but don't remember ever having to load that repository.

---

### Post by m_duck on 2014-05-29
The most popular and well-known emulators will be in the universe repository which is one of the standard Ubuntu repos. When packages aren't available, other repositories can be set up to add more packages (or alternatively, you could just install the package from a .deb file, but it won't be automatically updated). The one you mention is just one containing the Dolphin emulator. Adding repositories is great because it gives you easy access to extra packages and updates (if the repository owner keeps it up to date), but be careful which repositories you add.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by deadflowr on 2014-05-29
> **freewarelover said:**
> Really? Dolphin seemed to have it's own repository called glennric. ```
 ppa:glennric/dolphin-emu
``` is what I had to type to get it loaded. Is the universe repository fully preloaded because I was able to get visualboyadvance loaded but don't remember ever having to load that repository.

I stated already that emulators NOT included within the Ubuntu repo system would need to have their own repos added.
I don't know what preloaded means. But the repos are nothing more than archives, from which you download packages.
And typically, you should have it(universe) enabled by default, without the need to manually enable it.
If any of that makes sense.

---

### Post by freewarelover on 2014-06-01
> **m_duck said:**
> The most popular and well-known emulators will be in the universe repository which is one of the standard Ubuntu repos. When packages aren't available, other repositories can be set up to add more packages (or alternatively, you could just install the package from a .deb file, but it won't be automatically updated). The one you mention is just one containing the Dolphin emulator. Adding repositories is great because it gives you easy access to extra packages and updates (if the repository owner keeps it up to date), but be careful which repositories you add.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Hmm I'm surprised that Dolphin isn't considered a very popular emulator. Also why would I have to be careful about whatr repos I add? (the more the merrier no?_

> **deadflowr said:**
> I stated already that emulators NOT included within the Ubuntu repo system would need to have their own repos added.
I don't know what preloaded means. But the repos are nothing more than archives, from which you download packages.
And typically, you should have it(universe) enabled by default, without the need to manually enable it.
If any of that makes sense.
Preloaded means it was installed upon installation of the OS. Again though, I'm asking what the equivalent of ```
sudo apt-cache search
``` for repositories. In other words, ```
sudo apt-cache search
``` is to programs as what is to repositories?

---

### Post by Bucky Ball on 2014-06-01
> **freewarelover said:**
> Hmm I'm surprised that Dolphin isn't considered a very popular emulator. Also why would I have to be careful about whatr repos I add? (the more the merrier no?_

From Launchpad:
> 
Important: The contents of Personal Package Archives are not checked or monitored. You install software from them at your own risk. 

PPAs are open-source but third-party, i.e. not checked or approved by Ubuntu/Canonical (and therefore not in the main repositories, although some of the apps in a PPA might be!). The contents in a PPA can be at various stages of development and not always stable versions. You may inadvertantly update to a version of a package that causes issues. 

Finally, PPAs can cause problems at your end if there's a problem with the PPA itself or the server(s) it lives on. If you start having odd problems updating, like a Launchpad error where the PPA is not found, or being prevented from updating, disable the PPAs you've added and try again.

---

### Post by freewarelover on 2014-06-01
Oh ok I never knew that rep are deved by third-parties since repos are something that's a linux thing, I thought (even if it was remotely that) linux coders made them. That explains why there's no repo equivalent to ```
sudo apt-add-repository ppa:something
```

---

