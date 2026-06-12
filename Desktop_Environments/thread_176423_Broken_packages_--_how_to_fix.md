---
title: "Broken packages -- how to fix?"
date: 2006-05-14
forum: Desktop Environments
---

### Post by nismoskys on 2006-05-14
I screwed up. i was trying to install bmpx from the deb for breezy on their website and so i installed a bunch of dependancies but i got dependancy hell so i  said forget it so then i removed some of the things i installed but im left with these 3 broken packages and i dont know how to fix them. i cant remove them because then it tries to remove a bunchh of other apps with it. :confused: 

check out the attatched screenshot..


also if anyone knows how to get bmpx for breezy, that'd be nice too.

---

### Post by nismoskys on 2006-05-14
sudo apt-get install -f gives me this..

```
jaanisar@jaanisar:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  beep-media-player-dev build-essential g++-3.4 j2re1.4 j2re1.4-mozilla-plugin
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libaa1-dev libartsc0-dev libasound2-dev
  libatk1.0-dev libaudiofile-dev libc6-dev libc6-i686 libcairo2-dev
  libesd0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgd2-dev
  libgd2-xpm-dev libgl1-mesa-dev libglib1.2-dev libglib2.0-dev
  libglu1-mesa-dev libgtk1.2-dev libgtk2.0-dev libjpeg62-dev libmng-dev
  libncurses5-dev libpango1.0-dev libpng12-dev libqt3-mt-dev
  libsdl-image1.2-dev libsdl1.2-dev libslang2-dev libstdc++6-dev libtiff4-dev
  libtool libxft-dev locales qt3-apps-dev ubuntu-minimal ubuntucenter
  xlibs-dev xlibs-static-dev zlib1g-dev
0 upgraded, 0 newly installed, 49 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 172MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by nismoskys on 2006-05-14
also, trying to install anything through synaptic tells me that its going to remove all the above mentioned packages before it can install. .. i dont know too much but i think i know enough to know that removing those packages will really mess up my system.

please help.

---

### Post by catlett on 2006-05-14
Something similar happened to me and it wanted to remove the ubuntu-desktop. I didn't want to but nothing would go through until I resolved the dependency issue. I went ahead because I figured I could reinstall the ubuntu desktop from the command line.
Anyway, I let it uninstall but nothing happened to my ubuntu desktop. I don't know if it needed to reboot or if it was because I didn't close the terminal.
I then just installed the ubuntu desktop again. Problem solved.
One thing someone showed me was to use aptitude instead of apt-get. So instead of doing ```
sudo apt-get install ubuntu-desktop 
```I did ```
sudo aptitude install ubuntu-desktop
``` From what I'm told aptitude does a better job at adding and removing dependencies.
If my process works for you. Don't close the terminal. Reinstall those broken packages with aptitude. Enter sudo aptitude install for reinstalling the three broken ones.
If you get fixed run ```
sudo apt-get update
``` and then```
 sudo apt-get dist-upgrade 
```to get your system up to date.
Good luck. You have to do something because synaptic will want those broken packages fixed.

---

### Post by nismoskys on 2006-05-14
ah man.. thanks for the reply.. but im scared.. i dont wanna remove **all** those packages.. you luckily had only one package but i have ALot nd i really dont want to risk it.
is there no other possible way?

---

### Post by catlett on 2006-05-14
ubuntu-desktop is a meta package. It is the entirte gnome desktop that is installed on top of the server base system. It is ubuntu. Meaning it is far many more packages than your 49.
But since you don't know what the ubuntu-desktop is then maybe you should not do anything. Back up your info to cds and reinstall.

---

### Post by nismoskys on 2006-05-14
my badd.. but no theres gotta be an easier way.. is there not?
its not that i cant do it.. i just wanna be sure that my system wont get messed up

i have so many settings and everything.. i just did a reinstall a couple weeks ago, doing it again would be such a pain..

and also.. i have too much data to back up.. no extra drives or anything.

pleease:confused:

---

### Post by Omnios on 2006-05-14
I had a similar problem a while back while trying to install a GLX benchmark program that borke packages and wanted to uninstall everything. Anyways I did a google search of the Ubuntu archived packages using the package name and downloaded the debs released with Badger that solved my problem.

---

### Post by nismoskys on 2006-05-15
so what packages are you suggesting i try to get? The broken ones? which are libc6-dev, libc6-i686, and locales.

---

### Post by nismoskys on 2006-05-15
okay i have an idea but i dont know if it will work. someone please let me know what you think of this..

in synaptic, i go Edit -> Fix Broken Packages

Then, in filters->custom, i go to Marked Changes and i see all those packages (that i listed in an above post ^ )  marked, after i clicked 'fix broken packages'

so I highlight all those packages, and mark them for Reinstallation.

Will this work?
Please someone let me know.. as i really dont wanna mess up my system.
------
a more visual look on the above written..

Open Synaptic and see the broken packages..
[http://img211.imageshack.us/img211/6163/screenshotsynapticpackagemanag.png]("http://img211.imageshack.us/img211/6163/screenshotsynapticpackagemanag.png")

Go Edit-> Fix Broken Packages, and see in the Marked Changes..
[http://img211.imageshack.us/img211/8071/screenshotsynapticpackagemanag1.png]("http://img211.imageshack.us/img211/8071/screenshotsynapticpackagemanag1.png")

Then, Highlight all packages and right click -> Mark for Reinstallation
[http://img211.imageshack.us/img211/2641/screenshotsynaptic1ex.png]("http://img211.imageshack.us/img211/2641/screenshotsynaptic1ex.png")

Then, The Marked Changes shows:..
[http://img124.imageshack.us/img124/6163/screenshotsynapticpackagemanag.png]("http://img124.imageshack.us/img124/6163/screenshotsynapticpackagemanag.png")

Will it work?

**Thanks** again.

---

### Post by nismoskys on 2006-05-15
I FIXED MY PROBLEMS :D !! i feel good :D thanks guys for your help.

The remedy:
[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

Searched for and downloaded each package that was broken.
installed each deb with dpkg.

a couple more broken packages then showed up, but i did the same thing for them.

and now.. no more broken packages :D

--and to think how much effort would've been wasted if i reinstalled the whole os just because of this little problem. but still, thanks for your help.

:D

------
this is one thing i like about linux..
i get a problem, and although it's sometimes not **so** easily fixed, when it is fixed, you get that self-satisfaction, along with an increased knowledge about your system. a win-win situation lol

---

### Post by nismoskys on 2006-05-15
oh wait.. i just remembered what brought all these problems about in the first place..
i was trying to install BMPx
still didint get it tho lol

if anyone has any suggestions on that, id be happy(er) i guess  :P

---

### Post by qwelegen on 2008-03-13
Hi all,
I am :confused: and I am feel a bit screwed, tried to run ```
sudo apt-get install dist-upgrade
``` I was attempting to upgrade from 7.04 to 7.10 but it ended up removing most of my pakages and leaving my ubuntu a bit bare.
No Gnome desktop its all gone.
cant run ```
sudo apt-get install ubuntu-desktop
```
what toy do :confused:

---

### Post by KryoFrk on 2008-04-07
This was HUGE! I have been looking for hours how to resolve a broken package that did not show up in the synaptic manager or install -f in the terminal. 

USE aptitude NOT apt-get!

Specifically I had an issue installing libssl-dev and zlib1g-dev, but due to a broken package with libc6-i686 (of which I did not know of) I could not install them using apt-get or synaptic manager.

> sudo aptitude install

Thanks!

---

### Post by russo.mic on 2008-04-09
Why don't you take a screenshot and remove those packages?  the worst thing that could happen is you end up simply reinstalling them from the command line.

---

