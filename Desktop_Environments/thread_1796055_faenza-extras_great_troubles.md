---
title: "faenza-extras great troubles"
date: 2011-07-03
forum: Desktop Environments
---

### Post by sirius_2 on 2011-07-03
Hello, brothers and sisters!
I need your help because I've got some problem with faenza-extras package. I can neither update it nor remove or reinstall.
If I try update it I get
```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  faenza-extras
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/2354 B of archives.
After this operation, 115 kB disk space will be freed.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "ru_RU:en_US:en",
    LC_ALL = (unset),
    LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 442660 files and directories currently installed.)
Preparing to replace faenza-extras 0.9 (using .../faenza-extras_0.9-ubuntu1_i386.deb) ...
Unpacking replacement faenza-extras ...
No diversion 'diversion of /usr/share/lastfm/icons/user_black22.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/lastfm/icons/user_blue22.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/lastfm/icons/user_green22.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/lastfm/icons/user_orange22.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/lastfm/icons/user_red22.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/liferea/pixmaps/available.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/liferea/pixmaps/available_offline.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/liferea/pixmaps/empty.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/liferea/pixmaps/empty_offline.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/radiotray/images/radiotray_connecting.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/radiotray/images/radiotray_off.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/radiotray/images/radiotray_on.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/pixmaps/guake/guake-tray.png by faenza-extras', none removed.
Removing 'diversion of /usr/share/keepassx/icons/keepassx.png to /usr/share/keepassx/icons/keepassx.default.png by faenza-extras'
dpkg-divert: error: rename involves overwriting `/usr/share/keepassx/icons/keepassx.png' with
  different file `/usr/share/keepassx/icons/keepassx.default.png', not allowed
dpkg: warning: subprocess old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
No diversion 'diversion of /usr/share/lastfm/icons/user_black22.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/lastfm/icons/user_blue22.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/lastfm/icons/user_green22.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/lastfm/icons/user_orange22.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/lastfm/icons/user_red22.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/liferea/pixmaps/available.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/liferea/pixmaps/available_offline.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/liferea/pixmaps/empty.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/liferea/pixmaps/empty_offline.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/radiotray/images/radiotray_connecting.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/radiotray/images/radiotray_off.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/radiotray/images/radiotray_on.png by faenza-extras', none removed.
No diversion 'diversion of /usr/share/pixmaps/guake/guake-tray.png by faenza-extras', none removed.
Removing 'diversion of /usr/share/keepassx/icons/keepassx.png to /usr/share/keepassx/icons/keepassx.default.png by faenza-extras'
dpkg-divert: error: rename involves overwriting `/usr/share/keepassx/icons/keepassx.png' with
  different file `/usr/share/keepassx/icons/keepassx.default.png', not allowed
dpkg: error processing /var/cache/apt/archives/faenza-extras_0.9-ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
Adding 'diversion of /usr/share/lastfm/icons/user_black22.png to /usr/share/lastfm/icons/user_black22.default.png by faenza-extras'
Adding 'diversion of /usr/share/lastfm/icons/user_blue22.png to /usr/share/lastfm/icons/user_blue22.default.png by faenza-extras'
Adding 'diversion of /usr/share/lastfm/icons/user_green22.png to /usr/share/lastfm/icons/user_green22.default.png by faenza-extras'
Adding 'diversion of /usr/share/lastfm/icons/user_orange22.png to /usr/share/lastfm/icons/user_orange22.default.png by faenza-extras'
Adding 'diversion of /usr/share/lastfm/icons/user_red22.png to /usr/share/lastfm/icons/user_red22.default.png by faenza-extras'
Adding 'diversion of /usr/share/liferea/pixmaps/available.png to /usr/share/liferea/pixmaps/available.default.png by faenza-extras'
Adding 'diversion of /usr/share/liferea/pixmaps/available_offline.png to /usr/share/liferea/pixmaps/available_offline.default.png by faenza-extras'
Adding 'diversion of /usr/share/liferea/pixmaps/empty.png to /usr/share/liferea/pixmaps/empty.default.png by faenza-extras'
Adding 'diversion of /usr/share/liferea/pixmaps/empty_offline.png to /usr/share/liferea/pixmaps/empty_offline.default.png by faenza-extras'
Adding 'diversion of /usr/share/radiotray/images/radiotray_connecting.png to /usr/share/radiotray/images/radiotray_connecting.default.png by faenza-extras'
Adding 'diversion of /usr/share/radiotray/images/radiotray_off.png to /usr/share/radiotray/images/radiotray_off.default.png by faenza-extras'
Adding 'diversion of /usr/share/radiotray/images/radiotray_on.png to /usr/share/radiotray/images/radiotray_on.default.png by faenza-extras'
Adding 'diversion of /usr/share/pixmaps/guake/guake-tray.png to /usr/share/pixmaps/guake/guake-tray.default.png by faenza-extras'
Removing 'diversion of /usr/share/lastfm/icons/user_black22.png to /usr/share/lastfm/icons/user_black22.default.png by faenza-extras'
Removing 'diversion of /usr/share/lastfm/icons/user_blue22.png to /usr/share/lastfm/icons/user_blue22.default.png by faenza-extras'
Removing 'diversion of /usr/share/lastfm/icons/user_green22.png to /usr/share/lastfm/icons/user_green22.default.png by faenza-extras'
Removing 'diversion of /usr/share/lastfm/icons/user_orange22.png to /usr/share/lastfm/icons/user_orange22.default.png by faenza-extras'
Removing 'diversion of /usr/share/lastfm/icons/user_red22.png to /usr/share/lastfm/icons/user_red22.default.png by faenza-extras'
Removing 'diversion of /usr/share/liferea/pixmaps/available.png to /usr/share/liferea/pixmaps/available.default.png by faenza-extras'
Removing 'diversion of /usr/share/liferea/pixmaps/available_offline.png to /usr/share/liferea/pixmaps/available_offline.default.png by faenza-extras'
Removing 'diversion of /usr/share/liferea/pixmaps/empty.png to /usr/share/liferea/pixmaps/empty.default.png by faenza-extras'
Removing 'diversion of /usr/share/liferea/pixmaps/empty_offline.png to /usr/share/liferea/pixmaps/empty_offline.default.png by faenza-extras'
Removing 'diversion of /usr/share/radiotray/images/radiotray_connecting.png to /usr/share/radiotray/images/radiotray_connecting.default.png by faenza-extras'
Removing 'diversion of /usr/share/radiotray/images/radiotray_off.png to /usr/share/radiotray/images/radiotray_off.default.png by faenza-extras'
Removing 'diversion of /usr/share/radiotray/images/radiotray_on.png to /usr/share/radiotray/images/radiotray_on.default.png by faenza-extras'
Removing 'diversion of /usr/share/pixmaps/guake/guake-tray.png to /usr/share/pixmaps/guake/guake-tray.default.png by faenza-extras'
Removing 'diversion of /usr/share/keepassx/icons/keepassx.png to /usr/share/keepassx/icons/keepassx.default.png by faenza-extras'
dpkg-divert: error: rename involves overwriting `/usr/share/keepassx/icons/keepassx.png' with
  different file `/usr/share/keepassx/icons/keepassx.default.png', not allowed
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/faenza-extras_0.9-ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I cannot remove this package:
```

sudo apt-get remove faenza-extras 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtaskmanager4b libkscreensaver5 libsoprano-dev libkmbox xscreensaver libplasma-geolocation-interface4 libpowerdevilcore0 libprocesscore4b
  libprocessui4a libphonon-dev libksgrd4 libplasmaclock4b libkworkspace4 libkdecorations4 libkwineffects1a libplasmagenericshell4 libkephal4a
  libsolidcontrol4a libakonadi-calendar4 libphononexperimental4 libsolidcontrolifaces4a libweather-ion6 libksignalplotter4 liblsofui4
  libkunitconversion4 kdevplatform3-libs libsublime2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  faenza-extras
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 152 kB disk space will be freed.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "ru_RU:en_US:en",
    LC_ALL = (unset),
    LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing faenza-extras (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 faenza-extras
E: Sub-process /usr/bin/dpkg returned an error code (1)

```If I try sudo dpkg -P faenza-extras, I get: 
```

dpkg: error processing faenza-extras (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 faenza-extras

```

My OS: Ubuntu 11.04 32bit

---

### Post by Krytarik on 2011-07-03
Please see this earlier thread:
[http://ubuntuforums.org/showthread.php?t=1712079](http://ubuntuforums.org/showthread.php?t=1712079)

Greetings.

---

### Post by sirius_2 on 2011-07-03
> **Krytarik said:**
> Please see this earlier thread:
[http://ubuntuforums.org/showthread.php?t=1712079](http://ubuntuforums.org/showthread.php?t=1712079)

Greetings.
Hi!
Thanks for your answer. I know about this thread and I read it before. Unfortunately that advice doesn't help me. There is package faenza-extras installed in Synaptic. This package is upgradable, but I cannot upgrade it. Also I cannot remove it. The result of this actions is the error I described above.
Now any action with installation/removing/upgrading any packages is accompanied by the error of faenza-extras.I cannot do anything with this hapless package! (Except total reinstallation of the OS) But I suppose it isn't a decent way out.

---

### Post by Krytarik on 2011-07-03
Ok, the name of the package is different, but the errors, and therefore the solution, too, seem to be the same.

So, just run this command:
```
sudo dpkg -i --force-all /var/cache/apt/archives/faenza-extras_0.9-ubuntu1_i386.deb
```
Done, hopefully!

---

### Post by sirius_2 on 2011-07-03
> **Krytarik said:**
> Ok, the name of the package is different, but the errors, and therefore the solution, too, seem to be the same.

So, just run this command:
```
sudo dpkg -i --force-all /var/cache/apt/archives/faenza-extras_0.9-ubuntu1_i386.deb
```
Done, hopefully!
I know that I should specify the proper name of the package in this command.;) And I ran the command properly a few times but as a result I've got the same error!

---

### Post by sasoc on 2011-10-08
Hi

I have exactly the same problem with faenza-extras.
Have you solved this?

Regards,
Sašo

---

### Post by sirius_2 on 2011-10-09
> **sasoc said:**
> Hi

I have exactly the same problem with faenza-extras.
Have you solved this?

Regards,
Sašo
Yes, I succeeded in resolving this trouble two or three days ago. I ran this command:
```

sudo dpkg -P --force-all faenza*

```It'll purge all the packages with "faenza" in their names.

---

### Post by Krytarik on 2011-10-09
> **sirius_2 said:**
> It'll purge all the packages with "faenza" in their names.
And then reinstall Faenza, I'm guessing you mean? :P

---

### Post by sirius_2 on 2011-10-10
> **Krytarik said:**
> And then reinstall Faenza, I'm guessing you mean? :P
Yes, then you can reinstall this icon theme, if you like, of course ;)

---

### Post by brendanpiater on 2011-10-20
> **sirius_2 said:**
> Yes, I succeeded in resolving this trouble two or three days ago. I ran this command:
```

sudo dpkg -P --force-all faenza*

```It'll purge all the packages with "faenza" in their names.

Did not work for me, however with a small tweak all it did:

```
 
sudo dpkg -P --force-all faenza-extras

```

No problems from there.

Mark as solved?

Cheers
B

---

### Post by sirius_2 on 2011-10-20
> **brendanpiater said:**
> Did not work for me, however with a small tweak all it did:

```
 
sudo dpkg -P --force-all faenza-extras

```No problems from there.

Mark as solved?

Cheers
B
Hm-m... Yes, I think so. ;)

---

