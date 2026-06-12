---
title: "PCSX2 Install issues"
date: 2015-11-12
forum: Emulators
---

### Post by Ralthor on 2015-11-12
Hi,

Trying to install PCSX2 but running into dependency issues. Running 64 bit 14.04

sudo apt-get install pcsx2 returns 

```

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

I did consider: 
sudo apt-get install  libglew-dev libcheese7 libcheese-gtk23 libclutter-gst-2.0-0 libcogl15 libclutter-gtk-1.0-0 libclutter-1.0-0  xserver-xorg-input-all

But when it said it was going to uninstall 39 packages I decided discretion was the better part of valor.

Any help appreciated.

---

### Post by deadflowr on 2015-11-13
How are you trying to install it?
Which ppa.

 pcsx2 is not in the default repos for 14.04; it only came to the repos in 15.10

Note you might need to run a full system update to ensure your system's packages and the repos packages match.

---

### Post by Ralthor on 2015-11-30
Thanks for the suggestion and sorry for being so slow to reply. I never subscribed to thread and missed reply when browsing. 

Anyhow, I aded  gregory-hainaut/pcsx2.official.ppa - and attempted to install via apt-get

system update? apt-get update? If so, done.

---

### Post by deadflowr on 2015-12-01
> [COLOR=#000000]system update? apt-get update? If so, done.[/COLOR]
system update and apt-get update do two different things.
apt-get update does not update the system.
It only updates the list of available packages the system can see.

To actually apply those newly found updated packages, you need to run
either
```
sudo apt-get upgrade
```
this updates packages safely, meaning it won't install  any new packages, if the updates require those.
or
```
sudo apt-get dist-upgrade
```
this will update all packages including install new packages if the system requires that.


Or,
You can ignore the above if you already know this.

---

### Post by Ralthor on 2015-12-01
OK, reasonably sure I had tried sudo apt-get upgrade in  my struggles with installing something else so skipped straight to: 

sudo apt-get dist-upgrade - Which updated 10 packages, mostly seemed to be nautilus related. 

I had removed the repository so added it back in again and retried: Same dependency errors.

---

### Post by deadflowr on 2015-12-01
weird, definitely weird.
You don't have any other ppa's installed?

---

### Post by Ralthor on 2015-12-01
apt-cache policy > ppa.txt

```
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-yannubuntu-boot-repair,a=trusty,n=trusty,l=Boot-Repair,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-yannubuntu-boot-repair,a=trusty,n=trusty,l=Boot-Repair,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-webupd8team-tor-browser,a=trusty,n=trusty,l=Tor Browser Bundle,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-webupd8team-tor-browser,a=trusty,n=trusty,l=Tor Browser Bundle,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/webupd8team/java/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/webupd8team/java/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-webupd8team-java,a=trusty,n=trusty,l=Oracle Java (JDK) 7 / 8 / 9 Installer PPA,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/webupd8team/java/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-webupd8team-java,a=trusty,n=trusty,l=Oracle Java (JDK) 7 / 8 / 9 Installer PPA,c=main
     origin ppa.launchpad.net
 500 http://download.virtualbox.org/virtualbox/debian/ trusty/contrib i386 Packages
     release o=Oracle Corporation,n=trusty,l=Oracle Corporation,c=contrib
     origin download.virtualbox.org
 500 http://download.virtualbox.org/virtualbox/debian/ trusty/contrib amd64 Packages
     release o=Oracle Corporation,n=trusty,l=Oracle Corporation,c=contrib
     origin download.virtualbox.org
 500 http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-tualatrix,a=trusty,n=trusty,l=Ubuntu Tweak Stable PPA,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-tualatrix,a=trusty,n=trusty,l=Ubuntu Tweak Stable PPA,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-team-xbmc,a=trusty,n=trusty,l=Kodi stable,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-team-xbmc,a=trusty,n=trusty,l=Kodi stable,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/screenlets/ppa/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-screenlets,a=trusty,n=trusty,l=Screenlets PPA,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/screenlets/ppa/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-screenlets,a=trusty,n=trusty,l=Screenlets PPA,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/rael-gc/ubuntu-xboxdrv/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/rael-gc/ubuntu-xboxdrv/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-rael-gc-ubuntu-xboxdrv,a=trusty,n=trusty,l=Ubuntu xboxdrv Integration,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/rael-gc/ubuntu-xboxdrv/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-rael-gc-ubuntu-xboxdrv,a=trusty,n=trusty,l=Ubuntu xboxdrv Integration,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-qbittorrent-team-qbittorrent-stable,a=trusty,n=trusty,l=qbittorrent-stable,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-qbittorrent-team-qbittorrent-stable,a=trusty,n=trusty,l=qbittorrent-stable,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/pipelight/stable/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/pipelight/stable/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-pipelight-stable,a=trusty,n=trusty,l=pipelight-stable,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/pipelight/stable/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-pipelight-stable,a=trusty,n=trusty,l=pipelight-stable,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-notepadqq-team-notepadqq,a=trusty,n=trusty,l=Notepadqq,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-notepadqq-team-notepadqq,a=trusty,n=trusty,l=Notepadqq,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/noobslab/themes/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/noobslab/themes/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-noobslab-themes,a=trusty,n=trusty,l=Themes Collection by NoobsLab,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/noobslab/themes/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-noobslab-themes,a=trusty,n=trusty,l=Themes Collection by NoobsLab,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/mdeslaur/steamos/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/mdeslaur/steamos/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-mdeslaur-steamos,a=trusty,n=trusty,l=SteamOS,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/mdeslaur/steamos/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-mdeslaur-steamos,a=trusty,n=trusty,l=SteamOS,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-ian-berke-ppa-drawers,a=trusty,n=trusty,l=Drawers,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-ian-berke-ppa-drawers,a=trusty,n=trusty,l=Drawers,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-gregory-hainaut-pcsx2.official.ppa,a=trusty,n=trusty,l=official ppa for pcsx2 team,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-gregory-hainaut-pcsx2.official.ppa,a=trusty,n=trusty,l=official ppa for pcsx2 team,c=main
     origin ppa.launchpad.net
 500 http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages
     release v=1.0,o=Google, Inc.,a=stable,n=stable,l=Google,c=main
     origin dl.google.com
 500 http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages
     release v=1.0,o=Google, Inc.,a=stable,n=stable,l=Google,c=main
     origin dl.google.com
 500 http://archive.getdeb.net/ubuntu/ trusty-getdeb/apps i386 Packages
     release v=14.04,o=GetDeb,a=trusty-getdeb,n=trusty-getdeb,l=GetDeb,c=apps
     origin archive.getdeb.net
 500 http://archive.getdeb.net/ubuntu/ trusty-getdeb/apps amd64 Packages
     release v=14.04,o=GetDeb,a=trusty-getdeb,n=trusty-getdeb,l=GetDeb,c=apps
     origin archive.getdeb.net
 500 http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-caffeine-developers,a=trusty,n=trusty,l=Caffeine,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-caffeine-developers,a=trusty,n=trusty,l=Caffeine,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/atareao/atareao/ubuntu/ trusty/main Translation-en
 500 http://ppa.launchpad.net/atareao/atareao/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-atareao-atareao,a=trusty,n=trusty,l=atareao-team,c=main
     origin ppa.launchpad.net
 500 http://ppa.launchpad.net/atareao/atareao/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-atareao-atareao,a=trusty,n=trusty,l=atareao-team,c=main
     origin ppa.launchpad.net
 500 http://deb.playonlinux.com/ precise/main i386 Packages
     release v=12.04,o=PlayOnLinux,a=precise,n=precise,l=PoL,c=main
     origin deb.playonlinux.com
 500 http://deb.playonlinux.com/ precise/main amd64 Packages
     release v=12.04,o=PlayOnLinux,a=precise,n=precise,l=PoL,c=main
     origin deb.playonlinux.com
 500 http://repository.spotify.com/ stable/non-free i386 Packages
     release v=0.4,o=Spotify LTD,a=stable,n=stable,l=Spotify Public Repository,c=non-free
     origin repository.spotify.com
 500 http://repository.spotify.com/ stable/non-free amd64 Packages
     release v=0.4,o=Spotify LTD,a=stable,n=stable,l=Spotify Public Repository,c=non-free
     origin repository.spotify.com
 500 http://linux.dropbox.com/ubuntu/ trusty/main i386 Packages
     release o=Dropbox.com,a=trusty,n=trusty,l=Dropbox Ubuntu Repository,c=main
     origin linux.dropbox.com
 500 http://linux.dropbox.com/ubuntu/ trusty/main amd64 Packages
     release o=Dropbox.com,a=trusty,n=trusty,l=Dropbox Ubuntu Repository,c=main
     origin linux.dropbox.com
 500 http://extras.ubuntu.com/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=LP-PPA-app-review-board,a=trusty,n=trusty,l=Application Review Board PPA,c=main
     origin extras.ubuntu.com
 500 http://extras.ubuntu.com/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=LP-PPA-app-review-board,a=trusty,n=trusty,l=Application Review Board PPA,c=main
     origin extras.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ trusty-security/universe Translation-en
 500 http://security.ubuntu.com/ubuntu/ trusty-security/restricted Translation-en
 500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse Translation-en
 500 http://security.ubuntu.com/ubuntu/ trusty-security/main Translation-en
 500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-security,n=trusty,l=Ubuntu,c=multiverse
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ trusty-security/universe i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-security,n=trusty,l=Ubuntu,c=universe
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ trusty-security/restricted i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-security,n=trusty,l=Ubuntu,c=restricted
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ trusty-security/main i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-security,n=trusty,l=Ubuntu,c=main
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-security,n=trusty,l=Ubuntu,c=multiverse
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-security,n=trusty,l=Ubuntu,c=universe
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ trusty-security/restricted amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-security,n=trusty,l=Ubuntu,c=restricted
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-security,n=trusty,l=Ubuntu,c=main
     origin security.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/universe Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/restricted Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/multiverse Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/main Translation-en
 100 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/multiverse i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-backports,n=trusty,l=Ubuntu,c=multiverse
     origin ie.archive.ubuntu.com
 100 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/universe i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-backports,n=trusty,l=Ubuntu,c=universe
     origin ie.archive.ubuntu.com
 100 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/restricted i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-backports,n=trusty,l=Ubuntu,c=restricted
     origin ie.archive.ubuntu.com
 100 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/main i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-backports,n=trusty,l=Ubuntu,c=main
     origin ie.archive.ubuntu.com
 100 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/multiverse amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-backports,n=trusty,l=Ubuntu,c=multiverse
     origin ie.archive.ubuntu.com
 100 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/universe amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-backports,n=trusty,l=Ubuntu,c=universe
     origin ie.archive.ubuntu.com
 100 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/restricted amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-backports,n=trusty,l=Ubuntu,c=restricted
     origin ie.archive.ubuntu.com
 100 http://ie.archive.ubuntu.com/ubuntu/ trusty-backports/main amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-backports,n=trusty,l=Ubuntu,c=main
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/universe Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/restricted Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/main Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-updates,n=trusty,l=Ubuntu,c=multiverse
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/universe i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-updates,n=trusty,l=Ubuntu,c=universe
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/restricted i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-updates,n=trusty,l=Ubuntu,c=restricted
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
     release v=14.04,o=Ubuntu,a=trusty-updates,n=trusty,l=Ubuntu,c=main
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-updates,n=trusty,l=Ubuntu,c=multiverse
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-updates,n=trusty,l=Ubuntu,c=universe
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/restricted amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-updates,n=trusty,l=Ubuntu,c=restricted
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty-updates,n=trusty,l=Ubuntu,c=main
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/universe Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/restricted Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/multiverse Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/main Translation-en
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/multiverse i386 Packages
     release v=14.04,o=Ubuntu,a=trusty,n=trusty,l=Ubuntu,c=multiverse
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
     release v=14.04,o=Ubuntu,a=trusty,n=trusty,l=Ubuntu,c=universe
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/restricted i386 Packages
     release v=14.04,o=Ubuntu,a=trusty,n=trusty,l=Ubuntu,c=restricted
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
     release v=14.04,o=Ubuntu,a=trusty,n=trusty,l=Ubuntu,c=main
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty,n=trusty,l=Ubuntu,c=multiverse
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty,n=trusty,l=Ubuntu,c=universe
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/restricted amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty,n=trusty,l=Ubuntu,c=restricted
     origin ie.archive.ubuntu.com
 500 http://ie.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
     release v=14.04,o=Ubuntu,a=trusty,n=trusty,l=Ubuntu,c=main
     origin ie.archive.ubuntu.com
Pinned packages:
```

So, one or two. :P

This is a fairly mature installation, i.e. I now have all hardware working properly (inc my tv cards - they were hard!) and very nearly all software I want installed and working. Something I have installed along the way requires a very specific version of libclutter and has locked it in some way is what I am guessing, but I have no idea how to figure out what.

---

### Post by deadflowr on 2015-12-04
Yeah is a lot.
Perhaps running a quick apt-cache policy against each of the problem-listed packages might shed some light.

For what it's worth I installed the ppa and pcsx2 without any problems.
But I have no where no the ppa numbers (I only have 6, currently, including the pcsx2 ppa)

Note this other user is having a similar problem, something odd about the libcheese-gtk23/ libcheese7 packages.
[http://ubuntuforums.org/showthread.php?t=2302676](http://ubuntuforums.org/showthread.php?t=2302676)

---

