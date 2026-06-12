---
title: "bittorrent disappeared"
date: 2006-09-19
forum: Desktop Environments
---

### Post by richeo on 2006-09-19
Hello,

I'm running 6.06 (2.6.15-27-386) and bittorrent has quit working.  Here are the symptoms:

1. bittorrent worked fine after I first loaded Ubuntu; I was able to download several .iso files without any problems.  It worked both by clicking on a .torrent file from within firefox and also from the command line.

2. Two days ago it suddenly quit working, both in the browser and from the command line, with a "command not found" error.  I tried uninstalling (via apt-get) and then reinstalling it but the problem persists.

3. After uninstalling and reinstalling, running '$which bittorrent' yields no result and running '$locate bittorrent' returns the following:

/var/cache/apt/archives/bittorrent_3.4.2-6ubuntu2_all.deb
/var/cache/apt/archives/bittorrent-gui_3.4.2-6ubuntu2_all.deb
/var/lib/dpkg/info/bittorrent.list
/var/lib/dpkg/info/bittorrent.postrm
/var/lib/dpkg/info/bittorrent-gui.list
/var/lib/dpkg/info/bittorrent-gui.postrm
/etc/default/bittorrent
/etc/init.d/bittorrent
/etc/rc0.d/K20bittorrent
/etc/rc6.d/K20bittorrent
/usr/share/doc/bash/completion-contrib/bittorrent
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-x-bittorrent.png
/usr/share/icons/gnome/48x48/mimetypes/gnome-mime-application-x-bittorrent.png
/usr/share/mime/application/x-bittorrent.xml
/usr/share/mimelnk/application/x-bittorrent.desktop
/usr/share/ubuntu-docs/ubuntu/menus/C/bittorrent.xml

Running '$whereis bittorrent' returns "bittorrent: /usr/share/bittorrent" which is a directory.

I have the following files in /usr/bin:
$ ls /usr/bin/bt*
/usr/bin/btcompletedir                  
/usr/bin/btmakemetafile
/usr/bin/btcompletedir.bittorrent       
/usr/bin/btmakemetafile.bittorrent
/usr/bin/btdownloadcurses               
/usr/bin/btreannounce
/usr/bin/btdownloadcurses.bittorrent    
/usr/bin/btreannounce.bittorrent
/usr/bin/btdownloadheadless             
/usr/bin/btrename
/usr/bin/btdownloadheadless.bittorrent  
/usr/bin/btrename.bittorrent
/usr/bin/btlaunchmany                   
/usr/bin/btshowmetainfo
/usr/bin/btlaunchmany.bittorrent        
/usr/bin/btshowmetainfo.bittorrent
/usr/bin/btlaunchmanycurses             
/usr/bin/bttrack
/usr/bin/btlaunchmanycurses.bittorrent  
/usr/bin/bttrack.bittorrent

4. I tried downloading and install the .deb file from bittorrent.com but experienced the exact same problem as above.

5. When I reload bittorrent I receive the following:

$sudo apt-get install bittorrent
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  bittorrent-gui
The following NEW packages will be installed:
  bittorrent
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/94.2kB of archives.
After unpacking 594kB of additional disk space will be used.
Selecting previously deselected package bittorrent.
(Reading database ... 88238 files and directories currently installed.)
Unpacking bittorrent (from .../bittorrent_3.4.2-6ubuntu2_all.deb) ...
Setting up bittorrent (3.4.2-6ubuntu2) ...


Any ideas on why I can't install bittorrent properly?  I have no idea what I did to cause bittorrent to disappear off of my system, but it's really puzzling as to why I cannot reload it.  

Thanks!
Rich

---

### Post by Vogateer on 2006-11-07
I had this problem after I upgraded python to version 2.5, since apparently bittorrent only works using python 2.4. Of course, I had manually changed the symlink of python to point to 2.5, since I'm trying to learn python by using the newest version, so if you haven't done that, then your problem should be different. I'm not sure how advanced a linux user, so just ignore my recommendations if you've already tried them. Try this:

```
ls -al /usr/bin/pyth*
```

If you see something like this at the end of one of the lines:

```
root root  9 2006-11-07 05:31 /usr/bin/python -> python2.4
```

Then you have the correct version of python, and you should be okay in that respect.

The actual name of the program is /usr/bin/gnome-btdownload, so that's the file you want to look for. You might want to think about reinstalling bittorrent completely, as well.

```
sudo apt-get --reinstall install bittorrent
```

Good luck!

---

