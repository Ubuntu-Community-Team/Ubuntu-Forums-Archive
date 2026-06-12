---
title: "World of Goo: cannot install on Kubuntu 12.10"
date: 2013-02-17
forum: Gaming &amp; Leisure
---

### Post by Stosskraft on 2013-02-17
Hello all, when I download the latest version from the humble bundle and double click on the deb. it says it cannot satisfy dependencies?

I am not sure that this means as WOG worked flawless of 12.04

any Ideas?

---

### Post by sanderj on 2013-02-17
> **Stosskraft said:**
> Hello all, when I download the latest version from the humble bundle and double click on the deb. it says it cannot satisfy dependencies?

I am not sure that this means as WOG worked flawless of 12.04

any Ideas?

It would help (certainly yourself) if you would mention which dependencies, and then google it. Or just fill it out in SoftwareCenter.

... talking about which: World of Goo is in the Software Center, so probably easier to install from there?

---

### Post by Perfect Storm on 2013-02-17
You can also get access to World of goo via Steam with your Humble Bundle...if everything else fails.

---

### Post by Stosskraft on 2013-02-18
Hello, It doesnt say what dependencies are missing..I am using the deb installer. I just get a red written warning that the dependencies are missing and no further information. I only want to play this game as I am not really a gamer so steam is not for me.

Thanks for the help

---

### Post by Stosskraft on 2013-02-20
Please advise, I cant even find the demo in muon or Ubuntu center

---

### Post by Perfect Storm on 2013-02-20
Do
```
sudo dpkg -i nameofpackage.deb
```

to see error output.

---

### Post by Stosskraft on 2013-02-20
yanek@yanek-HP-G42-Notebook-PC:~$ sudo dpkg -i worldofgoosetup.deb
dpkg: error processing worldofgoosetup.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 worldofgoosetup.deb


Sorry how to I specify where the deb. is? It is in the home folder

---

### Post by Perfect Storm on 2013-02-20
Are you sure it's in your home directory?
```
cd && ls -a
```

---

### Post by Stosskraft on 2013-02-20
yanek@yanek-HP-G42-Notebook-PC:~$ cd && ls -a
.                      .kderc
..                     .local
.adobe                 .macromedia
.bash_history          .mission-control
.bash_logout           Music
.bashrc                Pictures
.cache                 .pki
.config                .profile
.dbus                  .pulse
Desktop                .pulse-cookie
.dmrc                  .recently-used
Documents              .rednotebook
Downloads              .Skype
.dropbox               .synaptic
Dropbox                .thumbnails
.fonts.conf            tor-browser_en-US
.gconf                 Videos
.gnupg                 .WorldOfGoo
.goutputstream-24R7RW  WorldOfGooSetup.1.41
.goutputstream-CJLMSW  WorldOfGooSetup.1.41.deb
.gstreamer-0.10        .Xauthority
.gtkrc-2.0             .xsession-errors
.kde                   .xsession-errors.old
yanek@yanek-HP-G42-Notebook-PC:~$

---

### Post by Perfect Storm on 2013-02-21
It is not in your home directory. Are sure it is not on your Desktop or Download directory?

To change directory you can eg:
```
cd Desktop
```
or
```
cd Downloads
```

another way is to drag the package into the terminal:
Type;
```
sudo dpkg -i 
```
then drag the package into the terminal and hit enter.

---

### Post by Stosskraft on 2013-02-21
Yes I am sure it is in the home folder, I also copied it into the downloads and tried this:

yanek@yanek-HP-G42-Notebook-PC:~/Downloads$ sudo dpkg -i WorldOfGoosetup.deb
dpkg: error processing WorldOfGoosetup.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 WorldOfGoosetup.deb
yanek@yanek-HP-G42-Notebook-PC:~/Downloads$ sudo dpkg -i WorldOfGooSetup.deb
dpkg: error processing WorldOfGooSetup.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 WorldOfGooSetup.deb
yanek@yanek-HP-G42-Notebook-PC:~/Downloads$ ^C
yanek@yanek-HP-G42-Notebook-PC:~/Downloads$ 

This is a fresh torrent download from my humble bundle, I am still not sure what dependencies they are looking for,

Thank you

---

### Post by Perfect Storm on 2013-02-21
It's not dependencies, it's complaing that something is missing in the package itself.
Try redownload it, but direct link instead.

---

### Post by Stosskraft on 2013-02-21
I have tried that also. I also tried to download through the ubuntu software center and am getting this pop up:

The package is of bad quality
The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.

Lintian check results for /home/yanek/Downloads/WorldOfGooSetup.1.41.deb:
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/WorldOfGoo.bin32
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/WorldOfGoo.bin64
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/libs32/libSDL-1.2.so.0
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/libs32/libSDL_mixer-1.2.so.0
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/libs32/libogg.so.0
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/libs32/libvorbis.so.0
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/libs32/libvorbisfile.so.3
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/libs64/libSDL-1.2.so.0
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/libs64/libSDL_mixer-1.2.so.0
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/libs64/libogg.so.0
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/libs64/libvorbis.so.0
E: WorldOfGoo: arch-independent-package-contains-binary-or-object opt/WorldOfGoo/libs64/libvorbisfile.so.3
E: WorldOfGoo: bad-package-name
E: WorldOfGoo: package-not-lowercase

I click install anyway and something happens. Now I see worldof goo in my games folder but when I try to play it does not load.

?

---

### Post by Perfect Storm on 2013-02-22
Go to the World of Goo folder and launch the binary from there.

opt/WorldOfGoo/WorldOfGoo.bin32
opt/WorldOfGoo/WorldOfGoo.bin64

---

### Post by Stosskraft on 2013-02-22
I keep getting this: KDEInit could not launch '/opt/WorldOfGoo/WorldOfGoo'

I give up

---

### Post by Perfect Storm on 2013-02-22
May be it's a bug in KDE?

---

### Post by Stosskraft on 2013-02-22
I would go with that. I find 12.10 a lot more buggy than 12.04.. I might switch back

---

