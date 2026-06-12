---
title: "Uninstall kiba dock?  (I have the guide that I used)"
date: 2008-03-16
forum: Desktop Effects &amp; Customization
---

### Post by cex on 2008-03-16
Well, again another kiba-dock installation that didn't work for me.  

This is the guide I used:  

[http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.0](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.0)

I've tried 

sudo apt-get remove kiba-dock  

but I get this reply : 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kiba-dock is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libakamaru0 kiba-settings
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

[IMG]http://i153.photobucket.com/albums/s214/heart_nails/Screenshot.png[/IMG]

---

### Post by Kabezon on 2008-03-17
Why didn't the installation work? I know you are trying to uninstall it, but just in case you might be interested, somebody posted a .deb package for Gutsy:

> **Mega_Mike said:**
> I created a set of Ubuntu Gutsy .deb (debian) packages for kiba-dock.  I DID NOT build the dependency list so make sure you have the following packages installed in your system to be safe. 
    * automake
    * autoconf
    * gcc
    * libtool
    * intltool >= 0.35.0
    * gettext 
    * glib2 >= 2.12
    * gtk+2 >= 2.10
    * cairo >= 1.0.0
    * libxml-2.0
    * pango >= 1.10.0
    * Optional depends:
          o librsvg > 2.14.4 (for SVG support)
          o glitz >= 0.5.3
          o akamaru (for physics) 
    * Dbus plugin
          o dbus
          o pygtk2-devel (to build the actual Dbus plugins, located in the kiba-dbus-plugins directory) 
    * Gmenu plugin
          o libgnome-menu 
    * Stack plugin
          o libgnomeui-2.0 > 2.0.0
          o libgnomevfs > 2.0.0 
    * Sysinfo plugin
          o libgtop > 2.0.0 
    * Trash plugin
          o libgnomevfs > 2.0.0 

I got this list from [http://www.kiba-dock.org/](http://www.kiba-dock.org/) .  Also make sure you apply the packages in this order akamaru, kiba-dock, kiba-plugins, kiba-dbus-plugins.

[http://rapidshare.com/files/97493813/kiba.tar.gz.html](http://rapidshare.com/files/97493813/kiba.tar.gz.html)

---

### Post by cex on 2008-03-17
I can't install anything until I get this uninstalled. =\

---

### Post by ThaRabbit on 2008-03-17
> **cex said:**
> I can't install anything until I get this uninstalled. =\

Best way would be to open the script with a text editor to see what exactly it did :)

Checking through the script it seems it downloads the svn and them compiles / installs.

This means that the folders holding the actual source files should still be available on your system. According to the script these folders would be located like this:

> kiba
-akamaru
-kiba-dock
-kiba-plugins
-kiba-dbus-plugins

and, if you've chose at install time:
-kiba-gaim-plugin

you can remove all of this by doing:
> sudo make uninstall
sudo make clean

in each of these subfolders!

This leaves the dependancies the script installed:
> fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0

These are not actually part of kiba, but required for kiba to run. Several of these can be uninstalled.. several can not. If you want I'm sure we can figure out which are deletable.

To be clear though, the sudo make uninstall / make clean routine in every subfolder will completely remove kiba from your system.

You will, ofcource, have to delete the folders afterwards.

---

### Post by cex on 2008-03-17
Well, when I try to uninstall everyone like this, it doesn't work.

john@john-desktop:~$ cd kiba
bash: cd: kiba: No such file or directory
john@john-desktop:~$ kiba
bash: kiba: command not found
john@john-desktop:~$ -akamaru
bash: -akamaru: command not found
john@john-desktop:~$ cd akamaru
bash: cd: akamaru: No such file or directory
john@john-desktop:~$ cd kiba-dock
john@john-desktop:~/kiba-dock$ sudo make uninstall
[sudo] password for john:
make: *** No rule to make target `uninstall'.  Stop.
john@john-desktop:~/kiba-dock$ sudo make clean
make: *** No rule to make target `clean'.  Stop.
john@john-desktop:~/kiba-dock$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
john@john-desktop:~/kiba-dock$ cd ..
john@john-desktop:~$ 

Again, I'm not sure if I'm doing this right...

---

### Post by ThaRabbit on 2008-03-17
> **cex said:**
> Well, when I try to uninstall everyone like this, it doesn't work.

john@john-desktop:~$ cd kiba
bash: cd: kiba: No such file or directory
john@john-desktop:~$ kiba
bash: kiba: command not found
john@john-desktop:~$ -akamaru
bash: -akamaru: command not found
john@john-desktop:~$ cd akamaru
bash: cd: akamaru: No such file or directory
john@john-desktop:~$ cd kiba-dock
john@john-desktop:~/kiba-dock$ sudo make uninstall
[sudo] password for john:
make: *** No rule to make target `uninstall'.  Stop.
john@john-desktop:~/kiba-dock$ sudo make clean
make: *** No rule to make target `clean'.  Stop.
john@john-desktop:~/kiba-dock$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
john@john-desktop:~/kiba-dock$ cd ..
john@john-desktop:~$ 

Again, I'm not sure if I'm doing this right...

Where did you download the script to, the folder you are looking for will most likely be there :)

The script creates a folder called "kiba" in the location where you had the script, it then creates several subdirectories (the ones listed above).

Running the sudo make uninstall command inside those directories should work :)

If those directories are gone (you may have deleted them by yourself already?), you can try to redownload the source files and make uninstall from there. Here's how to do that (based on the script you linked to):

```
1. cd ~
2. svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/ kiba
3. cd ~/kiba/akamaru/
4. ./autogen.sh  --prefix="/usr"
5. sudo make uninstall
6. cd ~/kiba/kiba-dock/
7. ./autogen.sh  --enable-akamaru 
8. sudo make uninstall
9. cd ~/kiba/kiba-plugins/
10. ./autogen.sh  --enable-gst
11. sudo make uninstall
12. cd ~/kiba/kiba-dbus-plugins/
13. ./autogen.sh
14. sudo make uninstall
```

Now if you've also installed the gaim plugin:
>  15. cd ~/kiba/kiba-gaim-plugin/
16. ./autogen.sh
17. sudo make uninstall

---

### Post by MyR on 2008-05-11
thanks!

just a note: i had to run the ./autogen.sh as root to get this to work

peace

---

