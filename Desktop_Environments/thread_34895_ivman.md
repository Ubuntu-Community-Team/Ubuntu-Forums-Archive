---
title: "ivman"
date: 2005-05-16
forum: Desktop Environments
---

### Post by !nkubus on 2005-05-16
i have read on the wikki thet kubuntu might have plans to use ivman so i wanted to try it because  it look really cool :

[http://code.mizzenblog.com/thing/ivman](http://code.mizzenblog.com/thing/ivman)


si i wanted to compile it because of the lack of a debian package but i received the following error:

```

checking stdio.h usability... no
checking stdio.h presence... yes
configure: WARNING: stdio.h: present but cannot be compiled
configure: WARNING: stdio.h:     check for missing prerequisite headers?
configure: WARNING: stdio.h: see the Autoconf documentation
configure: WARNING: stdio.h:     section "Present But Cannot Be Compiled"
configure: WARNING: stdio.h: proceeding with the preprocessor's result
configure: WARNING: stdio.h: in the future, the compiler will take precedence
configure: WARNING:     ## -------------------------------- ##
configure: WARNING:     ## Report this to the ivman lists.  ##
configure: WARNING:     ## -------------------------------- ##
checking for stdio.h... yes


```

i'm not able to compile it.

any help would be appreciated :)

thanks

---

### Post by evermind on 2005-06-08
a while ago I builded a debian package -- for me it works on hoary so far

---

### Post by philipacamaniac on 2005-06-08
[QUOTE=evermind]a while ago I builded a debian package -- for me it works on hoary so far[/QUOTE]

You should build a source package, and submit this to the MOTU team. I installed it on Hoary with KDE 3.4.1 and it looks good as of yet. Automount support is awesome! I wonder if the Ubuntu/GNOME folks have something in the works also...

---

### Post by !nkubus on 2005-06-08
wow thank you very much guys :)

awesome

---

### Post by !nkubus on 2005-06-08
[QUOTE=philipacamaniac]You should build a source package, and submit this to the MOTU team. I installed it on Hoary with KDE 3.4.1 and it looks good as of yet. Automount support is awesome! I wonder if the Ubuntu/GNOME folks have something in the works also...[/QUOTE]

I Really hope so , i think this is one package that can make all the difference in the world, because no we can configure easyl  every media or events we want on the computer :)

please include this in breezy  :)

---

### Post by evermind on 2005-06-09
[QUOTE=philipacamaniac]You should build a source package, and submit this to the MOTU team. I installed it on Hoary with KDE 3.4.1 and it looks good as of yet. Automount support is awesome! I wonder if the Ubuntu/GNOME folks have something in the works also...[/QUOTE]

It was just a dirt-hack -- so I don´t know how to do an deb-src package the "easy way"
can you direct me to some good tutorials if you know one?


thx


UPDATED .deb: ivman-0.5_pre3-5_i386.deb
In the init script I provided there is  a workaround for ejecting dvd´s after playing them (in current ivman-0.6x this issues should be gone but it depends on hal 0.5 etc.)

# enable eject-button
echo 0 >  /proc/sys/dev/cdrom/lock

I provide another release of ivman-0.5_pre3 in which this workaround is applied within the case-selection and not just added to the script (like in ivman-0.5_pre3-4_i386.deb)

so no need to update its just a formal thing

---

### Post by !nkubus on 2005-06-09
Thanks it worked #1 :)

I have a another qquestion, i habe enables Kde notifications, but i can't customize the place and the color of the pop up, it appears on top righs in a light gray , it's really hard to notice, i want to have it  around the systray in some sort of a color that catch the eyes 

any ideas?

or i will have to launch kdevelopp and program my self a popup?

---

### Post by haaglin on 2005-06-22
hi, when i tried to run ivman, i get this error:
> 
Ikke's Volume Manager, [http://ivman.sf.net](http://ivman.sf.net)
10334: arguments to dbus_message_new_method_call() were incorrect, assertion "path != NULL" failed in file dbus-message.c line 1723.
This is normally a bug in some application using the D-BUS library.
libhal.c 1856 : Couldn't allocate D-BUS message
 

Does anyone know how to fix this?

---

### Post by evermind on 2005-06-22
[QUOTE=haaglin]hi, when i tried to run ivman, i get this error:
 

Does anyone know how to fix this?[/QUOTE]

which vesion of dbus and hal are you using?
and are those services runing?

execute
dpkg-query -l hal dbus-1
to see which version is installed
output should be similar to this
```
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hal            0.4.7-1ubuntu1 Hardware Abstraction Layer
ii  dbus-1         0.23.4-0ubuntu simple interprocess messaging system
```


ps -A|grep -e dbus -e hal
to see if dbus and hal is runing

you should see something like this
```

 6177 ?        00:00:00 dbus-launch
 6178 ?        00:00:00 dbus-daemon-1
 7661 ?        00:00:00 dbus-daemon-1
 7673 ?        00:00:01 hald
```


I get a similar message some time ago but no longer know how I fixed it
so try above

---

### Post by haaglin on 2005-06-22
it gives me the same output as you: 

> 
+++-==============-==============-============================================
ii  hal            0.4.7-1ubuntu1 Hardware Abstraction Layer
ii  dbus-1         0.23.4-0ubuntu simple interprocess messaging system

 

> 
 7888 ?        00:00:00 dbus-launch
 7889 ?        00:00:00 dbus-daemon-1
26508 ?        00:00:00 dbus-daemon-1
26520 ?        00:00:00 hald


---

### Post by haaglin on 2005-06-24
Does anyone have a solution?

---

### Post by evermind on 2005-07-01
Are you using ubuntu or kubuntu?
I don´t know exactly what the problem could be but either dbus or hal deps blocks ivman

use this and post output

rdeps for hal and dbus
```
export LC_ALL=C

for i in `apt-cache rdepends hal |grep -v  'Reverse Depends:'|sort|uniq`;do dpkg -s $i 2>&1|grep -e 'Package: ' -e 'Status: '|grep -v -e 'is not installed';done

for i in `apt-cache rdepends dbus-1 |grep -v  'Reverse Depends:'|sort|uniq`;do dpkg -s $i 2>&1|grep -e 'Package: ' -e 'Status: '|grep -v -e 'is not installed';done

```

this will show you the reverse dependencies of dbus-1 and hal and checks which package is installed and needs dbus-1/hal

---

### Post by evermind on 2005-07-01
have a look at
[http://forums.gentoo.org/viewtopic-t-319858-highlight-allocate+dbus.html](http://forums.gentoo.org/viewtopic-t-319858-highlight-allocate+dbus.html)

It seems there is something wrong with your config-files in /etc/ivman ?

---

### Post by haaglin on 2005-07-01
Fork is set to true and debug to false. 
Here is my output from the command you gave me:

```

Package: gnome-volume-manager
Status: install ok installed
Package: hal-device-manager
Status: install ok installed
Package: ivman
Status: install ok installed
Package: kdebase-kio-plugins
Status: install ok installed
Package: kubuntu-desktop
Status: install ok installed
Package: pmount
Status: install ok installed
Package: ubuntu-desktop
Status: purge ok not-installed
Package: hal
Status: install ok installed
vidar@BLACKPOWER:~ $ for i in `apt-cache rdepends dbus-1 |grep -v  'Reverse Depends:'|sort|uniq`;do dpkg -s $i 2>&1|grep -e 'Package: ' -e 'Status: '|grep -v -e 'is not installed';done
Package: bluez-pin
Status: install ok installed
Package: bluez-utils
Status: install ok installed
Package: dbus-1-dev
Status: install ok installed
Package: dbus-1-utils
Status: install ok installed
Package: dbus-glib-1
Status: install ok installed
Package: dbus-qt-1
Status: install ok installed
Package: evolution
Status: install ok installed
Package: gnome-media
Status: install ok installed
Package: gnome-volume-manager
Status: install ok installed
Package: hal
Status: install ok installed
Package: ivman
Status: install ok installed
Package: kdebase-kio-plugins
Status: install ok installed
Package: libdbus-1-1
Status: deinstall ok config-files
Package: libgnomevfs2-common
Status: install ok installed
Package: libhal-storage0
Status: install ok installed
Package: libhal0
Status: install ok installed
Package: libnautilus-burn1
Status: install ok installed
Package: nautilus-cd-burner
Status: install ok installed
Package: pmount
Status: install ok installed
Package: python2.3-dbus
Status: install ok installed
Package: python2.4-dbus
Status: install ok installed
Package: totem-gstreamer
Status: install ok installed
Package: totem-xine
Status: deinstall ok config-files
Package: update-notifier
Status: install ok installed
Package: vlc
Status: deinstall ok config-files
Package: dbus-1
Status: install ok installed           

```

---

### Post by evermind on 2005-07-01
will ivman work in the console without runing kde or gnome?

here my output pls compare:
```
# for i in `apt-cache rdepends hal |grep -v  'Reverse Depends:'|sort|uniq`;do dpkg -s $i 2>&1|grep -e 'Package: ' -e 'Status: '|grep -v -e 'is not installed';done
Package: gnome-volume-manager
Status: install ok installed
Package: hal
Status: install ok installed
Package: hal-device-manager
Status: install ok installed
Package: hwdb-client
Status: install ok installed
Package: ivman
Status: install ok installed
Package: pmount
Status: install ok installed
Package: ubuntu-desktop
Status: install ok installed
#for i in `apt-cache rdepends dbus-1 |grep -v  'Reverse Depends:'|sort|uniq`;do dpkg -s $i 2>&1|grep -e 'Package: ' -e 'Status: '|grep -v -e 'is not installed';done
Package: dbus-1
Status: install ok installed
Package: dbus-1-utils
Status: install ok installed
Package: dbus-glib-1
Status: install ok installed
Package: evolution
Status: install ok installed
Package: gnome-media
Status: install ok installed
Package: gnome-volume-manager
Status: install ok installed
Package: hal
Status: install ok installed
Package: ivman
Status: install ok installed
Package: libgnomevfs2-common
Status: install ok installed
Package: libhal0
Status: install ok installed
Package: libhal-storage0
Status: install ok installed
Package: libnautilus-burn1
Status: install ok installed
Package: nautilus-cd-burner
Status: install ok installed
Package: pmount
Status: install ok installed
Package: python2.4-dbus
Status: install ok installed
Package: totem-gstreamer
Status: deinstall ok config-files
Package: totem-xine
Status: install ok installed
Package: update-notifier
Status: install ok installed
Package: vlc
Status: install ok installed


```

---

