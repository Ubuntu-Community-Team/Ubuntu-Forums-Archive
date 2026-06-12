---
title: "dpkg problem"
date: 2010-03-01
forum: Desktop Environments
---

### Post by H0lyGanGs7eR on 2010-03-01
Hello! I was installing ubuntu studio on my Ubuntu installation when the electricity stopped and when i tried to install it after i had that error - dpkg error, use "dpgk --configure -a" to repair. I wrote, and after i ran again to install ubuntu studio i got this 
```
niki@niki-desktop:~$ sudo apt-get install ubuntustudio-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ubuntustudio-desktop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
24 not fully installed or removed.
Need to get 0B/9,290B of archives.
After this operation, 36.9kB of additional disk space will be used.
Selecting previously deselected package ubuntustudio-desktop.
(Reading database ... 182939 files and directories currently installed.)
Unpacking ubuntustudio-desktop (from .../ubuntustudio-desktop_0.64_amd64.deb) ...
Setting up ttf-sazanami-gothic (20040629-4ubuntu1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-sazanami-gothic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ttf-sazanami-mincho (20040629-4ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ttf-sazanami-mincho (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gnome-app-install (0.5.60.1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-app-install (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gnome-netstatus-applet (2.26.0-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-netstatus-applet (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gnome-network-admin (2.28.1-0ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-network-admin (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gnome-themes (2.28.1-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-themes (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libgconfmm-2.6-1c2 (2.24.0-2) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgconfmm-2.6-1c2 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up libglademm-2.4-1c2a (2.6.7-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libglademm-2.4-1c2a (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libglew1.5 (1.5.1-4ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libglew1.5 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.31-9-rt (2.6.31-9.152) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-headers-2.6.31-9-rt (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-rt:
 linux-headers-rt depends on linux-headers-2.6.31-9-rt; however:
  Package linux-headers-2.6.31-9-rt is not configured yet.
dpkg: error processing linux-headers-rt (--configure):
 dependency problems - leaving unconfigured
Setting up pavumeter (0.9.3-1ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing pavumeter (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pavucontrol:
 pavucontrol depends on libglademm-2.4-1c2a (>= 2.6.0); however:
  Package libglademm-2.4-1c2a is not configured yet.
dpkg: error processing pavucontrol (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of paman:
 paman depends on libglademm-2.4-1c2a (>= 2.6.0); however:
  Package libglademm-2.4-1c2a is not configured yet.
dpkg: error processing paman (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of paprefs:
 paprefs depends on libgconfmm-2.6-1c2 (>= 2.24.0); however:
  Package libgconfmm-2.6-1c2 is not configured yet.
 paprefs depends on libglademm-2.4-1c2a (>= 2.6.0); however:
  Package libglademm-2.4-1c2a is not configured yet.
dpkg: error processing paprefs (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of padevchooser:
 padevchooser depends on pavumeter; however:
  Package pavumeter is not configured yet.
 padevchooser depends on pavucontrol; however:
  Package pavucontrol is not configured yet.
 padevchooser depends on paman; however:
  Package paman is not configured yet.
 padevchooser depends on paprefs; however:
  Package paprefs is not configured yet.
dpkg: error processing padevchooser (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of rss-glx:
 rss-glx depends on libglew1.5 (>= 1.5.1); however:
  Package libglew1.5 is not configured yet.
dpkg: error processing rss-glx (--configure):
 dependency problems - leaving unconfigured
Setting up tango-icon-theme (0.8.90-3) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing tango-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of tango-icon-theme-common:
 tango-icon-theme-common depends on tango-icon-theme; however:
  Package tango-icon-theme is not configured yet.
dpkg: error processing tango-icon-theme-common (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-arabeyes (2.0-2) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ttf-arabeyes (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntustudio-icon-theme:
 ubuntustudio-icon-theme depends on tango-icon-theme; however:
  Package tango-icon-theme is not configured yet.
dpkg: error processing ubuntustudio-icon-theme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntustudio-look:
 ubuntustudio-look depends on ubuntustudio-icon-theme; however:
  Package ubuntustudio-icon-theme is not configured yet.
dpkg: error processing ubuntustudio-look (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntustudio-default-settings:
 ubuntustudio-default-settings depends on ubuntustudio-look; however:
  Package ubuntustudio-look is not configured yet.
dNo apport report written because MaxReports is reached already
                                                               No apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
         pkg: error processing ubuntustudio-default-settings (--configure):
 dependency problems - leaving unconfigured
Setting up usplash-theme-ubuntustudio (0.20) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing usplash-theme-ubuntustudio (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntustudio-desktop:
 ubuntustudio-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 ubuntustudio-desktop depends on gnome-netstatus-applet; however:
  Package gnome-netstatus-applet is not configured yet.
 ubuntustudio-desktop depends on gnome-network-admin; however:
  Package gnome-network-admin is not configured yet.
 ubuntustudio-desktop depends on gnome-themes; however:
  Package gnome-themes is not configured yet.
 ubuntustudio-desktop depends on rss-glx; however:
  Package rss-glx is not configured yet.
 ubuntustudio-desktop depends on tango-icon-theme; however:
  Package tango-icon-theme is not configured yet.
 ubuntustudio-desktop depends on tango-icon-themeNo apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             -common; however:
  Package tango-icon-theme-common is not configured yet.
 ubuntustudio-desktop depends on ubuntustudio-default-settings; however:
  Package ubuntustudio-default-settings is not configured yet.
 ubuntustudio-desktop depends on ubuntustudio-look; however:
  Package ubuntustudio-look is not configured yet.
 ubuntustudio-desktop depends on usplash-theme-ubuntustudio; however:
  Package usplash-theme-ubuntustudio is not configured yet.
dpkg: error processing ubuntustudio-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-sazanami-gothic
 ttf-sazanami-mincho
 gnome-app-install
 gnome-netstatus-applet
 gnome-network-admin
 gnome-themes
 libgconfmm-2.6-1c2
 libglademm-2.4-1c2a
 libglew1.5
 linux-headers-2.6.31-9-rt
 linux-headers-rt
 pavumeter
 pavucontrol
 paman
 paprefs
 padevchooser
 rss-glx
 tango-icon-theme
 tango-icon-theme-common
 ttf-arabeyes
 ubuntustudio-icon-theme
 ubuntustudio-look
 ubuntustudio-default-settings
 usplash-theme-ubuntustudio
 ubuntustudio-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Help please!

---

### Post by MelDJ on 2010-03-01
have you tried 
sudo defoma-reconfigure -f

---

### Post by H0lyGanGs7eR on 2010-03-01
yes, but after that it's the same. Everytime I want to install something dpkg tries to install these packages too :(

---

### Post by MelDJ on 2010-03-01
try  : ```
sudo apt-get install -f
```

---

### Post by MelDJ on 2010-03-01
check this out too:
[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

### Post by H0lyGanGs7eR on 2010-03-02
I used this link and the list i shorter now - only these packages - 
```
niki@niki-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ttf-sazanami-gothic (20040629-4ubuntu1) ...
/etc/defoma/hints/ttf-sazanami-gothic.hints: Unable to open, or empty.
dpkg: error processing ttf-sazanami-gothic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ttf-sazanami-mincho (20040629-4ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ttf-sazanami-mincho (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gnome-app-install (0.5.60.1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-app-install (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gnome-netstatus-applet (2.26.0-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-netstatus-applet (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gnome-themes (2.28.1-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-themes (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up ttf-arabeyes (2.0-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ttf-arabeyes (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up usplash-theme-ubuntustudio (0.20) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing usplash-theme-ubuntustudio (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 ttf-sazanami-gothic
 ttf-sazanami-mincho
 gnome-app-install
 gnome-netstatus-applet
 gnome-themes
 ttf-arabeyes
 usplash-theme-ubuntustudio
E: Sub-process /usr/bin/dpkg returned an error code (1)
niki@niki-desktop:~$ ^C

```
Please help how to repair this!

---

