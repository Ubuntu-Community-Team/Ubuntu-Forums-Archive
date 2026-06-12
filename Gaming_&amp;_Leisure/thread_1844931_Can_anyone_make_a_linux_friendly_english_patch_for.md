---
title: "Can anyone make a linux friendly english patch for Kanon"
date: 2011-09-16
forum: Gaming &amp; Leisure
---

### Post by TheManno1 on 2011-09-16
This is all you have to do [http://www.elliotglaysher.org/rlvm/guide_kanon_eng.html](http://www.elliotglaysher.org/rlvm/guide_kanon_eng.html)

---

### Post by TheManno1 on 2011-09-17
I can't seem to do it myself can anyone read the instructions an do it.

---

### Post by Perfect Storm on 2011-09-18
First, you need to install P7, open the terminal or search ubuntu software center for it:
```
sudo apt-get install p7zip-full
```


Next, You need to copy the content from your CD first. Make a new directory in your home directory called Kanon-eng and copy the CD into it. 

Now download Non-directional Translations to your home directory.
Then Download the patch to your home directory.

Open the terminal and type:

```
cd
7z x Kanon.7z
./patch-kanon-en-ndt.sh ~/Patch*files ~/Kanon-eng
```

---

### Post by TheManno1 on 2011-09-21
Usage: patch-kanon-en-ndt.sh </path/to/PatchFiles/> </path/to/KanonInstall>

  Installs NDT's English Kanon patch on the Mac or Linux.

  ERROR: Second argument does not appear to be Kanon: Standard Edition.

---

### Post by Perfect Storm on 2011-09-21
Please post the whole in/output from the terminal.

---

### Post by TheManno1 on 2011-09-22
family@ubuntu:~$ ./patch-kanon-en-ndt.sh ~/Patch*files ~/Kanon-eng
Usage: patch-kanon-en-ndt.sh </path/to/PatchFiles/> </path/to/KanonInstall>

  Installs NDT's English Kanon patch on the Mac or Linux.

  ERROR: Second argument does not appear to be Kanon: Standard Edition.

---

### Post by Perfect Storm on 2011-09-22
```
cd
ls -a
```

---

### Post by TheManno1 on 2011-09-22
family@ubuntu:~$ ls -a
** .                    Kanon.eng**
..                    .Kega Fusion
.acetoneiso                kl.png
.adobe                    lastlog.txt
.audacity-data                .libreoffice
.azureus                .local
Azureus Downloads            loghistory.txt
.bash_history                .macromedia
.blender                .miro
Bloo.blend                .mozilla
Bloo.blend1                .mtab.fuseiso
Bloo.blend2                Music
Braid                    My eSnips Downloads
.cache                    My Games
coco.py                    .nautilus
.compiz                    **Patch files**
**.config                    patch-kanon-en-ndt.sh**
DarkTabler(Eng).exe            .pcsx
DarkTabler(Eng).exe.manifest        Pictures
.dbus                    .pki
Desktop                    .PlayOnLinux
.dmrc                    Public
Documents                .pulse
Downloads                .pulse-cookie
DraftSight                qBT_dir
DraftSight.deb                .qjoypad3
dwhelper                .qt
.eclipse                Saves
Emulators                .shotwell
.esd_auth                .snes9x
examples.desktop            SOFTWARE
.extcalc                Stuff
.fceux                    .subversion
.fltk                    .sudo_as_admin_successful
.fontconfig                TaBuLar.exe
freedroid.1                Templates
.furiusisomount                temporal
Games                    .themes
.gconf                    .thumbnails
.gconfd                    .thunderbird
getlibs-all.deb                tmp
.gimp-2.7                .tor
.gksu.lock                Ubuntu One
.gnome2                    untitled.blend
.gnome2_private                untitled.blend1
.gnupg                    untitled.blend2
.googleearth                usr
.gstreamer-0.10                var
.gtk-bookmarks                Veoh
.gvfs                    .vidalia
.ICEauthority                Videos
.icedtea                virtual-drives
.icons                    VisualBoyAdvance.cfg
.idlerc                    WA
index.html                .wine
index.html.1                winetricks
install_flashplayer10_chra_aih.exe  workspace
.java                    .xsession-errors
** Kanon-eng                 .xsession-errors.old**

---

### Post by Perfect Storm on 2011-09-22
The patch files doesn't seems to be in your home directory. Make sure it is.

---

### Post by TheManno1 on 2011-09-22
Here is a better one

family@ubuntu:~$ ls -a
.                  .gksu.lock         .PlayOnLinux
..                  .gnome2             Public
.acetoneiso              .gnome2_private         .pulse
.adobe                  .gnupg             .pulse-cookie
.audacity-data              .googleearth         qBT_dir
.azureus              .gstreamer-0.10         .qjoypad3
Azureus Downloads          .gtk-bookmarks         .qt
.bash_history              .gvfs             Saves
.blender              .ICEauthority         .shotwell
.cache                  .icedtea             .snes9x
coco.py                  .icons             SOFTWARE
.compiz                  .idlerc             Stuff
.config                  index.html         .subversion
DarkTabler(Eng).exe.manifest  index.html.1         .sudo_as_admin_successful
.dbus                  .java             Templates
Desktop **                 Kanon-eng**          temporal
.dmrc                  **Kanon.eng**             .themes
Documents              .Kega Fusion         .thumbnails
Downloads              lastlog.txt         .thunderbird
DraftSight              .libreoffice         tmp
dwhelper              .local             .tor
.eclipse              loghistory.txt         Ubuntu One
Emulators              .macromedia         usr
.esd_auth              .miro             var
examples.desktop          .mozilla             Veoh
.extcalc              .mtab.fuseiso         .vidalia
.fceux                  Music             Videos
.fltk                  My eSnips Downloads    virtual-drives
.fontconfig              My Games             VisualBoyAdvance.cfg
freedroid.1              .nautilus             WA
.furiusisomount**              Patch files**         .wine
Games **                 patch-kanon-en-ndt.sh**  winetricks
.gconf                  .pcsx             workspace
.gconfd                  Pictures             .xsession-errors
.gimp-2.7              .pki             .xsession-errors.old

---

### Post by TheManno1 on 2011-09-22
Here is the content of the patch files

family@ubuntu:~/Patch files$ ls
1.2.6.8.map        G00         readme.txt         seen.txt
All Ages        gameexe.ini  reallive-patch.exe  SYS
DejaVuSansMono.ttf  License.txt  rlBabel.dll


And Kanon

anm         directx       dxset.exe    Kanon.ico      Seen.txt   sys
Autorun.inf  dsetup16.dll  g00        Kanon_se_all.env  Setup.bmp  test
bgm         dsetup32.dll  Gameexe.ini    pdt          setup.exe  wav
dat         dsetup.dll    gan        RealLive.exe      Setup.ini

---

### Post by TheManno1 on 2011-09-23
Everything seems right so why isn't it working.

---

### Post by Perfect Storm on 2011-09-23
The error says it's not the Standard version you have.

> ERROR: Second argument does not appear to be Kanon: Standard Edition.

---

