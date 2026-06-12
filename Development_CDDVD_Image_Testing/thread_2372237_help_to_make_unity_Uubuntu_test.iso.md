---
title: "help to make unity Uubuntu test.iso"
date: 2017-09-22
forum: Development CD/DVD Image Testing
---

### Post by ventrical on 2017-09-22
I need some assistance to make a distro (unity7.iso or Uubuntu.iso) an upload it to a ppa.

 I need step by step instruction of how to do this in launchpad? I think it would be. I don't like  the idea of doing it alone. If we could make a seperate spin of unity them perhaps I can request that development be re-opened  for a (unity9) spin for desktops only.

Any help , advice , comments, the good , the bad and the ugly .. please feel free to comment. All I ask is to stay on topic.  We may get ubunt-desktop-team advice because I patch these threads out to the desktop-team

Regards..

---

### Post by ventrical on 2017-09-22
Sent this off to will Cooke.

---

### Post by jbicha on 2017-09-22
Making ISOs is difficult. That's why there is such strong incentive to become an official Ubuntu flavor. Ubuntu Budgie had to make ISOs until last year when they became official; System76 makes ISOs now.

PPAs host Ubuntu packages (.deb's) not ISOs.

What do you mean by Unity 9?

---

### Post by sudodus on 2017-09-22
I saw this answer at AskUbuntu. I think it could be useful :-)

[Q: Transfer all file and programs and settings to iso file; A: Systemback](https://askubuntu.com/questions/958324/transfer-all-file-and-programs-and-settings-to-iso-file#comment1530338_958324)

I have not used it, but the instructions are rather detailed.

---

### Post by sudodus on 2017-09-22
> **jbicha said:**
> Making ISOs is difficult. That's why there is such strong incentive to become an official Ubuntu flavor. Ubuntu Budgie had to make ISOs until last year when they became official; System76 makes ISOs now.

PPAs host Ubuntu packages (.deb's) not ISOs.


+1

[Sourceforge](https://sourceforge.net/) is a possible host for iso files.

---

### Post by ventrical on 2017-09-22
> **sudodus said:**
> I saw this answer at AskUbuntu. I think it could be useful :-)

[Q: Transfer all file and programs and settings to iso file; A: Systemback]("https://askubuntu.com/questions/958324/transfer-all-file-and-programs-and-settings-to-iso-file#comment1530338_958324")

I have not used it, but the instructions are rather detailed.

Thanks Sudodus. I am currently going to try UCK and taskel. If that don't work will try your suggest.

---

### Post by ventrical on 2017-09-22
> **jbicha said:**
> Making ISOs is difficult. That's why there is such strong incentive to become an official Ubuntu flavor. Ubuntu Budgie had to make ISOs until last year when they became official; System76 makes ISOs now.

PPAs host Ubuntu packages (.deb's) not ISOs.

What do you mean by Unity 9?

Hey,

Thanks Jeremy. 

Unity9 is just logical next step for *desktop*  only. So .. if I can create a stable spin of unity7 then perhaps I could request that we re-open dev for unity with community support. it is just a very small seed at this time. It would not require any devs to split time from gnome.

Regards..

---

### Post by ventrical on 2017-09-22
> **sudodus said:**
> +1

[Sourceforge]("https://sourceforge.net/") is a possible host for iso files.

And thanks for that link also.

---

### Post by cariboo on 2017-09-22
ventrical, have you had a  look at [this]("https://help.ubuntu.com/community/LiveCDCustomization") for creating a LiveCD.

You'll probably have to get the iso hosted on someplace like [Github]("https://github.com/"), until you get your version accepted as an official flavour.

---

### Post by ventrical on 2017-09-22
@cariboo

:)

I first have to get a succesful build:)


failed_build
```

tk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Preparing build environment...
Running build process...
[sudo] password for ventrical: Build (/usr/bin/uck-gui --wait-before-exit) started at 2017-09-22 16:16:09

>> Ubuntu Customization Kit 2.4.7 on Ubuntu 17.10, 4.13.0-11-generic x86_64
Starting CD remastering on  Fri Sep 22 16:16:28 EDT 2017
Customization dir=/home/ventrical/tmp/customization-scripts
Mounting ISO image...
mount: /home/ventrical/tmp/remaster-iso-mount: WARNING: device write-protected, mounted read-only.
Unpacking ISO image...
Unmounting ISO image...
Mounting SquashFS image...
Unpacking SquashFS image...
Unmounting SquashFS image...
Removing win32 files...
Creating apt cache...
Creating root home...
Mounting /proc
Mounting /sys
Mounting /dev/pts
Mounting /tmp
Mounting /home/ventrical/tmp/remaster-root-home
Mounting /home/ventrical/tmp/remaster-apt-cache
Mounting /run
Mounting /home/ventrical/tmp/customization-scripts
Copying fstab/mtab...
Creating DBUS uuid...
Deactivating initctl...
mv: cannot stat '/sbin/initctl': No such file or directory
Deactivating update-grub...
Deactivating grub-probe...
Hacking grub-probe postinst/postrm...
Remembering kernel update state...
>> Customizing: Ubuntu 17.10, 4.12.0-13-generic x86_64
Get:1 http://archive.ubuntu.com/ubuntu artful InRelease [237 kB]
Hit:2 http://security.ubuntu.com/ubuntu artful-security InRelease
Hit:3 http://archive.ubuntu.com/ubuntu artful-updates InRelease
Get:4 http://archive.ubuntu.com/ubuntu artful/main amd64 Packages [1080 kB]
Get:5 http://archive.ubuntu.com/ubuntu artful/main Translation-en [544 kB]
Get:6 http://archive.ubuntu.com/ubuntu artful/main amd64 DEP-11 Metadata [435 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/main DEP-11 64x64 Icons [278 kB]
Get:8 http://archive.ubuntu.com/ubuntu artful/restricted amd64 Packages [8608 B]
Get:9 http://archive.ubuntu.com/ubuntu artful/restricted Translation-en [2724 B]
Get:10 http://archive.ubuntu.com/ubuntu artful/universe amd64 Packages [8092 kB]
Get:11 http://archive.ubuntu.com/ubuntu artful/universe Translation-en [4785 kB]
Get:12 http://archive.ubuntu.com/ubuntu artful/universe amd64 DEP-11 Metadata [2833 kB]
Get:13 http://archive.ubuntu.com/ubuntu artful/universe DEP-11 64x64 Icons [7929 kB]
Fetched 26.2 MB in 57s (460 kB/s)
Reading package lists...
Installing language packs (en)...
Reading package lists...
Building dependency tree...
Reading state information...
language-pack-en-base is already the newest version (1:17.10+20170703).
language-pack-gnome-en-base is already the newest version (1:17.10+20170703).
The following packages will be upgraded:
  language-pack-en language-pack-gnome-en
2 upgraded, 0 newly installed, 0 to remove and 272 not upgraded.
Need to get 606 kB of archives.
After this operation, 632 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu artful/main amd64 language-pack-en all 1:17.10+20170918 [250 kB]
Get:2 http://archive.ubuntu.com/ubuntu artful/main amd64 language-pack-gnome-en all 1:17.10+20170918 [356 kB]
Fetched 606 kB in 1s (336 kB/s)
(Reading database ... 136988 files and directories currently installed.)
Preparing to unpack .../language-pack-en_1%3a17.10+20170918_all.deb ...
Unpacking language-pack-en (1:17.10+20170918) over (1:17.10+20170828) ...
Replacing files in old package language-pack-en-base (1:17.10+20170703) ...
Preparing to unpack .../language-pack-gnome-en_1%3a17.10+20170918_all.deb ...
Unpacking language-pack-gnome-en (1:17.10+20170918) over (1:17.10+20170828) ...
Replacing files in old package language-pack-gnome-en-base (1:17.10+20170703) ...
Setting up language-pack-en (1:17.10+20170918) ...
Setting up language-pack-gnome-en (1:17.10+20170918) ...
W: --force-yes is deprecated, use one of the options starting with --allow instead.
Removing unnecessary language packages...
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be REMOVED:
  firefox-locale-de* firefox-locale-es* firefox-locale-fr* firefox-locale-it*
  firefox-locale-pt* firefox-locale-ru* firefox-locale-zh-hans*
  language-pack-de* language-pack-de-base* language-pack-es*
  language-pack-es-base* language-pack-fr* language-pack-fr-base*
  language-pack-gnome-de* language-pack-gnome-de-base* language-pack-gnome-es*
  language-pack-gnome-es-base* language-pack-gnome-fr*
  language-pack-gnome-fr-base* language-pack-gnome-it*
  language-pack-gnome-it-base* language-pack-gnome-pt*
  language-pack-gnome-pt-base* language-pack-gnome-ru*
  language-pack-gnome-ru-base* language-pack-gnome-zh-hans*
  language-pack-gnome-zh-hans-base* language-pack-it* language-pack-it-base*
  language-pack-pt* language-pack-pt-base* language-pack-ru*
  language-pack-ru-base* language-pack-zh-hans* language-pack-zh-hans-base*
0 upgraded, 0 newly installed, 35 to remove and 258 not upgraded.
                                                                 After this operation, 252 MB disk space will be freed.
(Reading database ... 136995 files and directories currently installed.)
Removing firefox-locale-de (50.1.0+build2-0ubuntu1) ...
Removing firefox-locale-es (50.1.0+build2-0ubuntu1) ...
Removing firefox-locale-fr (50.1.0+build2-0ubuntu1) ...
Removing firefox-locale-it (50.1.0+build2-0ubuntu1) ...
Removing firefox-locale-pt (50.1.0+build2-0ubuntu1) ...
Removing firefox-locale-ru (50.1.0+build2-0ubuntu1) ...
Removing firefox-locale-zh-hans (50.1.0+build2-0ubuntu1) ...
Removing language-pack-de-base (1:17.10+20170703) ...
Removing language-pack-gnome-es-base (1:17.10+20170703) ...
Removing language-pack-gnome-es (1:17.10+20170828) ...
Removing language-pack-es-base (1:17.10+20170703) ...
Removing language-pack-gnome-fr-base (1:17.10+20170703) ...
Removing language-pack-gnome-fr (1:17.10+20170828) ...
Removing language-pack-fr-base (1:17.10+20170703) ...
Removing language-pack-gnome-it-base (1:17.10+20170703) ...
Removing language-pack-gnome-pt-base (1:17.10+20170703) ...
Removing language-pack-gnome-ru-base (1:17.10+20170703) ...
Removing language-pack-gnome-zh-hans-base (1:17.10+20170703) ...
Removing language-pack-it-base (1:17.10+20170703) ...
Removing language-pack-pt-base (1:17.10+20170703) ...
Removing language-pack-ru-base (1:17.10+20170703) ...
Removing language-pack-zh-hans-base (1:17.10+20170703) ...
Removing language-pack-gnome-de-base (1:17.10+20170703) ...
Removing language-pack-gnome-de (1:17.10+20170828) ...
Removing language-pack-de (1:17.10+20170828) ...
Removing language-pack-es (1:17.10+20170828) ...
Removing language-pack-fr (1:17.10+20170828) ...
Removing language-pack-gnome-it (1:17.10+20170828) ...
Removing language-pack-gnome-pt (1:17.10+20170828) ...
Removing language-pack-gnome-ru (1:17.10+20170828) ...
Removing language-pack-gnome-zh-hans (1:17.10+20170828) ...
Removing language-pack-it (1:17.10+20170828) ...
Removing language-pack-pt (1:17.10+20170828) ...
Removing language-pack-ru (1:17.10+20170828) ...
Removing language-pack-zh-hans (1:17.10+20170828) ...
(Reading database ... 127832 files and directories currently installed.)
Purging configuration files for language-pack-pt-base (1:17.10+20170703) ...
Purging configuration files for language-pack-gnome-fr-base (1:17.10+20170703) ...
Purging configuration files for language-pack-ru-base (1:17.10+20170703) ...
Purging configuration files for language-pack-gnome-es-base (1:17.10+20170703) ...
Purging configuration files for language-pack-gnome-zh-hans-base (1:17.10+20170703) ...
Purging configuration files for language-pack-es-base (1:17.10+20170703) ...
Purging configuration files for language-pack-gnome-pt-base (1:17.10+20170703) ...
Purging configuration files for language-pack-gnome-de-base (1:17.10+20170703) ...
Purging configuration files for language-pack-zh-hans-base (1:17.10+20170703) ...
Purging configuration files for language-pack-fr-base (1:17.10+20170703) ...
Purging configuration files for language-pack-de-base (1:17.10+20170703) ...
Purging configuration files for language-pack-gnome-ru-base (1:17.10+20170703) ...
Purging configuration files for language-pack-gnome-it-base (1:17.10+20170703) ...
Purging configuration files for language-pack-it-base (1:17.10+20170703) ...
W: --force-yes is deprecated, use one of the options starting with --allow instead.
Done
Restoring kernel update state...
Reactivating initctl...
mv: cannot stat '/sbin/initctl.uck_blocked': No such file or directory
Reactivating update-grub...
Reactivating grub-probe...
Reactivating grub-probe postinst/postrm...
Removing generated machine uuid...
Removing generated fstab/mtab...
Removing crash reports...
Unmounting /home/ventrical/tmp/remaster-root/var/cache/apt...
Unmounting /home/ventrical/tmp/remaster-root/tmp/customization-scripts...
Unmounting /home/ventrical/tmp/remaster-root/tmp...
Unmounting /home/ventrical/tmp/remaster-root/sys...
Unmounting /home/ventrical/tmp/remaster-root/run...
Unmounting /home/ventrical/tmp/remaster-root/root...
Unmounting /home/ventrical/tmp/remaster-root/proc...
Unmounting /home/ventrical/tmp/remaster-root/dev/pts...
Cleaning up temporary directories...
Running ISO customization script /home/ventrical/tmp/customization-scripts/customize_iso...
--2017-09-22 16:22:34--  http://archive.ubuntu.com/ubuntu/ubuntu/ubuntu/dists/artful/main/source/Sources.gz
Resolving archive.ubuntu.com (archive.ubuntu.com)... 91.189.88.152, 91.189.91.26, 91.189.88.149, ...
Connecting to archive.ubuntu.com (archive.ubuntu.com)|91.189.88.152|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1092931 (1.0M) [application/x-gzip]
Saving to: ‘/tmp/tmp.phOxncRngW/Sources.gz’

     0K .......... .......... .......... .......... ..........  4%  231K 4s
    50K .......... .......... .......... .......... ..........  9%  478K 3s
   100K .......... .......... .......... .......... .......... 14%  461K 3s
   150K .......... .......... .......... .......... .......... 18%  157K 3s
   200K .......... .......... .......... .......... .......... 23%  685K 3s
   250K .......... .......... .......... .......... .......... 28%  905K 2s
   300K .......... .......... .......... .......... .......... 32%  430K 2s
   350K .......... .......... .......... .......... .......... 37%  174M 2s
   400K .......... .......... .......... .......... .......... 42% 70.7K 2s
   450K .......... .......... .......... .......... .......... 46%  592K 2s
   500K .......... .......... .......... .......... .......... 51%  200K 2s
   550K .......... .......... .......... .......... .......... 56%  194M 2s
   600K .......... .......... .......... .......... .......... 60%  197M 1s
   650K .......... .......... .......... .......... .......... 65%  182M 1s
   700K .......... .......... .......... .......... .......... 70%  144K 1s
   750K .......... .......... .......... .......... .......... 74%  186M 1s
   800K .......... .......... .......... .......... .......... 79% 1.93M 1s
   850K .......... .......... .......... .......... .......... 84%  208M 0s
   900K .......... .......... .......... .......... .......... 89%  241M 0s
   950K .......... .......... .......... .......... .......... 93% 3.63M 0s
  1000K .......... .......... .......... .......... .......... 98%  209M 0s
  1050K .......... .......                                    100%  190M=2.4s

2017-09-22 16:22:37 (440 KB/s) - ‘/tmp/tmp.phOxncRngW/Sources.gz’ saved [1092931/1092931]

--2017-09-22 16:22:37--  http://archive.ubuntu.com/ubuntu/ubuntu/ubuntu/pool/main/g/gfxboot-theme-ubuntu/
Resolving archive.ubuntu.com (archive.ubuntu.com)... 91.189.88.152, 91.189.91.26, 91.189.88.149, ...
Connecting to archive.ubuntu.com (archive.ubuntu.com)|91.189.88.152|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6465 (6.3K) [text/html]
Saving to: ‘index.html’

     0K ......                                                100%  653K=0.01s

2017-09-22 16:22:37 (653 KB/s) - ‘index.html’ saved [6465/6465]

tar (child): *.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
Unable to extract gfxboot-theme-ubuntu source package
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.


```

---

### Post by Chanath on 2017-09-22
*I am very glad about this thread.* Making isos is not that difficult. If it was difficult, there won't be so many Ubuntu based distros around. You make squashfs file off your install. In your install you have to have an installer. Or, you can just unsquash the live iso, put it somewhere, get in it in chroot, change whatever you want, change the distro name, change name in python-apt, change the distro name in isolinux, boot etc. Once done, squash it back and you have a installable live iso. That's in a nutshell.

To study how its constructed just download artful iso, unarchive it, then unsquash the squashfs file in casper. Being a coder, you'd find how it is. First create your own installable iso from your install. Getting the official recognition is a later matter. 

When you install, all the installer packages are uninstalled. You can see what's missing by comparing the installed one and the unsquashed file.

---

### Post by ventrical on 2017-09-22
UCK is absolutely useless  stable or unstable.. anyways back to drawing board...

---

### Post by jbicha on 2017-09-22
> **ventrical said:**
> 
Unity9 is just logical next step for *desktop*  only.

Unless you're making really big changes, there's no need to bump the version number.

---

### Post by Chanath on 2017-09-22
1) [https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall](https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall)
2) Download remastersys fork from here, [https://sourceforge.net/projects/pinguy-os/files/ISO_Builder/](https://sourceforge.net/projects/pinguy-os/files/ISO_Builder/) You can read code, so you'd know how its built.
3) Some interesting reading here,  [http://www.funtoo.org/Install](http://www.funtoo.org/Install)

---

### Post by ventrical on 2017-09-22
> **jbicha said:**
> Unless you're making really big changes, there's no need to bump the version number.


Hi Jeremy,

Thanks for your words of wisdom here :)
I was speaking only if unity were ever opened again for development.  For spin it would be U7 of course.

Regards..

---

### Post by ventrical on 2017-09-22
> **Chanath said:**
> 1) [https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall](https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall)
2) Download remastersys fork from here, [https://sourceforge.net/projects/pinguy-os/files/ISO_Builder/](https://sourceforge.net/projects/pinguy-os/files/ISO_Builder/) You can read code, so you'd know how its built.
3) Some interesting reading here,  [http://www.funtoo.org/Install](http://www.funtoo.org/Install)

@Chanath,

Ok .. thanks Chanath. Leave it with me. I want to make sure UCK is not working first. I am going to try it on another box and then try some of the other links.

Regards..

---

### Post by Chanath on 2017-09-23
I think UCK will not work, not compatible with UEFI or something like that. 
You can also try Cubic from P.J. Singh  [https://launchpad.net/cubic](https://launchpad.net/cubic) or here, [https://launchpad.net/~cubic-wizard/+archive/ubuntu/release](https://launchpad.net/~cubic-wizard/+archive/ubuntu/release)

---

### Post by ventrical on 2017-09-23
> **Chanath said:**
> I think UCK will not work, not compatible with UEFI or something like that. 
You can also try Cubic from P.J. Singh  [https://launchpad.net/cubic](https://launchpad.net/cubic) or here, [https://launchpad.net/~cubic-wizard/+archive/ubuntu/release](https://launchpad.net/~cubic-wizard/+archive/ubuntu/release)

You are correct UCK will not work from UEFI or BIOS mode atm . It has not been updated. However .. !!Success!! with pinguy. Creates a live, installable system using 17.10. I have to do some tweaking to get it just right. You have to start from a clean install .etc.. so far .. so good..created working live custom install and was able to install it to hdd. has issues..

Regards..

---

### Post by Chanath on 2017-09-23
Bit of history, maybe off topic. 
Remastersys was (and is) a superb script. Its creator had a web site and a forums too. But, after so many arguments, attacks, etc, he dropped the development and closed the forums. Antoni Norman created Pinguy OS, which was also doing so well, but money is needed to run the website, so one day he went off air saying he's thinking of killing the project. While he was still developing, he forked the Remastersys to support UEFI for both 32 and 64 bit. [http://pinguyos.com/2015/09/pinguy-builder-an-app-to-backupremix-buntu/](http://pinguyos.com/2015/09/pinguy-builder-an-app-to-backupremix-buntu/)

If you open /usr/bin/PinguyBuilder, you'd see how the script is constructed. 

If you want to look at the original Remastersys, someone had uploaded it here, [https://launchpad.net/~mutse-young/+archive/ubuntu/remastersys/+packages](https://launchpad.net/~mutse-young/+archive/ubuntu/remastersys/+packages)

---

### Post by ventrical on 2017-09-23
> **Chanath said:**
> Bit of history, maybe off topic. 
Remastersys was (and is) a superb script. Its creator had a web site and a forums too. But, after so many arguments, attacks, etc, he dropped the development and closed the forums. Antoni Norman created Pinguy OS, which was also doing so well, but money is needed to run the website, so one day he went off air saying he's thinking of killing the project. While he was still developing, he forked the Remastersys to support UEFI for both 32 and 64 bit. [http://pinguyos.com/2015/09/pinguy-builder-an-app-to-backupremix-buntu/](http://pinguyos.com/2015/09/pinguy-builder-an-app-to-backupremix-buntu/)

If you open /usr/bin/PinguyBuilder, you'd see how the script is constructed. 

If you want to look at the original Remastersys, someone had uploaded it here, [https://launchpad.net/~mutse-young/+archive/ubuntu/remastersys/+packages](https://launchpad.net/~mutse-young/+archive/ubuntu/remastersys/+packages)

I have used remastersys long ago.

 I have already built a spin of 17.10. Pinguy will not build on an install that is in UEFI mode. If you want to build it in UEFI .. be my guest. It will create an ISO that will run in UEFI but I am not concerned with that atm. So I have a solid compiler that works on development versions with PCs in BIOS mode. When I get something built that I am satisfied with I'll put  up a link for those who may want to test it. 

Regards..

---

### Post by Chanath on 2017-09-23
OK. Have a look at this too, if you want, [https://sourceforge.net/projects/bodhibuilder/files/](https://sourceforge.net/projects/bodhibuilder/files/)

---

### Post by sudodus on 2017-09-23
> **ventrical said:**
> I have used remastersys long ago.

 I have already built a spin of 17.10. Pinguy will not build on an install that is in UEFI mode. If you want to build it in UEFI .. be my guest. _It will create an ISO that will run in UEFI_ but I am not concerned with that atm. So I have a solid compiler that works on development versions with PCs in BIOS mode. When I get something built that I am satisfied with I'll put  up a link for those who may want to test it. 

Regards..

This sounds good :-)

---

### Post by Chanath on 2017-09-23
Looks like Ubiquity and Ubiquity-frontend-gtk are interconnected with gnome-shell, gnome-shell-common and ubuntu-session. If you are to make live iso with only unity, you'd have to install ubiquity, ubiquity-frontend-gtk using some other way.

---

### Post by ventrical on 2017-09-23
> **Chanath said:**
> Looks like Ubiquity and Ubiquity-frontend-gtk are interconnected with gnome-shell, gnome-shell-common and ubuntu-session. If you are to make live iso with only unity, you'd have to install ubiquity, ubiquity-frontend-gtk using some other way.

I am doing a study of this but I have to do some other tests first, ie; To use lightdm ..etc..


Regards..

---

### Post by ventrical on 2017-09-23
> **sudodus said:**
> This sounds good :-)

It boots very well in UEFI mode with almost no bugs. In BIOS mode there are bugs and a Debian live boot screen  With gdm. So I am changing to lightdm and see if that will fix.

---

### Post by Chanath on 2017-09-23
Check in /etc/PinguyBuilder/isolinux, if you are using Pinguy to build it.

---

### Post by mc4man on 2017-09-23
Notwithstanding the effort, ect. I can't fathom the purpose here. Atm unity is available & usable in 17.10 & will be in 18.04, at least to start.
So what would this "iso" reflect. A point in time artful, some point in time b*, or something else?

From a general user perspective non lts releases are useless, once eol one has to advance, the repos are moved & locked, ppa builds are no longer possible.
So my view is as far as unity it's either 16.04 or *possibly* 18.04 if it remains viable & usable. In any event one would want to be able to install & update all the other stuff, whether from the ubuntu repos or ppa's.

---

### Post by ventrical on 2017-09-23
> **Chanath said:**
> Looks like Ubiquity and Ubiquity-frontend-gtk are interconnected with gnome-shell, gnome-shell-common and ubuntu-session. If you are to make live iso with only unity, you'd have to install ubiquity, ubiquity-frontend-gtk using some other way.

It works just fine. I have an installable Unity7 (live) Only ISO with Ubiquity installers. I am writing this message from a Unity7 only hard install.

Regards..

---

### Post by ventrical on 2017-09-23
> **mc4man said:**
> Notwithstanding the effort, ect. I can't fathom the purpose here. Atm unity is available & usable in 17.10 & will be in 18.04, at least to start.
So what would this "iso" reflect. A point in time artful, some point in time b*, or something else?

Good pointed questions here.

1. If it remains stable through 17.10 then it may at some point be considered as an ubuntu-distro in the furture, version unity9 for desktops. Unity8 is already forked to another group so Unity9 would be the logical next step for desktops.

The current .ISO that I just built this am: runs on the current 17.10 and is fully update-able. It is unity7 only with lightdm.   


> 
From a general user perspective non lts releases are useless, once eol one has to advance, the repos are moved & locked, ppa builds are no longer possible.
So my view is as far as unity it's either 16.04 or *possibly* 18.04 if it remains viable & usable. In any event one would want to be able to install & update all the other stuff, whether from the ubuntu repos or ppa's.

The ISO I created  this morning , when hard installed, can do all the features you mention above. Again ..idea is to have Unity7 distro Uubuntu. I am not worried  about what happens in the repos with 18.04 because all I am getting is "should be's", "probably", "maybe" , "we hope" etc.. and I understand because they have downsized their development resources  considerably. I too hope that they continue to keep unity7 during 18.04.  The other thing is that I can now hack and modify untiy7 to unity9 and compiz  and hopefully clean up some bugs and other issues . Once I do something effective and proper with this I could perhaps request that unity9 be reopened for development, most likely , from a group of community maintainers but also would need Canonical help. It's just an idea. If they shoot that down then maybe a ppa.

Regards..

---

### Post by ventrical on 2017-09-23
Other than sourceforge.. is there anywhere else to upload iso files that is somewhat secure? I cant afford cloud.

regards..

---

### Post by Frogs Hair on 2017-09-23
> **ventrical said:**
> Other than sourceforge.. is there anywhere else to upload iso files that is somewhat secure? I cant afford cloud.

regards..

MEGA offers 50 GB free with encryption .

---

### Post by ventrical on 2017-09-23
> **Frogs Hair said:**
> MEGA offers 50 GB free with encryption .

:) Thanks .. Snailloading....:)

---

### Post by Chanath on 2017-09-23
Sourceforge is free and your distro will be there practically forever. Its where most Linux users look in for newer distros and remixes. You can also upload to Linuxtracker as torrent. You can even find Ubuntu 17.04 there, [http://linuxtracker.org/index.php?page=torrent-details&id=59066769b9ad42da2e508611c33d7c4480b3857b&hit=1](http://linuxtracker.org/index.php?page=torrent-details&id=59066769b9ad42da2e508611c33d7c4480b3857b&hit=1)

---

### Post by ventrical on 2017-09-23
> **Chanath said:**
> Sourceforge is free and your distro will be there practically forever. Its where most Linux users look in for newer distros and remixes. You can also upload to Linuxtracker as torrent. You can even find Ubuntu 17.04 there, [http://linuxtracker.org/index.php?page=torrent-details&id=59066769b9ad42da2e508611c33d7c4480b3857b&hit=1](http://linuxtracker.org/index.php?page=torrent-details&id=59066769b9ad42da2e508611c33d7c4480b3857b&hit=1)

Would rather not use sourceforge. Might have to anyways. Uploading to MEGA now..it'll just take some time.

regards..

---

### Post by ventrical on 2017-09-23
This is the 17.10 iso called Unity7Ubuntu.iso which is an amd64 remix. It is fully installable, updateable and upgradeable just like any other ubuntu.iso At first hard install it will run Unity7 by default. No other DEs are on this disk .. but they can be installed from repo. The USB may not work on all machines.  No modifications have been made to unity or the ubuntu 17.10 distribution. This is a test .iso only. On slower drives and slower machines you may have to wait for full bootup. The ISO will install just fine to USB using 'restore' option from  'disks'.


  Unity7Ubuntu:   [URL="https://mega.nz/#!4LZCkYwD!O3DuEpNiruvuO1SWSDvhFC6r_PDx3Xua6NCXNzSsibg"]https://mega.nz/#!4LZCkYwD!O3DuEpNiruvuO1SWSDvhFC6r_PDx3Xua6NCXNzSsibg
[/URL]      
   md5 :    [https://mega.nz/#!ULJXkTBC!jBuTq2Yk5muAoE6BUQ0Z626AY51cOEPceqOExEk3YPs](https://mega.nz/#!ULJXkTBC!jBuTq2Yk5muAoE6BUQ0Z626AY51cOEPceqOExEk3YPs)
        
sha256:   [https://mega.nz/#!JSpE2DzR!EUEgEyVl9baZv8Gs4Wp8-G64SEBzt3MKOwjxl83hqLg](https://mega.nz/#!JSpE2DzR!EUEgEyVl9baZv8Gs4Wp8-G64SEBzt3MKOwjxl83hqLg)
        

Regards..

---

### Post by mc4man on 2017-09-23
Well - 
The live session loaded ok & ran ok (though no touchpad settings & no tap to click, could move cursor though..
The bootloader install fails so the Os is installed but not in grub.
Running update-grub from my current 16.04 did add it, haven't rebooted yet though to see if the install is usable. (/dev/sdb6

edit: the install is usable, definitely missing touchpad in settings, is that also seen in normal 17.10 install > add unity session?

---

### Post by mc4man on 2017-09-23
A few thoughts
Did you intend to leave all those things you installed? (gedit-plugins, gst-libav, inkscape, synaptic, bunch of gnome-* stuff, ect.
Also - most main /var/logs are not being written to (boot, kernel, syslog, ect.)  there is a significant block of errors early in the boot though with no logs...
Honestly I think you should be patient & see what transpires in 18.04..

On a positive note - your live session exits cleanly, something the current Ubuntu images are likely not to do. Probably  from using lightdm rather than that bug ridden gdm3

---

### Post by ventrical on 2017-09-24
> **mc4man said:**
> A few thoughts
Did you intend to leave all those things you installed? (gedit-plugins, gst-libav, inkscape, synaptic, bunch of gnome-* stuff, ect.
Also - most main /var/logs are not being written to (boot, kernel, syslog, ect.)  there is a significant block of errors early in the boot though with no logs...
Honestly I think you should be patient & see what transpires in 18.04..

On a positive note - your live session exits cleanly, something the current Ubuntu images are likely not to do. Probably  from using lightdm rather than that bug ridden gdm3

mac4man,

Thanks for your comments.  That remix is from an earlier install that had some gdm problems. I had it boot live and install on three machines.  Yes .. there are some issues on that install .. and so certainly they came out in the  remix.  I plan to go  ahead and try another  spin on a clean install and see if I can get the grub problem fixed using some different build options.

  I am still enthusiastic that 18.04 will squeeze unity7 into the repos but in the meantime I am going to  continue  to experiment with more builds. Thanks for your positive comments. Much appreaciated :)

Regards..

---

### Post by Chanath on 2017-09-24
Downloaded few minutes ago. Booted quite nicely in live mode. Live boot login screen on a MBR laptop gets the background picture from /etc/PinguyBuilder/isolinux. ([https://ubuntuforums.org/showthread.php?t=2372237&page=3#26](https://ubuntuforums.org/showthread.php?t=2372237&page=3#26)) It was the same way in Remastersys. You can change that picture to any, if you are using Remastersys script, whatever its name now. Will try on a UEFI laptop later.

Firefox opens much faster than in default Ubuntu. Nautilus too. This is a problem with Gnome, the lag. It looks like this lag was not taken into account when deciding on making Gnome the default. Unity greeter responds immediately; gdm has to think a little before logging. Unity launcher moves in an out of hiding in the normal smoother way.

There is no installer icon. This has to be checked in PinguyBuilder.  

Will try now on a Uefi.

EDIT: Booted nicely on a UEFI laptop. No installer icon here too. Firefox starts just as quickly. Nautilus too. In both laptops there are no lags. Open window movements are smooth in both. In the default Ubuntu, those movements are jerky. No idea, why someone would want to change nicer smoother experience to a jerky one.

Suggestion: Try making the live installable iso in a chroot manually.

---

### Post by ventrical on 2017-09-24
> **Chanath said:**
> Downloaded few minutes ago. Booted quite nicely in live mode. Live boot login screen on a MBR laptop gets the background picture from /etc/PinguyBuilder/isolinux. ([https://ubuntuforums.org/showthread.php?t=2372237&page=3#26](https://ubuntuforums.org/showthread.php?t=2372237&page=3#26)) It was the same way in Remastersys. You can change that picture to any, if you are using Remastersys script, whatever its name now. Will try on a UEFI laptop later.

Firefox opens much faster than in default Ubuntu. Nautilus too. This is a problem with Gnome, the lag. It looks like this lag was not taken into account when deciding on making Gnome the default. Unity greeter responds immediately; gdm has to think a little before logging. Unity launcher moves in an out of hiding in the normal smoother way.

There is no installer icon. This has to be checked in PinguyBuilder.  

Will try now on a Uefi.

EDIT: Booted nicely on a UEFI laptop. No installer icon here too. Firefox starts just as quickly. Nautilus too. In both laptops there are no lags. Open window movements are smooth in both. In the default Ubuntu, those movements are jerky. No idea, why someone would want to change nicer smoother experience to a jerky one.

Suggestion: Try making the live installable iso in a chroot manually.

@Chanath

There are two installer icons. One in the unity panel and  just double-click ubiquity.desktop.

Regards..

---

### Post by ventrical on 2017-09-24
> **Chanath said:**
> Downloaded few minutes ago. Booted quite nicely in live mode. Live boot login screen on a MBR laptop gets the background picture from /etc/PinguyBuilder/isolinux. ([https://ubuntuforums.org/showthread.php?t=2372237&page=3#26](https://ubuntuforums.org/showthread.php?t=2372237&page=3#26)) It was the same way in Remastersys. You can change that picture to any, if you are using Remastersys script, whatever its name now. Will try on a UEFI laptop later.

Firefox opens much faster than in default Ubuntu. Nautilus too. This is a problem with Gnome, the lag. It looks like this lag was not taken into account when deciding on making Gnome the default. Unity greeter responds immediately; gdm has to think a little before logging. Unity launcher moves in an out of hiding in the normal smoother way.

There is no installer icon. This has to be checked in PinguyBuilder.  

Will try now on a Uefi.

EDIT: Booted nicely on a UEFI laptop. No installer icon here too. Firefox starts just as quickly. Nautilus too. In both laptops there are no lags. Open window movements are smooth in both. In the default Ubuntu, those movements are jerky. No idea, why someone would want to change nicer smoother experience to a jerky one.

Suggestion: Try making the live installable iso in a chroot manually.

There were initially some problems with 4.13.0-11 and gdm .. or it was just gdm. (I filed a bug and posted it- didn't get much attention on both the kernel and gdm but nobody else could confirm the bug as of yet.) So there is systemd problems. gdm problems and maybe kernel problems binding gdm. I think it has to do with the way the post-boot is trying to jockey with xorg and wayland. So I think this is a growing pain and not really a big problem.

 Also thank you for your positive comments and links. I may not get to all suggestions but I am going methodically along here.

 Just a side note: I am beginning to like the gnome dock. It works smoothly on my intel base graphics boxes but there is a herkity-jerkity effect with nvidia graphics. Obviously the unity desktop is a smoother operator than most desktop experiences but it looks as though  it is getting better, however slowly, with gnome.  Perhaps a lot of this will be cleaned up during 18.04 and so I am committed to help them test.

Regards..

---

### Post by ventrical on 2017-09-24
@Chanath,

Thanks for testing! :)

I plan to make more builds but I have to check with service-provider becau$e of bandwidth.Also might try to find a faster cloud service. I think Canonical gives 10GBs free or something. When I get something a little faster I'll post some upgraded builds.

Regards..

---

### Post by Chanath on 2017-09-24
> **ventrical said:**
> @Chanath

There are two installer icons. One in the unity panel and  just double-click ubiquity.desktop.

Regards..

I know that. Both icons have to be there, when this iso goes out finally.

---

### Post by Chanath on 2017-09-24
> **ventrical said:**
> There were initially some problems with 4.13.0-11 and gdm .. or it was just gdm. (I filed a bug and posted it- didn't get much attention on both the kernel and gdm but nobody else could confirm the bug as of yet.) So there is systemd problems. gdm problems and maybe kernel problems binding gdm. I think it has to do with the way the post-boot is trying to jockey with xorg and wayland. So I think this is a growing pain and not really a big problem.

 Also thank you for your positive comments and links. I may not get to all suggestions but I am going methodically along here.

 Just a side note: I am beginning to like the gnome dock. It works smoothly on my intel base graphics boxes but there is a herkity-jerkity effect with nvidia graphics. Obviously the unity desktop is a smoother operator than most desktop experiences but it looks as though  it is getting better, however slowly, with gnome.  Perhaps a lot of this will be cleaned up during 18.04 and so I am committed to help them test.

Regards..

In this Unity7Ubuntu, gdm problems don't matter as its not there. Lightdm takes over the job, and this is just there only for login. Unity doesn't need wayland, so that jockeying problem also goes away. (Gparted is Xorg and live iso cannot do without Gparted. Xwayland is not wayland, but..well what?). We are talking about a Unity Ubuntu live installable iso that works very well with Xorg (and Gparted).

Gnome's jerky problems are there in the default Ubuntu and in Ubuntu Gnome. This is a Gnome problem. Sure, they have time till 18.04, as the LTS users won't move to a new LTS until then. But, when 17.10 comes out, the triers would shout, the websites would clamour. Anyway, that's not my problem. (Most Unity users would say the same.) 

If Unity would stay in 18.04, it would be nice. If not, one should just download all Unity related deb files to one's computer, sort of internal repo. I'm sure some have already done it.

Regards!

---

### Post by ventrical on 2017-09-24
Post installation:

I went to:

```

sudo apt-get dist-upgrade

```

and I got this.

```

ventrical@ventrical-MS-7850:~$ sudo apt-get dist-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
ventrical@ventrical-MS-7850:~$ sudo dpkg --configure -a
Setting up grub-pc (2.02~beta3-4ubuntu6) ...
Installing for i386-pc platform.
grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.13.0-11-generic
Found initrd image: /boot/initrd.img-4.13.0-11-generic
Found linux image: /boot/vmlinuz-4.12.0-12-generic
Found initrd image: /boot/initrd.img-4.12.0-12-generic
Adding boot menu entry for EFI firmware configuration
done
Processing triggers for initramfs-tools (0.125ubuntu11) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-11-generic
Setting up gconf-service (3.2.6-4ubuntu1) ...
Processing triggers for libc-bin (2.26-0ubuntu1) ...
Processing triggers for systemd (234-2ubuntu10) ...
Setting up gconf2 (3.2.6-4ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-9ubuntu2) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Processing triggers for gconf2 (3.2.6-4ubuntu1) ...
Setting up gksu (2.0.2-9ubuntu1) ...
Setting up ubiquity (17.10.7) ...
Created symlink /etc/systemd/system/graphical.target.wants/ubiquity.service &#8594; /lib/systemd/system/ubiquity.service.
Setting up ubiquity-frontend-debconf (17.10.7) ...
Setting up pinguybuilder (4.3-8) ...
Processing triggers for libc-bin (2.26-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-20) ...
ventrical@ventrical-MS-7850:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  fonts-cantarell

```

but the grub-pc option window gave me two choices .. the hdd or sda2 - so I chose sda2 and it gave me errors but it is now to  update/upgrade.


Regards..

---

### Post by Chanath on 2017-09-25
> **ventrical said:**
> Post installation:

I went to:

```

sudo apt-get dist-upgrade

```



Check your original install before creating the live iso. The problem must've come from it. What you got was a installable live iso from your install. Whatever problems that were there came through.

---

### Post by ventrical on 2017-09-25
> **Chanath said:**
> Check your original install before creating the live iso. The problem must've come from it. What you got was a installable live iso from your install. Whatever problems that were there came through.

Thats a given. As I said  I will work with a clean install during second build .  I am encouraged at how the first build went though I just want something cleaner for those who want to test it. Of course I would rather spend more time building an ISO during the 18.04 cycle but that will have to wait. If I get some stable build then I will work on unity9 for desktops. That will take some weeks . I am not declaring or committing  that I will actually have a working unity9 but if I get the time to squeeze in between testing, then I'll certainly try. If 18.04 keeps unity7 viable or in the universe and our team actually gets to maintain it then there will be time drawn away from trying to build a Unity9 system.

mac4man has posted some words of wisdom..

> 
Honestly I think you should be patient & see what transpires in 18.04..


So I  am considering all these things and considering  how to compartmentalize my time.

Again .. a big thanks to all here who have  helped me out on this.

Regards..

---

### Post by Chanath on 2017-09-25
Created a test iso through chroot from the last daily live iso and uploaded to Mega. Its 64 bit. Let me know how you find it. Its there only for testing purposes. Its called Unity7N.iso and weighs 1.29GB

Link: [https://mega.nz/#!OwFwDB4b!7_OG1GI7Jfer8WE8i58YDQpFidHC39ujvEJ-5yaRcj0](https://mega.nz/#!OwFwDB4b!7_OG1GI7Jfer8WE8i58YDQpFidHC39ujvEJ-5yaRcj0)

md5sum 9a4b29b41db59b813e9d41344fc0077d
sha256sum 97f5a5a4492e855f466df05bd85639a265a5dadf530bd56779796037caa2562e

---

### Post by ventrical on 2017-09-25
> **Chanath said:**
> Created a test iso through chroot from the last daily live iso and uploaded to Mega. Its 64 bit. Let me know how you find it. Its there only for testing purposes. Its called Unity7N.iso and weighs 1.29GB

Link: [https://mega.nz/#!OwFwDB4b!7_OG1GI7Jfer8WE8i58YDQpFidHC39ujvEJ-5yaRcj0](https://mega.nz/#!OwFwDB4b!7_OG1GI7Jfer8WE8i58YDQpFidHC39ujvEJ-5yaRcj0)

md5sum 9a4b29b41db59b813e9d41344fc0077d
sha256sum 97f5a5a4492e855f466df05bd85639a265a5dadf530bd56779796037caa2562e

I'm downloading now but it is taking too much time. It cost money to loosen up the bandwidth speed. I'll do this download but  it ties up my KVM from doing other work on the internet with my other boxes. I searched for free cloud space to upload isos to ubuntu cloud but can't find any. Sourceforge has had problems in the past. Canonical expects a high level of due dilligence and security when considering support for an off-site distro.. Just thought I would mention that. I'll be back later to report test on your iso.

Regards..

---

### Post by ventrical on 2017-09-25
I  have requested from another source if we could find another cloud service where there are not any  speed restricts adn that are safe and secure.

Regards..

---

### Post by cariboo on 2017-09-25
From what I can see, you can use[ Github]("https://github.com/") for your iso, but if it's open source, you also have to provide the source code.

---

### Post by Chanath on 2017-09-25
Thanks for downloading. I didn't download it myself, but I burned it to a usb stick and tried it in a MBR laptop and a UEFI laptop. It should boot up normally as the normal Ubuntu iso would do. Everything in it is pure Ubuntu, so uploaded where you did, to Mega.

---

### Post by ventrical on 2017-09-25
> **cariboo said:**
> From what I can see, you can use[ Github]("https://github.com/") for your iso, but if it's open source, you also have to provide the source code.

Yes.. it's repository , branch, pull etc..

 I did make an account there and will look further into it.

Thanks cariboo.

Regards..

---

### Post by Chanath on 2017-09-25
If you upload to places, where anyone can download your distro, you'd have to rebrand it.

---

### Post by ventrical on 2017-09-25
> **cariboo said:**
> From what I can see, you can use[ Github]("https://github.com/") for your iso, but if it's open source, you also have to provide the source code.

25mb limit. I tried.

---

### Post by ventrical on 2017-09-25
> **Chanath said:**
> Created a test iso through chroot from the last daily live iso and uploaded to Mega. Its 64 bit. Let me know how you find it. Its there only for testing purposes. Its called Unity7N.iso and weighs 1.29GB

Link: [https://mega.nz/#!OwFwDB4b!7_OG1GI7Jfer8WE8i58YDQpFidHC39ujvEJ-5yaRcj0](https://mega.nz/#!OwFwDB4b!7_OG1GI7Jfer8WE8i58YDQpFidHC39ujvEJ-5yaRcj0)

md5sum 9a4b29b41db59b813e9d41344fc0077d
sha256sum 97f5a5a4492e855f466df05bd85639a265a5dadf530bd56779796037caa2562e

Used disks to burn to usb.

Had verbose machine and socket errors on bootup, but finished booting. Live session ok. Installed ok but would not exit. Hard reboot. No errors. on 

```

ventrical@ventrical-Satellite-A210:~$ inxi -Fxz
System:    Host: ventrical-Satellite-A210 Kernel: 4.13.0-11-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome  (Gtk 3.22.21-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: kvm System: TOSHIBA product: Satellite A210 v: PSAFGC-MS008C serial: N/A
           Mobo: ATI model: SB600 v: Rev 1 serial: N/A
           BIOS: Phoenix v: 1.90 date: 06/02/2009
CPU:       Dual core AMD Athlon 64 X2 TK-55 (-MCP-) 
           arch: K8 rev.F+ cache: 512 KB
           flags: (lm nx sse sse2 sse3 svm) bmips: 3192
           clock speeds: max: 1800 MHz 1: 1795 MHz 2: 1795 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RS690M [Radeon Xpress 1200/1250/1270]
           bus-ID: 01:05.0
           Display Server: x11 (X.Org 1.19.3 )
           drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1280x800@60.00hz
           OpenGL: renderer: ATI RS690
           version: 2.1 Mesa 17.2.1 Direct Render: Yes
Audio:     Card Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel bus-ID: 00:14.2
           Sound: Advanced Linux Sound Architecture v: k4.13.0-11-generic
Network:   Card-1: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: a000 bus-ID: 08:00.0
           IF: enp8s0 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Realtek RTL8187B Wireless Adapter
           driver: rtl8187 usb-ID: 001-002
           IF: wlx00164469e552 state: N/A mac: N/A
Drives:    HDD Total Size: 120.0GB (5.3% used)
           ID-1: /dev/sda model: FUJITSU_MHY2120B size: 120.0GB
Partition: ID-1: / size: 110G used: 6.0G (6%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 59.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 176 Uptime: 18 min Memory: 843.4/2877.6MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.37 
ventrical@ventrical-Satellite-A210:~$ 

```

also does not use llvmpipe on radeon graphics which is a bonus.

nice work. for now..

edit:

will not shut down.. plymouth freezes, have to hard shutdown.

---

### Post by Chanath on 2017-09-25
Practically all live ubuntu and derivative isos don't exit after live session. No idea why. Installed ones do exit, except Ubuntu on wayland. If the devs know the problem, they'd correct it by the release day. If they spend more time trying to make Ubuntu mimic Unity, they won't get this done.

The iso was done from the Ubuntu live iso without installing it. Unarchived the iso, took out the filesystem.sqaushfs and unsquashed it, and then the resulting  squashfs-root edited in chroot. installed, uninstalled apps, updated, cleaned it and went out of chroot and squashed it back. Made the iso using xorriso, isohybrid it.    

Must try a Unity-jeos.iso sometime.

---

### Post by ventrical on 2017-09-26
> **Chanath said:**
> Practically all live ubuntu and derivative isos don't exit after live session. 

Must try a Unity-jeos.iso sometime.

I get good exits from live isos. There are a few cases though.

---

### Post by sunny_sigara on 2017-10-05
Hi,

Is there any plan to provide a 32 bit iso ? Thanks.

---

### Post by ventrical on 2017-10-05
> **sunny_sigara said:**
> Hi,

Is there any plan to provide a 32 bit iso ? Thanks.

Not from me. No.

Canoncial will also not be providing  32bit ISO during next cycle.

regards..

---

### Post by ventrical on 2017-10-13
@cariboo

Please move this thread to here: 
[https://ubuntuforums.org/forumdisplay.php?f=201](https://ubuntuforums.org/forumdisplay.php?f=201)

regards..

---

### Post by ventrical on 2017-10-13
Just followup. Running the two Unity7spins, one created by myself and one created by Chanath, they are both working seamlessly at the moment.  One of the bugs , which are many, is that when you eject a USB stick it will not notify that USB is safe to remove.

Regards..

---

### Post by ventrical on 2017-10-20
@cariboo,

So are we blocked out of discussion of unity7 here also?


Regards

---

### Post by ventrical on 2017-10-20
Been thinking on this. Unity9 is just too overly enthusiastic so will take Jeremy's advice and roll it back to a unity7 development.

Regards..

---

### Post by ventrical on 2017-10-20
The sticky definition is outdated and has been abandoned. [https://ubuntuforums.org/showthread.php?t=383067&p=2302520#post2302520](https://ubuntuforums.org/showthread.php?t=383067&p=2302520#post2302520)

So perhaps we can use this area as slackspace to continue to discuss  the unity iso adventure without blocking?

Regards..

---

### Post by NikTh on 2017-11-02
Hello and sorry for being a bit off-topic. 

@Vertical you have opened too many threads in too many different places for Unity 7 continuation. I'm a supporter and I want to contribute but I cannot follow so many different places for the same subject. Please, if you can, stick to one place. It really doesn't matter where, but one place. 

[Ubuntu Community Hub]("https://community.ubuntu.com") ? 
Ubuntu Forums (here) ? 
The mailing list ? 
Elsewhere ? 

It is really tiring jumping from one place to another trying to following, posting, replying in too many different places.

---

### Post by ventrical on 2017-11-05
Hi Nick,

Please accept my apologies for not getting back to you sooner. Also, if I have caused you any confusion. I had just read the comment from Khurshid about building the ISO and it is sort of news to me. I was under the impression that we were not going to immediately pursue building an ISO until perhaps in Janurary.  

As far as I can discern at the moment we can use both forums to discuss this but we cannot discuss unity7 as being an official  flavor here in these ubuntuforums echos.

Ubuntuforums is my ubuntu Home base and so I am familiar with the KB and it is an easier sandbox for me to work here. However ubuntu.com community is just as well also.

Before I continue I am awaiting  message from Khurshid as to which ISO he is speaking. There are currently 2 that I know of. One built by Chanath and one built by myself. I used pinguy app to create mine and Chanath used another method. So I will wait to hear from Khurshid and then let you know where we will go from there..

Regards..

---

