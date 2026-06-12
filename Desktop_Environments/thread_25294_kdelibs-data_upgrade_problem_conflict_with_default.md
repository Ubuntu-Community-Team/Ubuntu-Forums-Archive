---
title: "kdelibs-data upgrade problem: conflict with default icons in knetworkconf"
date: 2005-04-09
forum: Desktop Environments
---

### Post by goofrider on 2005-04-09
I tried to upgrade my Hoary preview to release version (I have a Hoary preview with Kubuntu packages installed), and kdelibs-data failed to upgrade.

```

(Reading database ... 155844 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0pre1ubuntu2 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

knetworkconf is @ version 0.6.1-3ubuntu2

---

### Post by goofrider on 2005-04-16
[QUOTE=goofrider]I tried to upgrade my Hoary preview to release version (I have a Hoary preview with Kubuntu packages installed), and kdelibs-data failed to upgrade.

```

(Reading database ... 155844 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0pre1ubuntu2 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

knetworkconf is @ version 0.6.1-3ubuntu2[/QUOTE]
 hello? anyone?

---

### Post by brelic on 2005-04-21
I have the same problem on Hoary Final.  Others on #kubuntu are also reporting the same issue.

---

### Post by jan.letko on 2005-04-21
I have this problem too. Where is problem ? In the package ?

---

### Post by gunnyman on 2005-04-21
I just fixed this by doing apt-get remove knetworkconf.
Then I did apt-get dist-upgrade
then I did apt-get install knetworkconf
seems to have worked.

---

### Post by rosslaird on 2005-04-21
I can't seem to remove knetworkconf. I get this:

The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is to be installed
  kubuntu-desktop: Depends: knetworkconf but it is not going to be installed

So I seem to be good and stuck: can't upgrade, can't remove.

---

### Post by gunnyman on 2005-04-21
Ok I recall having kubuntu-desktop removed when I removed some other package and since its an empty meta package, kde function remained.
I think that is why my fix worked for me.

---

### Post by jgbreezer on 2005-04-22
Well the upgrade not only failed for me but managed to kill all the default panels on my kde toolbar (er... "kicker"??). Just left with 3 application buttons I had added myself. Where's all the defaults gone to? Upgraded about 3 packages last night after my original hoary upgrade and switch to kubuntu a week or so ago (after the 5.04 release).

Removing knetworkconf worked ok, removing kubuntu-desktop and I think kdelib-data too; then reinstall of knetworkconf worked fine, and kubuntu-desktop went back on apparently fine too, but all the config is gone..I've re-setup my background (went to plain blue) and theme but need to get the other parts of the main toolbar (apps menu, the clock, task-list, start-tray, everything!) back again.

I'm sure I can do it via the right-click->Add Panel, but I'm wondering if I can force it to reset to the kubuntu defaults (easier) or there was a setup-wizard when I first logged in after the upgrade. I cancelled it, but would be handy now!

---

### Post by titan23 on 2005-04-22
[QUOTE=jgbreezer]Well the upgrade not only failed for me but managed to kill all the default panels on my kde toolbar (er... "kicker"??). Just left with 3 application buttons I had added myself. .

I tried Ubuntu for the first time yesterday and I had the same problem. I installed 5.04 development edition from a dvd then upgraded and added KDE and everything was fine but Synaptic said I had a broken programme Knetlibs ( or similar) I tried removing and reloading but ended up like you with no kicker bar. I ended up downloading the new iso and reinstalling, KDE looks a lot better even the fonts look sharper. One problem though there is no e-mail client in the programme list so just added Kmail and also downloaded  Firefox. I think it is great and this will be my new desktop.

---

### Post by sarigue_aut on 2005-04-22
Hi, I got the same.

For me it worked like this .. (although i don't know if forcing an overwrite is the right way) ...

root@chello080108038083:~ # dpkg -i --force-overwrite /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
(Reading database ... 144879 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Setting up kdelibs-data (3.4.0-0ubuntu3.1) ...

root@chello080108038083:~ # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up kdelibs-bin (3.4.0-0ubuntu3.1) ...
Setting up kdelibs4 (3.4.0-0ubuntu3.1) ...

Setting up kdelibs (3.4.0-0ubuntu3.1) ...


Cu ...

---

### Post by ubuntu UsER on 2005-04-22
Step 1. Uninstall knetworkconf,
Step 2. Install kdelibs ,
Step 3. Install knetworkconf again.

It works for me.

---

### Post by Frustration on 2005-04-22
Oh great - now everything I try to install/uninstall brings up

/var/cache/apt/archives/kdelibs-data_4-0x1.27a3b0000005ap-1333.4.0-0ubuntu3.1_all.deb:  trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf

 ](*,) 

I have this feeling that KDE isn't going to be bootable when I restart - in which case it'll be bye bye to Kubuntu - I can't be doing with an update that f**ks the whole system up  :rolleyes:  [-X

---

### Post by tristure on 2005-04-22
[QUOTE=ubuntu UsER]Step 1. Uninstall knetworkconf,
Step 2. Install kdelibs ,
Step 3. Install knetworkconf again.

It works for me.[/QUOTE]
 Well it kinda works... but it still screws up many settings (background image, kicker applets, etc...).
So when you first reboot your box after that, be prepared for an awful surprise.

Yet, unless you got 10000 applets on your kicker or something really special in your setup, this should be only a matter of a couple of minutes to get things right. I didn't lose anything crucial (bookmarks are still here, as well as the weird manual entries in my menu).

Anyway, I believe such things should not happen. Well, they happened all the time when I was on gentoo (:-)), but I switched because I had the feeling kubuntu would be easier.

Kubuntu is a young distro, so I guess we just have to give the devs some time to tidy things up. What's been done so far is very promising, but there is still a long way to go! 

I don't mean to bash, here, and I keep Kubuntu as my main OS. But while installation is mega-easy, the speed and the general "just-works-ness" impressive, the stability is not quite there yet.

---

### Post by fordp on 2005-04-23
Here is my attempt to fix it

but it is broke :(

 ```
simon@ubuntu:~ $ sudo apt-get remove knetworkconf
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is to be installed
  kubuntu-desktop: Depends: knetworkconf but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
simon@ubuntu:~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdelibs-data
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/8013kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 118044 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
simon@ubuntu:~ $ sudo apt-get remove knetworkconf
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is to be installed
  kubuntu-desktop: Depends: knetworkconf but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
simon@ubuntu:~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdelibs-data
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/8013kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 118044 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

Can anybody help ?

---

### Post by ceti on 2005-04-23
follow this thread:

[http://www.ubuntuforums.org/showthread.php?t=28678](http://www.ubuntuforums.org/showthread.php?t=28678)

cheers
ceti

---

### Post by JuanC on 2005-04-23
I have the same error too

---

### Post by bluefrog on 2005-05-04
no fuss solution.

assuming you have already downloaded kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb

cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb

---

