---
title: "Kiba Dock on Gutsy [Help]"
date: 2008-01-03
forum: Desktop Effects &amp; Customization
---

### Post by Fleece Flamingo on 2008-01-03
So I finished the installation in [this thread]("http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba"), but where do I go from there. Kiba dock didnt boot up and all I have is the documents and there files in my home folder.

Any help is appreciated!

---

### Post by b0rka7a on 2008-01-03
Type in a terminal
```
kiba-dock
```
and comment the output here. I don't know if I can help you, but someone other could... :)

---

### Post by Fleece Flamingo on 2008-01-03
Says the commands not found

---

### Post by Fleece Flamingo on 2008-01-03
Aww come on, I know someones gotta know how to do this!

---

### Post by b0rka7a on 2008-01-03
Are you sure you have kiba-dock installed ? If you type kiba-dock and you get "command not found" in response, that means that you don't have kiba-dock installed.
Follow the guide again (to the end) and it should work.

---

### Post by Mega_Mike on 2008-03-06
I created a set of Ubuntu Gutsy .deb (debian) packages for kiba-dock.  I DID NOT build the dependency list so make sure you have the following packages installed in your system to be safe. 
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

