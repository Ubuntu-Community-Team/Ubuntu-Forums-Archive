---
title: "apt-get upgrade problem"
date: 2006-08-07
forum: Desktop Environments
---

### Post by Nickoladze on 2006-08-07
I got home from vacation today so i ran apt-get upgrade to install a week's worth of updated programs and i got an error, so i rebooted.

So i rebooted and gdm said that png is not a supported format anymore, but i can still manage to login but half my icons and my theme doesnt work because they use png images.

So i ran apt-get upgrade again and i got this:
> The following packages will be REMOVED:
  eog
The following packages have been kept back:
  totem
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
13 not fully installed or removed.
Need to get 0B of archives.
After unpacking 3416kB disk space will be freed.
Do you want to continue [Y/n]? y
](Reading database ... 165061 files and directories currently installed.)
Removing eog ...
*** glibc detected *** double free or corruption (!prev): 0x086d90c8 ***
/var/lib/dpkg/info/eog.postrm: line 9:  5891 Aborted                 scrollkeeper-update -q
dpkg: error processing eog (--remove):
 subprocess post-removal script returned error exit status 134
Errors were encountered while processing:
 eog
E: Sub-process /usr/bin/dpkg returned an error code (1)

Unfortunatly I don't remember the error I got before I rebooted, but it was similar to the one I'm getting now.

---

### Post by fistfullofroses on 2006-08-07
try this:

# apt-get update
# apt-get upgrade

then look at the package list of those programs which need to be upgraded,
copy and paste them into a line that says the following:

# apt-get -fy install <package name list>

if that does not work, then you may want to try upgrading apt itself.

---

### Post by Ziox on 2006-08-07
or try using aptitude:

sudo aptitude update

sudo aptitude dist-upgrade

---

### Post by Nickoladze on 2006-08-07
i did the -fy install thing and got this:
> Setting up eog (2.14.3-0ubuntu1) ...
*** glibc detected *** double free or corruption (!prev): 0x08076128 ***
/var/lib/dpkg/info/eog.postinst: line 11:  7505 Aborted                 scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 134
Setting up epiphany-browser (2.14.3-0ubuntu1) ...
*** glibc detected *** double free or corruption (!prev): 0x08076390 ***
/var/lib/dpkg/info/epiphany-browser.postinst: line 25:  7518 Aborted      scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing epiphany-browser (--configure):
 subprocess post-installation script returned error exit status 134
Setting up file-roller (2.14.4-0ubuntu1) ...
*** glibc detected *** double free or corruption (!prev): 0x08076390 ***
/var/lib/dpkg/info/file-roller.postinst: line 11:  7525 Aborted scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 134

It repeated like that for every one of the programs.
Here's the list:
> Errors were encountered while processing:
 eog
 epiphany-browser
 file-roller
 gdm
 gedit-common
 gedit
 gnome-applets-data
 gnome-panel-data
 gnome-panel
 gnome-applets
 gnome-games-data
 gnome-games
 zenity
 ubuntu-desktop

---

### Post by Nickoladze on 2006-08-08
bump

aptitude does the same

i still cant view png images, or watch mpg and avi movies. the window list on my gnome-panel doesnt work either.
i really need this fixed

---

### Post by Ramses de Norre on 2006-08-08
What does this:
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo aptitude install -f #be careful with this one, don't just pick yes, it's very aggressive
sudo aptitude update && sudo aptitude dist-upgrade
```

That are the commands I'd try to see what the problem is.

---

### Post by Nickoladze on 2006-08-08
they all return the same error i posted above for all the programs

---

### Post by Ramses de Norre on 2006-08-08
Could you post the output of ```
cat /var/lib/dpkg/info/eog.postrm
```

---

### Post by Nickoladze on 2006-08-08
```
#!/bin/sh
set -e
# Automatically added by dh_installmenu
if [ -x "`which update-menus 2>/dev/null`" ]; then update-menus ; fi
# End automatically added section
# Automatically added by dh_scrollkeeper
if [ "$1" = "remove" ] && which scrollkeeper-update >/dev/null 2>&1; then
        scrollkeeper-update -q
fi
# End automatically added section
# Automatically added by dh_gconf
if [ "$1" = purge ]; then
        OLD_DIR=/etc/gconf/schemas
        SCHEMA_FILES="eog.schemas "
        if [ -d $OLD_DIR ]; then
                for SCHEMA in $SCHEMA_FILES; do
                        rm -f $OLD_DIR/$SCHEMA
                done
                rmdir -p --ignore-fail-on-non-empty $OLD_DIR
        fi
fi
# End automatically added section
# Automatically added by dh_desktop
if [ "$1" = "remove" ] && which update-desktop-database >/dev/null 2>&1 ; then
        update-desktop-database -q
fi
# End automatically added section
```

---

### Post by Ramses de Norre on 2006-08-08
Hmm looks exactely the same here..
Could you do which scrollkeerper-update to check wether it's there?
And it's a shot in the dark but could you comment out this piece of the file: ```
if [ "$1" = purge ]; then
        OLD_DIR=/etc/gconf/schemas
        SCHEMA_FILES="eog.schemas "
        if [ -d $OLD_DIR ]; then
                for SCHEMA in $SCHEMA_FILES; do
                        rm -f $OLD_DIR/$SCHEMA
                done
                rmdir -p --ignore-fail-on-non-empty $OLD_DIR
        fi
fi
```
And try again?

---

### Post by Nickoladze on 2006-08-08
when running
# scrollkeeper-update
i get:
```
*** glibc detected *** double free or corruption (!prev): 0x08069ac0 ***
Aborted

```

just of of curiosity i ran 
# scrollkeeper-update -q >/dev/null 2>&1
then edited /var/lib/dpkg/info/eog.postinst and commented out:
```
if [ "$1" = "configure" ] && which scrollkeeper-update >/dev/null 2>&1; then
	scrollkeeper-update -q >/dev/null 2>&1
fi
```
and apt doesnt have any more problems with eog. should i go ahead and do the same with the rest of the programs its having trouble with?


edit: i just did something similar to epiphany-browser.postrm and i uninstalled epiphany-broswer and alot of the errors are fixed now. but i still get:
```
Setting up file-roller (2.14.4-0ubuntu1) ...
/var/lib/dpkg/info/file-roller.postinst: line 11: 22152 Segmentation fault scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gdm (2.14.10-0ubuntu1) ...
 * Reloading GNOME Display Manager configuration...  * Changes will take effect when all current X sessions have ended.
                                                                         [ ok ]
/var/lib/dpkg/info/gdm.postinst: line 113: 22207 Segmentation fault      scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on file-roller; however:
  Package file-roller is not configured yet.
 ubuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 file-roller
 gdm
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

so i did the same with the file-roller and gdm postinst files and it seems that everything is fine (i hope)

---

### Post by Ramses de Norre on 2006-08-08
You need to be careful editing those files, you could break stuff..
What does sudo dpkg --configure -a?
And does sudo apt-get -f install tell you there are any dependency problems besides file-roller and gdm?
There seems to be a problem with scrolkeeper or glibc but I'm not sure about how to troubleshoot it..

---

### Post by Nickoladze on 2006-08-08
sudo dpkg --configure -a returns nothing

sudo apt-get -f install says everything is fine

and i just commented out bits in them, so if there is a problem i can uncomment them.

i still cant view png files but im gonna reboot in a little bit, maybe thatll fix it

---

### Post by Nickoladze on 2006-08-08
rebooting didnt do anything but im still having problems.

i might just be better off reformatting wouldnt i?

---

### Post by Nickoladze on 2006-08-10
bump, please help

---

### Post by jeduan on 2006-08-11
Hi, I don't know if this will solve the problem. I was having the same problems and it worked for me, though.

Just run
```

sudo scrollkeeper-rebuilddb
sudo dpkg --configure -a

```

Hope it helps!

---

### Post by Nickoladze on 2006-08-11
```
/usr/bin/scrollkeeper-rebuilddb: line 48:  5613 Segmentation fault      scrollkeeper-update $quiet $verbose -p $scrollkeeper_db_dir
```

---

