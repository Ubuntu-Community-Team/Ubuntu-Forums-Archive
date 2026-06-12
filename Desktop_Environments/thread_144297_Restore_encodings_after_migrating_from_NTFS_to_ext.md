---
title: "Restore encodings after migrating from NTFS to ext3"
date: 2006-03-14
forum: Desktop Environments
---

### Post by adamkane on 2006-03-14
This post is a re-write of this thread:
[http://www.ubuntuforums.org/showthread.php?t=139154]("http://www.ubuntuforums.org/showthread.php?t=139154")

** Scenario:** 
You move your files from an NTFS partition to an ext3 partition, and the special characters have disappeared from all your filenames.

**What you can do:** 
You can move the files back onto an NTFS partition, and then mount the NTFS partition with nls=utf8, or you can leave the files on the ext3 partition, and convert the filenames to UTF-8 encoding.

**What you can't do:** 
There's no special command or method to mount an ext3 partition that will "just display" the special characters again. You must move the files off the ext3 partition, or convert the filenames to UTF-8 encoding.

**Notes:**
It's important to understand that NTFS uses CP850 filename encoding. This is different than ISO-8859-1 filename encoding. To say it another way, your ISO-8859-1 encoded filenames are actually CP850 encoded, if they are located on an NTFS partition.

If you want to make the leap and go Ubuntu all-the-way, the best recommendation is to add a second empty hard drive, format and mount it as ext3, then **browse** to the Windows share over your local network. This way you don't have to worry about mounting the remote share correctly. If you need to **mount** a remote Windows share or a local Windows partition, do not forget to use nls=utf8!

If you want to use both Windows and Ubuntu on a single machine, then you should format and mount your second hard drive as FAT32. Use iocharset=utf8 and nls=utf8 when mounting. FAT32 isn't recommended however, since it is much more likely that your FAT32 directory structure will become corrupt, and that you will find yourself in file recovery hell.

**Instructions:**
If you are stuck, because you've already moved your files with NTFS encoding onto an ext3 partition, and you can't move the files back onto an NTFS partition, I've listed the methods you can use to convert your NTFS encoded filenames to UTF-8 encoding. 

After I list methods to convert from NTFS (CP850) to UTF-8, I then list ways to convert from ISO-8859-1 to UTF-8, in case you have archives of files with ISO-8859-1 encoded filenames that need to be converted as well.

**To begin**, add the Universe repository, if you haven't already:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")

**NTFS to UTF-8 conversion:**

**Option 1 (Gnome/KDE/XFCE):**

```

sudo apt-get install convmv
convmv -f cp850 -t utf-8 -r --notest *.*

``` 
Be aware that there is a bug in convmv 1.08:
[http://j3e.de/linux/convmv/]("http://j3e.de/linux/convmv/")

> 
 ATTENTION: Perl 5.8.7 seems to have a broken decode_utf8() function so that convmv can not convert files to UTF-8 without using the --nosmart switch! convmv 1.09 works around this.
 
**Option 2 (Gnome):**

To make things a little easier you can right-click any files you need to convert using this **Nautilus-script**:

```

#!/bin/bash
#NTFS to UTF-8

if [ $# -gt 0 ];then

    convmv -f cp850 -t utf-8 -r --notest "$@"| zenity --progress --pulsate --text="conversion in progress" --auto-close

fi
exit 0

``` 
Save the Nautilus-script as a text file here:

~/.gnome2/nautilus-scripts/

then:

```

sudo chmod 700 ~/.gnome2/nautilus-scripts/*.*

``` 
More information about Nautilus-scripts:
[http://g-scripts.sourceforge.net/faq.php]("http://g-scripts.sourceforge.net/faq.php")

**Option 3 (KDE):**

If you use Konqueror, you can right-click any files you need to convert with this **KDE service menu**:

**ToUTF-8**
[http://www.kde-apps.org/content/show.php?content=31400]("http://www.kde-apps.org/content/show.php?content=31400")

Save the file to your Desktop and install:

```

cd ~/Desktop
tar xzvf 31400-toutf8_0.2.1.tar.gz
cd 31400-toutf8_0.2.1
gedit changeFilenameCode.desktop

``` 
Replace iso-8859-1 with cp850, then save the file.

```

gedit changeDirnameCode.desktop

``` 
Replace iso-8859-1 with cp850, then save the file.

```

cp *.desktop  ~/.kde/share/apps/konqueror/servicemenus/

``` 
**ISO-8859-1 to UTF-8 conversion:**

**Option 1 (Gnome/KDE/XFCE):**

```

sudo apt-get install convmv
convmv -f iso-8859-1 -t utf-8 -r --notest *.*

``` 
[B]Option 2 (Gnome):
[/B]
This **Nautilus-Script** is slightly different than the one above:

```

#!/bin/bash
#ISO-8859-1 to UTF-8

if [ $# -gt 0 ];then

    convmv -f iso-8859-1 -t utf-8 -r --notest "$@"| zenity --progress --pulsate --text="conversion in progress" --auto-close

fi
exit 0

``` 
Save the Nautilus-script here:

~/.gnome2/nautilus-scripts/

then:

```

sudo chmod 700 ~/.gnome2/nautilus-scripts/*.*

``` 
**Option 3 (KDE):**

The instructions for this **KDE service menu** are slightly different than those above:

**ToUTF-8**
[http://www.kde-apps.org/content/show.php?content=31400]("http://www.kde-apps.org/content/show.php?content=31400")

Save the file to your Desktop and install:

```

cd ~/Desktop
tar xzvf 31400-toutf8_0.2.1.tar.gz
cd 31400-toutf8_0.2.1
cp *.desktop  ~/.kde/share/apps/konqueror/servicemenus/

``` 
**Option 4 (Gnome/KDE/XFCE):**

If you have a bunch of files with **ISO-8859-1** encoded filenames, you can use **ROX-Filer** to view and manipulate the files. ISO-8859-1 encoded filenames will appear in red:

ROX-Filer:
[http://rox.sourceforge.net/]("http://rox.sourceforge.net/")
[http://rox.sourceforge.net/desktop/Internationalisation]("http://rox.sourceforge.net/desktop/Internationalisation")

```

sudo apt-get install rox-filer
rox-filer

``` 
ROX-Filer isn't able to view NTFS encoded filenames correctly. Only use ROX-Filer to view ISO-8859-1 encoded filenames.

**Tip:**
Nautilus is the default file manager for Gnome, Konqueror is the default file manager for KDE, and ROX-Filer is the default file manager for XFCE. However you aren't limited to any one file manager.

Be aware that .desktop files are hidden in Gnome and XFCE, so it is easier to install KDE service menus while you are in KDE.

Save .desktop files here for the current user:

~/.kde/share/apps/konqueror/servicemenus/

or here for all users:

/usr/share/apps/konqueror/servicemenus/

** Big list of KDE service menus:**
[http://www.kde-apps.org/index.php?xcontentmode=287]("http://www.kde-apps.org/index.php?xcontentmode=287")

** General information** about UTF-8 on the desktop:
[http://www.gentoo.org/doc/en/utf-8.xml]("http://www.gentoo.org/doc/en/utf-8.xml")
[http://www.suse.de/~mfabian/suse-cjk/unicode-switch.html]("http://www.suse.de/%7Emfabian/suse-cjk/unicode-switch.html")

---

