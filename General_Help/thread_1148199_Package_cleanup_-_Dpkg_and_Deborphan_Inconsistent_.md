---
title: "Package cleanup - Dpkg and Deborphan Inconsistent Output"
date: 2009-05-04
forum: General Help
---

### Post by cmcginty on 2009-05-04
Can anyone explain why dpkg indicates stale config files, but deborphan does not?

```

$ dpkg -l | egrep -v '^ii'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                              Description
+++-==========================================-====================================-============================================
rc  console-tools                              1:0.2.3dbs-65.1ubuntu1               Linux console and font utilities
rc  cups-pdf                                   2.5.0-1ubuntu1                       PDF printer for CUPS
rc  libavutil49                                3:0.svn20080206-12ubuntu3.1          ffmpeg utility library
rc  libqt4-dbus                                4.4.3-0ubuntu1.2                     Qt 4 D-Bus module
rc  libqt4-designer                            4.4.3-0ubuntu1.2                     Qt 4 designer module
rc  libqt4-network                             4.4.3-0ubuntu1.2                     Qt 4 network module
rc  libqt4-qt3support                          4.4.3-0ubuntu1.2                     Qt 3 compatibility library for Qt 4
rc  libqt4-script                              4.4.3-0ubuntu1.2                     Qt 4 script module
rc  libqt4-sql                                 4.4.3-0ubuntu1.2                     Qt 4 SQL module
rc  libqt4-xml                                 4.4.3-0ubuntu1.2                     Qt 4 XML module
rc  libqtcore4                                 4.4.3-0ubuntu1.2                     Qt 4 core module
rc  libqtgui4                                  4.4.3-0ubuntu1.2                     Qt 4 GUI module
rc  libsdl1.2debian-alsa                       1.2.13-2ubuntu1                      Simple DirectMedia Layer (with X11 and ALSA 
rc  libsdl1.2debian-pulseaudio                 1.2.13-4ubuntu3                      Simple DirectMedia Layer (with X11 and Pulse
rc  linux-image-2.6.27-11-generic              2.6.27-11.31                         Linux kernel image for version 2.6.27 on x86
rc  myspell-en-us                              1:2.4.0~m240-1ubuntu1                English_american dictionary for myspell
rc  nautilus-cd-burner                         2.24.0-0ubuntu1                      CD Burning front-end for Nautilus
rc  nvidia-glx-177                             177.82-0ubuntu0.1                    NVIDIA binary Xorg driver
rc  nvidia-glx-new                             169.12+2.6.24.14-21.51               NVIDIA binary XFree86 4.x/X.Org 'new' driver
rc  powernowd                                  1.00-1ubuntu5                        control cpu speed and voltage using 2.6 kern
rc  python2.5                                  2.5.4-1ubuntu4                       An interactive high-level object-oriented la
rc  python2.5-minimal                          2.5.4-1ubuntu4                       A minimal subset of the Python language (ver
rc  qt4-qtconfig                               4.4.3-0ubuntu1.2                     Qt 4 configuration tool
rc  scrollkeeper                               0.3.14-16ubuntu1                     A free electronic cataloging system for docu

```

```

$ deborphan --find-config
$

```

---

