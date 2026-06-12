---
title: "no updates"
date: 2006-09-16
forum: Desktop Environments
---

### Post by ilyaostr on 2006-09-16
i cant get the updates, neither through the GUI, nor through sudo apt-get update and sudo apt-get upgrades, it says that it can tconnect to the update server, heres the result

[QUOTE=aptget updates]ilyaostr9@edubuntu:~$ sudo apt-get update
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg
  Connection failed
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.23 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/Release.gpg](http://www.getautomatix.com/apt/dists/dapper/Release.gpg)  Connection failed
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.23 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/QUOTE]





I am on Edubuntu 6.06 LTS searching didnt work, help plz](*,) ](*,)

---

### Post by ilyaostr on 2006-09-16
Part 2:


apt-get upgrade
[QUOTE=aptget upgrade]
ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main desktop-file-utils 0.10-1ubuntu13
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-control-center 1:2.14.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main capplets-data 1:2.14.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libcupsys2 1.2.2-0ubuntu0.6.06
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libcupsimage2 1.2.2-0ubuntu0.6.06
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main cupsys 1.2.2-0ubuntu0.6.06
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main cupsys-bsd 1.2.2-0ubuntu0.6.06
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main cupsys-client 1.2.2-0ubuntu0.6.06
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main deskbar-applet 2.14.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libgnomecups1.0-1 0.2.2-1ubuntu5.1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libgnomeprint2.2-0 2.12.1-3ubuntu2
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libgnomeprint2.2-data 2.12.1-3ubuntu2
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main eog 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main evince 0.5.2-0ubuntu3
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main file-roller 2.14.4-0ubuntu1  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-session 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main metacity 1:2.14.5-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libvte4 1:0.12.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libvte-common 1:0.12.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-terminal 2.14.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-terminal-data 2.14.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gdm 2.14.10-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libgtksourceview-common 1.6.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libgtksourceview1.0-0 1.6.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gedit 2.14.4-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gedit-common 2.14.4-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-about 2.14.3-0ubuntu1  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-highcontrast 1:2.7.4.is.2.6.10-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-accessibility-themes 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-app-install 0.1.33
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libpanel-applet2-0 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libwnck-common 2.14.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libwnck18 2.14.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-applets 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-applets-data 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-panel 2.14.3-0ubuntu1  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-panel-data 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gstreamer0.10-alsa 0.10.7-0ubuntu5
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-games 1:2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-games-data 1:2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libnautilus-burn3 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gstreamer0.10-plugins-base 0.10.7-0ubuntu5
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-media 2.14.2-0ubuntu1  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-screensaver 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-pixbuf 2.8.20-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-thinice 1:2.7.4.is.2.6.10-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-crux 1:2.7.4.is.2.6.10-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-redmond95 1:2.7.4.is.2.6.10-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-lighthouseblue 1:2.7.4.is.2.6.10-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-smooth 1:2.7.4.is.2.6.10-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-mist 1:2.7.4.is.2.6.10-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-clearlooks 1:2.7.4.is.2.6.10-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-themes 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gstreamer0.10-plugins-base-apps 0.10.7-0ubuntu5
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtk2-engines-industrial 1:2.7.4.is.2.6.10-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main language-selector 0.1.20.1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main language-selector-common 0.1.20.1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libgnomevfs2-bin 2.14.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libeel2-2 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libeel2-data 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main nautilus-data 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main nautilus 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main nautilus-cd-burner 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main python2.4-pyorbit 2.14.1-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main python-pyorbit 2.14.1-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gstreamer0.10-gnomevfs 0.10.7-0ubuntu5
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main sound-juicer 2.14.4-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libtotem-plparser1 1.4.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gstreamer0.10-x 0.10.7-0ubuntu5
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main totem-gstreamer 1.4.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main totem 1.4.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main ubuntu-docs 6.06.2
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gnome-doc-utils 0.6.1-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main yelp 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main zenity 2.14.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main edubuntu-desktop 0.81
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libgtkhtml3.8-15 3.10.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main gtkhtml3.8 3.10.3-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libqt3-mt 3:3.3.6-1ubuntu6
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libsoup2.2-8 2.2.93-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main python-vte 1:0.12.2-0ubuntu1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main xserver-xorg-core 1:1.0.2-0ubuntu10.4
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main xserver-xorg-input-mouse 1:1.0.3.1+cvs.20060109-0ubuntu1.1
  Connection failed [IP: 195.248.90.23 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main pcmcia-cs 3.2.8-5.2ubuntu7
  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060725_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060725_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_6.06+20060725_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_6.06+20060725_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.4.8-3ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.4.8-3ubuntu1.1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_0.120_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_0.120_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-standard_0.120_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-standard_0.120_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/acpi-support/acpi-support_0.85_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/acpi-support/acpi-support_0.85_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/app-install-data_0.1.33_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_5_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.10.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.10.3-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.10.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.10.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-extra_2.14.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-extra_2.14.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.11-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.11-1ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-0_2.14.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-0_2.14.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-common_2.14.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-common_2.14.2-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.8.20-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.8.20-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.12.3-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.12.3-0ubuntu3_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.12.3-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.12.3-0ubuntu3_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.8.20-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.8.20-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.20-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.20-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeui/libgnomeui-0_2.14.1-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeui/libgnomeui-0_2.14.1-0ubuntu3_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeui/libgnomeui-common_2.14.1-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeui/libgnomeui-common_2.14.1-0ubuntu3_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/libgnome-menu2_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/libgnome-menu2_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/libgstreamer-plugins-base0.10-0_0.10.7-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/libgstreamer-plugins-base0.10-0_0.10.7-0ubuntu5_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/libmetacity0_2.14.5-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/libmetacity0_2.14.5-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/python-gmenu_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/python-gmenu_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/gnome-menus_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/gnome-menus_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.14.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.14.3-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/desktop-file-utils/desktop-file-utils_0.10-1ubuntu13_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/desktop-file-utils/desktop-file-utils_0.10-1ubuntu13_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/gnome-control-center_2.14.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/gnome-control-center_2.14.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/capplets-data_2.14.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/control-center/capplets-data_2.14.2-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.2-0ubuntu0.6.06_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.2-0ubuntu0.6.06_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.2-0ubuntu0.6.06_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.2-0ubuntu0.6.06_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.2-0ubuntu0.6.06_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.2-0ubuntu0.6.06_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.2-0ubuntu0.6.06_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.2-0ubuntu0.6.06_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.2-0ubuntu0.6.06_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.2-0ubuntu0.6.06_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.14.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.14.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecups/libgnomecups1.0-1_0.2.2-1ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecups/libgnomecups1.0-1_0.2.2-1ubuntu5.1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprint/libgnomeprint2.2-0_2.12.1-3ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprint/libgnomeprint2.2-0_2.12.1-3ubuntu2_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprint/libgnomeprint2.2-data_2.12.1-3ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprint/libgnomeprint2.2-data_2.12.1-3ubuntu2_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/eog/eog_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/eog/eog_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_0.5.2-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_0.5.2-0ubuntu3_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/file-roller/file-roller_2.14.4-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/file-roller/file-roller_2.14.4-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-session/gnome-session_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-session/gnome-session_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity_2.14.5-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity_2.14.5-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte4_0.12.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte4_0.12.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.12.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.12.2-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal_2.14.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal_2.14.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal-data_2.14.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal-data_2.14.2-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.14.10-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.14.10-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtksourceview/libgtksourceview-common_1.6.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtksourceview/libgtksourceview-common_1.6.2-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtksourceview/libgtksourceview1.0-0_1.6.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtksourceview/libgtksourceview1.0-0_1.6.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit_2.14.4-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit_2.14.4-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit-common_2.14.4-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit-common_2.14.4-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-highcontrast_2.7.4.is.2.6.10-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-highcontrast_2.7.4.is.2.6.10-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-themes/gnome-accessibility-themes_2.14.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-themes/gnome-accessibility-themes_2.14.3-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.1.33_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.1.33_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck-common_2.14.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck-common_2.14.2-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck18_2.14.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck18_2.14.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.14.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.14.3-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.14.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.14.3-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-alsa_0.10.7-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-alsa_0.10.7-0ubuntu5_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.14.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.14.3-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus-cd-burner/libnautilus-burn3_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus-cd-burner/libnautilus-burn3_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base_0.10.7-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base_0.10.7-0ubuntu5_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-media/gnome-media_2.14.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-media/gnome-media_2.14.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.8.20-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.8.20-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-thinice_2.7.4.is.2.6.10-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-thinice_2.7.4.is.2.6.10-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-crux_2.7.4.is.2.6.10-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-crux_2.7.4.is.2.6.10-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-redmond95_2.7.4.is.2.6.10-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-redmond95_2.7.4.is.2.6.10-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-lighthouseblue_2.7.4.is.2.6.10-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-lighthouseblue_2.7.4.is.2.6.10-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-smooth_2.7.4.is.2.6.10-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-smooth_2.7.4.is.2.6.10-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-mist_2.7.4.is.2.6.10-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-mist_2.7.4.is.2.6.10-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-clearlooks_2.7.4.is.2.6.10-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-clearlooks_2.7.4.is.2.6.10-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-themes/gnome-themes_2.14.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-themes/gnome-themes_2.14.3-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base-apps_0.10.7-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base-apps_0.10.7-0ubuntu5_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-industrial_2.7.4.is.2.6.10-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines-industrial_2.7.4.is.2.6.10-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.1.20.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.1.20.1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.1.20.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.1.20.1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-bin_2.14.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-bin_2.14.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/eel2/libeel2-2_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/eel2/libeel2-2_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/eel2/libeel2-data_2.14.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/eel2/libeel2-data_2.14.3-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.14.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.14.3-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus-cd-burner/nautilus-cd-burner_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus-cd-burner/nautilus-cd-burner_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyorbit/python2.4-pyorbit_2.14.1-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyorbit/python2.4-pyorbit_2.14.1-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyorbit/python-pyorbit_2.14.1-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pyorbit/python-pyorbit_2.14.1-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-gnomevfs_0.10.7-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-gnomevfs_0.10.7-0ubuntu5_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sound-juicer/sound-juicer_2.14.4-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sound-juicer/sound-juicer_2.14.4-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_1.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_1.4.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-x_0.10.7-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-x_0.10.7-0ubuntu5_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_1.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_1.4.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_1.4.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_1.4.3-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_6.06.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_6.06.2_all.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-doc-utils/gnome-doc-utils_0.6.1-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-doc-utils/gnome-doc-utils_0.6.1-0ubuntu1_all.deb)  Connection failed [IP: 195.248.90.23 80]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/y/yelp/yelp_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/y/yelp/yelp_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/z/zenity/zenity_2.14.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/z/zenity/zenity_2.14.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/edubuntu-meta/edubuntu-desktop_0.81_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/edubuntu-meta/edubuntu-desktop_0.81_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.8/libgtkhtml3.8-15_3.10.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.8/libgtkhtml3.8-15_3.10.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.8/gtkhtml3.8_3.10.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.8/gtkhtml3.8_3.10.3-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-1ubuntu6_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsoup/libsoup2.2-8_2.2.93-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsoup/libsoup2.2-8_2.2.93-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/python-vte_0.12.2-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/python-vte_0.12.2-0ubuntu1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-mouse/xserver-xorg-input-mouse_1.0.3.1+cvs.20060109-0ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-mouse/xserver-xorg-input-mouse_1.0.3.1+cvs.20060109-0ubuntu1.1_i386.deb)  Connection failed [IP: 195.248.90.23 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcmcia-cs/pcmcia-cs_3.2.8-5.2ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pcmcia-cs/pcmcia-cs_3.2.8-5.2ubuntu7_i386.deb)  Connection failed [IP: 195.248.90.23 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/QUOTE]

---

### Post by ilyaostr on 2006-09-16
omg somebody help please i need these!!!!!!!!!!!!!!!

---

### Post by ilyaostr on 2006-09-16
bump bump help!!!

---

### Post by ilyaostr on 2006-09-17
omg is this how you treat your users?

---

### Post by DoktorSeven on 2006-09-17
For starters, can you access the Internet at all with Ubuntu?  Can you access [http://yahoo.com](http://yahoo.com) with a web browser? Can you access [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) with a web browser?  

Dumb questions to start out with, I know, but apt not being able to access the Ubuntu update servers is a bit unusual, and points to some sort of network misconfiguration...

---

### Post by ilyaostr on 2006-09-17
yes, i can access all internet with ubuntu except for the updates through the shell and through the terminal, same thing happens when i try to install anything, whether its automatix nor java

---

### Post by DoktorSeven on 2006-09-17
Certainly an odd issue.  Do you have to set a proxy server for your web browser, or something like that?  

Beyond that, I don't know.  Anyone else?

---

### Post by ilyaostr on 2006-09-17
no proxy, no anything, i am behind a router, but that has nothing to d with it since it all goes through port 80


if you need more info

Dell Dimension 8100
1500Mhz CPU
60G HD - 10G's for ubuntu
Dual Boot with windows 2000 Pro

---

### Post by hk_2999 on 2006-09-17
> *i cant get the updates, neither through the GUI, nor through sudo apt-get update and sudo apt-get upgrades, it says that it can tconnect to the update server, heres the result.*

Maybe you should try again and see if maybe the server is just down the last time you fetched, or try changing servers.

And double-check for firewalls, They're tricky.

Anyway, if it still doesn't work, try using synaptic and update there.

---

### Post by ilyaostr on 2006-09-17
the thing is i tried reinstalling ubuntu several times

first time was regular ubuntu, the other was kbununtu, and now edubuntu

---

### Post by ilyaostr on 2006-09-17
nothing works for me.

why does ubuntu hate me so much????

---

### Post by karamba_kid on 2006-09-17
Can you ping google.com? If you can try traceroute 195.248.90.23 and see if that goes all the way through.

---

### Post by ilyaostr on 2006-09-17
i can ping from the terminal, but how do i traceroute

---

### Post by karamba_kid on 2006-09-17
The command is traceroute.  I don't think it's included by default (try man traceroute) so since your having trouble using apt-get it would be difficult to install that way if you don't have it already.  If you have your CD you could install it from there. BUT if you can ping that  ubuntu IP it basically verifies the same exact thing so your problem is somewhere else.  What do you have in /etc/apt/apt.conf?  My apt.conf looks like 

~$ cat /etc/apt/apt.conf
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";

and the permissions are

~$ ls -l /etc/apt/apt.conf
-rw-r--r-- 1 root root 70 2006-08-11 01:44 /etc/apt/apt.conf

---

### Post by ilyaostr on 2006-09-17
ilyaostr9@edubuntu:~$ cat /etc/apt/apt.conf
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";


ilyaostr9@edubuntu:~$ ls -l /etc/apt/apt.conf
-rw-r--r-- 1 root root 70 2006-09-16 13:44 /etc/apt/apt.conf

---

### Post by karamba_kid on 2006-09-17
I'm hoping somebody else can tell you what's up, because I'm all out of ideas. sorry. :(

---

### Post by ilyaostr on 2006-09-17
you think you can pm mea a copy of your thing

p.s. cherck your pms

---

### Post by ilyaostr on 2006-09-18
ok this isnt working so somw elsw help

---

