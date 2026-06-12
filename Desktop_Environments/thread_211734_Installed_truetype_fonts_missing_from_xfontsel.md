---
title: "Installed truetype fonts missing from xfontsel"
date: 2006-07-08
forum: Desktop Environments
---

### Post by yabbadabbadont on 2006-07-08
I have the following truetype fonts installed:
> /usr/share/fonts $ l
total 12
-rw-r--r-- 1 root root   37 2006-07-08 18:11 fonts.cache-1
drwxr-xr-x 6 root root 4096 2006-07-08 02:45 truetype/
drwxr-xr-x 3 root root 4096 2006-07-08 17:12 type1/
/usr/share/fonts $ l *
-rw-r--r-- 1 root root   37 2006-07-08 18:11 fonts.cache-1

truetype:
total 20
-rw-r--r-- 1 root root   97 2006-07-08 18:11 fonts.cache-1
drwxr-xr-x 2 root root 4096 2006-07-08 17:37 freefont/
drwxr-xr-x 2 root root 4096 2006-07-08 17:37 msttcorefonts/
drwxr-xr-x 2 root root 4096 2006-07-08 17:37 ttf-bitstream-vera/
drwxr-xr-x 2 root root 4096 2006-07-08 17:37 ttf-dejavu/

type1:
total 8
-rw-r--r-- 1 root root   19 2006-07-08 18:11 fonts.cache-1
drwxr-xr-x 2 root root 4096 2006-07-08 17:12 gsfonts/

They all show up when using a gtk2 based font selector, like the one in switch2 provided by gtk-theme-switch.  However, none of them show up in gtk1 based font selectors like switch from gtk-theme-switch.  Also, neither xlsfonts nor xfontsel list these fonts.  I have done many searches of these forums for different terms but have not yet found any relevant information.  I did find out that they are all defoma fonts.  I also discovered that the FontPath setting in /etc/X11/xorg.conf for the defoma fonts points to a path that doesn't exist...  I would appreciate any information and/or suggestions you may have to help me try to resolve this issue.  Thanks in advance.

---

### Post by yabbadabbadont on 2006-07-08
Just to be sure, I reinstalled all fonts.  All looked fine except that when reinstalling the msttcorefonts, I get this warning:
> warning: /usr/share/X11/fonts/truetype does not exist or is not a directory

All of the truetype fonts were actually installed into /usr/share/fonts/truetype.  I wonder if the package maintainers have made a mistake?

---

### Post by ThanosP on 2006-07-08
Dear all,
I am running Kubuntu Dapper and have the same problem: when trying to select a font for the login screen (from kcontrol's login manager), none of my installed msttcorefonts show up.

Even when I cd'ed to /usr/share/apps/kdm/themes/ and edited the .xml file of my login theme to force it to use Georgia, the font displayed at login was still the system-standard DejaVu Sans.

Any ideas, anyone?

Thanks,
Thanos

---

### Post by yabbadabbadont on 2006-07-11
Well, I came up with a work around.  I restored my backup of Gentoo.  I don't know why mkfontdir wouldn't create fonts.dir files for these fonts in Ubuntu.  When I have more time, I'll see about pulling the various fonts.* files from my Gentoo system and see if they will work (with or without modification) in Ubuntu.

---

