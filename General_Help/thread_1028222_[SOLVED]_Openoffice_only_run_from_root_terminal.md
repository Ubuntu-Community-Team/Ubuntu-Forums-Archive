---
title: "[SOLVED] Openoffice only run from root terminal"
date: 2009-01-02
forum: General Help
---

### Post by xksinz on 2009-01-02
Hi! i'm a recent Ubuntu convert. i love working with Ubuntu, although i'm still not quite used to the way it operates. 

i just installed Openoffice. It was working fine until i started importing PDF. When i run it by clicking on .doc documents or from the main menu, it won't load. it will just show the 'starting screen' for about 1 sec, and nothing else happen.

i tried running it in terminal typing 'openoffice'. same thing happen. and there is no error message, in fact no message at all. 

i tried using 'sudo openoffice', didn't work.

so i tried running 'openoffice' in root terminal, it work!

Is there any way to run it normally?

---

### Post by ajgreeny on 2009-01-02
You say you installed open office, so I assume you mean OOo 3 as OOo 2.4 is already in ubuntu, and OOo3 is the only one that can import PDFs if I remember correctly.

If you installed open office 3 using the release from the OOo website, there will be two versions on your computer unless you uninstalled OOo2.4 manually.  You may also not have any menu items for OOo3 unless you went through the installation of the openoffice.org3.0-debian-menus package that is separate from all the other deb packages.

Can you enlighten us about how you installed open office, and which version is causing the problems.  If necessary open up a document and go to **Help > About OpenOffice.org** to see which it is.

I don't think there is an executable openoffice file either, just a shell script by that name to the executable named **soffice**, but the command **openoffice** does open a start page for me.  More info needed I'm afraid.

---

### Post by xksinz on 2009-01-02
Hi, thanks for replying. i thought i messed up too so i tried to purge Openoffice.

i tried using this command,
```
sudo apt-get --purge remove openoffice.org
```
in the terminal. But it says only 45.1kb will be cleared after the uninstallation.

[COLOR="Blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-crypto libsox-fmt-flac libswscale0 libqca2 libqimageblitz4
  vim-addon-manager liblzo1 libdc1394-22 texlive-humanities
  texlive-pictures-doc texlive-pstricks-doc libfame-0.9 libwxgtk2.6-0
  libqt4-test bsh-gcj toolame libpvm3 libsox-fmt-ao texlive-latex-extra-doc
  texlive-humanities-doc libboost-thread1.34.1 transcode-doc
  libswt3.2-gtk-java libboost-date-time1.34.1 libsox0 texlive-pstricks
  libsox-fmt-ffmpeg libsdl-net1.2 libgnomescan0 python-openssl
  texlive-generic-extra tidy libgnomescanui-common blt bsh python-tk libt1-5
  python-bittorrent libsox-fmt-all texlive-latex-extra libwxbase2.6-0
  texlive-xetex libxul0d ffmpeg libmjpegtools0c2a libsox-fmt-gsm lesstif2
  transcode libsox-fmt-mp3 pvm libgnomescanui0 libpoppler-qt4-3 libxalan2-java
  libsox-fmt-base libsox-fmt-ogg sox texlive-generic-recommended tcl8.4 tcl8.5
  libsox-fmt-sndfile python-wxversion libmozjs0d libsox-fmt-oss libgeoip1
  libsox-fmt-alsa libgnomescan-common tk8.4 tk8.5 mjpegtools
  libboost-filesystem1.34.1 libswt3.2-gtk-gcj python-wxgtk2.6 winbind
  libxul-common libswt3.2-gtk-jni libquicktime1 libimlib2 lame
  libglademm-2.4-1c2a texlive-pictures libmpeg2-4 libxalan2-java-gcj
  libavdevice52 libfaad0 liba52-0.7.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  openoffice.org*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 45.1kB disk space will be freed.[/COLOR]

i find it weird so i uninstall it using Synaptic Package Manager, restarted, then reinstall it again.

The version is 3.0, OOO300m9 build 9358.
The start page that i see also indicated the version to be 3.0.

It works nicely if i run it using root terminal. Any other ways would just be a glimpse of the start page.

---

### Post by The Cog on 2009-01-02
If you open your home folder in nautilus and press Ctrl-H to enable seeing "hidden" files and folders, you will probably find several folders starting with ".openoffice" (I have .openoffice.org, .openoffice.org2 and .openoffice.org3). There may be settings stored in one of these that causes the crash, so try renaming all those folders to ".Xopen..." so that openoffice doesn't see your old settings, then try to launch it again. I seem to remember having to do this with my setup, then deleting the original folders once I knew that they were the problem.

---

### Post by 73ckn797 on 2009-01-02
Try this:
I have installed OO 3.0 on my desk and laptops with Intrepid. Everything was effortless and is running great.

I completely removed all OO related installs through Synaptic. In your case you may have to even delete any other directories manually in your /home/*yourname* folder.

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org

Created a directory in /home/name/whatever.

Extracted files using File Roller (default Gnome compression utility) to the created directory. Double click on file.

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS) then entered "sudo dpkg -i *.deb" The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command "sudo dpkg -i *.deb". This creates the menu choices.

Started OO 3.0 and it works like a charm for me.

The desktop icon created using menu right click was read only but right click, properties allows changing that so I could rename the shortcut icon.

---

### Post by xksinz on 2009-01-03
thanks for the help. i went to my home folder and and renamed all the openoffice.org folders. it works!!! :D

---

