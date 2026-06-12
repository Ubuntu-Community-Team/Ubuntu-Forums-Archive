---
title: "Calibre (epub reader) install totally hosed my desktop"
date: 2016-08-27
forum: Desktop Environments
---

### Post by watchpocket on 2016-08-27
So I installed *Calibre* -- the ebook reader -- on my Xenial drive and noticed right away that the icons on my  top-panel & my desktop were suddenly all-white with a red "X" on them.

I re-booted, and the login screen was black (background image totally not there), but the username & password boxes still appeared, so at least I could log in. 

The second I was logged in, instantly the entire screen on both my monitors did this whole BLINK-BLINK-BLINK-BLINK thing and just kept flickering like that.  So I can't use my 16.04 system and am posting this from my 14.04 drive.

I installed Calibre according to the instructions on its download page [here]("https://calibre-ebook.com/download_linux"). The command used was this:
```
sudo -v && wget -nv -O- https://raw.githubusercontent.com/kovidgoyal/calibre/master/setup/linux-installer.py | sudo python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()"
``` 

I later removed Calibre  with the recommended "sudo calibre-uninstall" but of course the desktop was, and is, still broken.

On the download page, below the install command, it says: 

[I]"You must have xdg-utils, wget and python &#8805; 2.6 installed on your system before running the installer."
[/I]
Since I have python 3.5 installed (and xdg-utils and wget), I didn't anticipate a problem.  I made sure I had current versions of all of Calibre's dependencies.

[I][Brief update: I've discovered I can enter commands in 16.04 at the terminal between the flickering. Reinstalling from scratch just isn't an option, except as an absolutely final final last-ditch effort.  I'm going to try everything I can before I get to that point.]
[/I]
Can anyone suggest what further steps I might take to recover a functioning desktop in this situation?  Thanks.

---

### Post by philhughes on 2016-08-28
I can't help much, except to say I have seen the exact same thing (straight Ubuntu, pre 16.04). It was a while ago now, and I tried a bunch of stuff I can't remember to try and get the desktop back, but failed and ended up reinstalling. I tried another Calibre installation on the fresh installation, and the exact same thing happened.

I haven't reported it in the Calibre forums on Mobileread, as I didn't see any other reports there and assumed it was something peculiar to my system, but maybe not. You could try posting there, the developer is very helpful.

---

### Post by watchpocket on 2016-08-28
Thanks, I'll go ahead & post the problem on Mobileread.  It's particularly bad that Calibre causes this (for others as well as myself).  Still looking for a solution, any suggestions appreciated.

---

### Post by watchpocket on 2016-08-29
@philhughes: 
> the developer is very helpful.

I take it this just your observation of the developer's presence on the Mobileread Calibre forum, and not from direct communication with him, yes? 

I've [posted]("http://www.mobileread.com/forums/showthread.php?t=277803") what happened to on the Mobileread Calibre forum and solicited the developer's help as to what might have caused this fiasco. 

 I'm still trying to track down the problem.  

I installed that program as responsibly as I could, and IMO the developer owes it to Linux users of his program to look into it, if what happened to me and what happened to you -- twice for you, as you say -- is happening to others trying to install Calibre on Ubuntu.

---

### Post by philhughes on 2016-08-30
Responsive might have been a better word ;) To be fair, without further detail and without being able to reproduce it, it is difficult for anyone to help. For what it's worth, I just did a fresh install of Ubuntu 16.04.1 on an old laptop, did all the updates and then installed Calibre as shown on the website, and the problem didn't occur.

In terms of restoring your desktop, I suspect the quickest way will be a reinstall.

---

### Post by watchpocket on 2016-09-03
I am stumped as to how to tackle the problem of a flickering, strobe-light-like desktop.

I did create and log into a 2nd user-account on the same system, to see if the problem persisted there.

Everything is fine on the 2nd desktop ***except*** that all icons there are white, with a red "X" inside of them.  (This icon problem is also on the main, flickering desktop.)

I ***am*** able to enter terminal commands between the flickers on the main desktop. 

 I can also access the virtual terminal (but I cannot get a network connection from the virtual terminal).

What steps might others take to try to begin to track down such a problem?

/var/log/syslog shows: ```
Sep  3 19:49:45 rjbox mate-session[4610]: WARNING: Could not launch application 'ubuntu-mate-welcome.desktop': Unable to start application: Failed to execute 
  child process "ubuntu-mate-welcome" (No such file or directory)
```

Also: ```
Sep  3 19:49:48 rjbox org.mate.panel.applet.TrashAppletFactory[4756]: (trashapplet:4875): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format 
Sep  3 19:49:48 rjbox org.mate.panel.applet.WnckletFactory[4756]: Failed to load user-desktop: Unrecognized image file format 
Sep  3 19:49:48 rjbox org.mate.panel.applet.WnckletFactory[4756]: (wnck-applet:4873): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format 
Sep  3 19:49:49 rjbox org.gtk.vfs.Daemon[4756]: ** (gvfsd:4853): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused 
Sep  3 19:49:49 rjbox org.gtk.vfs.Daemon[4756]: ** (process:5095): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted 
Sep  3 19:50:05 rjbox mate-session[4610]: Gtk-WARNING: Error loading theme icon 'gtk-cancel' for stock: Unrecognized image file format 
Sep  3 19:50:05 rjbox mate-session[4610]: Gtk-WARNING: Error loading theme icon 'image-missing' for stock: Unrecognized image file format 
Sep  3 19:50:07 rjbox systemd[1]: Stopping Session c1 of user lightdm. 
```

---

### Post by Bashing-om on 2016-09-03
watchpocket; Hey ...

Have you looked at the DE log file ?
```

cat .xsession-errors

```
and verified that the driver is installed and no conflicts ?
```

dpkg -l | grep -i nvidia
sudo lshw -C display

```


What now does the package manager think - with a working internet connection ! - ?
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]many times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2016-09-04
.xsession-errors shows the following. (I can access that from my 14.04 drive).  I'll try to do the other commands on the problem system itself.
```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
mate-session[6442]: WARNING: Unable to find provider '' of required component 'dock'

** (mate-panel:6699): WARNING **: couldn't get background pixmap

** (mate-panel:6699): WARNING **: couldn't get background pixmap

Sep 03 23:24 : socket: Failed to bind to '127.0.0.1:6600': Address already in use

** (process:6774): WARNING **: Warning: show_on_monitor_number is no longer a valid config option for the current version of Tilda.

** (process:6774): WARNING **: Warning: scroll_background is no longer a valid config option for the current version of Tilda.

** (process:6774): WARNING **: Warning: use_image is no longer a valid config option for the current version of Tilda.

(update-notifier:6729): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/TraditionalOkTest/gtk-3.0/img/border.svg': Unrecognized image file format

(update-notifier:6729): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/TraditionalOkTest/gtk-3.0/img/border-insensitive.svg': Unrecognized image file format
grep: /home/rj/.xinputrc: No such file or directory

(nm-applet:6771): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/TraditionalOkTest/gtk-3.0/img/border.svg': Unrecognized image file format

(nm-applet:6771): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/TraditionalOkTest/gtk-3.0/img/border-insensitive.svg': Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/TraditionalOkTest/gtk-3.0/img/border.svg': Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/TraditionalOkTest/gtk-3.0/img/border-insensitive.svg': Unrecognized image file format

** (mate-panel:6699): WARNING **: couldn't get background pixmap


(mate-panel:6699): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

** (mate-panel:6699): WARNING **: couldn't get background pixmap

** Gtk:ERROR:/build/gtk+2.0-KsZKkB/gtk+2.0-2.24.30/gtk/gtkrecentmanager.c:2116:get_icon_fallback: assertion failed: (retval != NULL)

(mate-volume-control-applet:6788): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format
/usr/lib/python2.7/dist-packages/variety/__init__.py:105: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version $
  from gi.repository import Gtk, Gdk, GObject # pylint: disable=E0611

(nm-applet:6771): nm-applet-WARNING **: failed to load icon "nm-device-wired": Unrecognized image file format

(nm-applet:6771): nm-applet-WARNING **: failed to load icon "nm-signal-50": Unrecognized image file format

(nm-applet:6771): nm-applet-WARNING **: failed to load icon "nm-secure-lock": Unrecognized image file format

(nm-applet:6771): nm-applet-WARNING **: failed to load icon "nm-signal-75": Unrecognized image file format

(nm-applet:6771): nm-applet-WARNING **: failed to load icon "nm-signal-25": Unrecognized image file format
/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py:50: RuntimeWarning: You have imported the Gtk 2.0 module.  Because Gtk 2.0 was not designed for use with introspection some of the interfaces and API will $
  warnings.warn(warn_msg, RuntimeWarning)

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format
/usr/lib/mate-optimus/mate-optimus-applet:7: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk

(tilda:6774): Gtk-WARNING **: Error loading theme icon 'image-missing' for stock: Unrecognized image file format

(tilda:6774): GLib-GObject-CRITICAL **: g_object_ref: assertion 'G_IS_OBJECT (object)' failed

(tilda:6774): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** (caja:6723): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (caja:6723): WARNING **: Can not get _NET_WORKAREA

** (caja:6723): WARNING **: Can not determine workarea, guessing at layout
**
Gtk:ERROR:/build/gtk+2.0-KsZKkB/gtk+2.0-2.24.30/gtk/gtkrecentmanager.c:2116:get_icon_fallback: assertion failed: (retval != NULL)
/usr/lib/python2.7/dist-packages/variety/VarietyWindow.py:25: PyGIWarning: Notify was imported without specifying a version first. Use gi.require_version('Notify', '0.7') before import to ensure that the righ$
  from gi.repository import Gtk, Gdk, GdkPixbuf, GObject, Gio, Notify # pylint: disable=E0611
/usr/lib/python2.7/dist-packages/variety/AddPanoramioDialog.py:19: PyGIWarning: WebKit was imported without specifying a version first. Use gi.require_version('WebKit', '3.0') before import to ensure that the$
  from gi.repository import Gtk, WebKit, GObject # pylint: disable=E0611
/usr/lib/python2.7/dist-packages/variety/QuoteWriter.py:19: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that th$
  from gi.repository import Gdk, Pango, PangoCairo, GdkPixbuf, GObject
/usr/lib/python2.7/dist-packages/variety/indicator.py:30: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure tha$
  from gi.repository import AppIndicator3 # pylint: disable=E0611
INFO: 2016-09-03 23:24:20,387: perform_upgrade() 'Last run version was 0.6.2 or earlier, current version is 0.6.2'
INFO: 2016-09-03 23:24:20,388: process_command() 'Received command: []'
INFO: 2016-09-03 23:24:20,391: load_banned() 'Missing or invalid banned URLs list, no URLs will be banned'
/home/rj/.config/variety/scripts/get_wallpaper: line 32: mateconftool-2: command not found
ERROR: 2016-09-03 23:24:20,430: get_desktop_wallpaper() 'Exception when calling get_wallpaper script'

```

---

### Post by watchpocket on 2016-09-04
```

~$ dpkg -l | grep -i nvidia
ii  libcublas7.5:amd64                                          7.5.18-0ubuntu1                                     amd64        NVIDIA cuBLAS Library
ii  libcuda1-367                                                367.44-0ubuntu0~gpu16.04.1                          amd64        NVIDIA CUDA runtime library
ii  libcudart7.5:amd64                                          7.5.18-0ubuntu1                                     amd64        NVIDIA CUDA Runtime Library
ii  libcufft7.5:amd64                                           7.5.18-0ubuntu1                                     amd64        NVIDIA cuFFT Library
ii  libcufftw7.5:amd64                                          7.5.18-0ubuntu1                                     amd64        NVIDIA cuFFTW Library
ii  libcuinj64-7.5:amd64                                        7.5.18-0ubuntu1                                     amd64        NVIDIA CUINJ Library (64-bit)
ii  libcurand7.5:amd64                                          7.5.18-0ubuntu1                                     amd64        NVIDIA cuRAND Library
ii  libcusolver7.5:amd64                                        7.5.18-0ubuntu1                                     amd64        NVIDIA cuSOLVER Library
ii  libcusparse7.5:amd64                                        7.5.18-0ubuntu1                                     amd64        NVIDIA cuSPARSE Library
ii  libnppc7.5:amd64                                            7.5.18-0ubuntu1                                     amd64        NVIDIA Performance Primitives core runtime library
ii  libnppi7.5:amd64                                            7.5.18-0ubuntu1                                     amd64        NVIDIA Performance Primitives for image processing runtime library
ii  libnpps7.5:amd64                                            7.5.18-0ubuntu1                                     amd64        NVIDIA Performance Primitives for signal processing runtime library
ii  libnvrtc7.5:amd64                                           7.5.18-0ubuntu1                                     amd64        CUDA Runtime Compilation (NVIDIA NVRTC Library)
ii  libnvtoolsext1:amd64                                        7.5.18-0ubuntu1                                     amd64        NVIDIA Tools Extension Library
ii  libnvvm3:amd64                                              7.5.18-0ubuntu1                                     amd64        NVIDIA NVVM Library
ii  mate-optimus                                                1.0.0-1                                             all          MATE Desktop applet for controlling NVIDIA Optimus graphics cards
rc  nvidia-304                                                  304.131-0ubuntu3                                    amd64        NVIDIA legacy binary driver - version 304.131
rc  nvidia-304-updates                                          304.131-0ubuntu3                                    amd64        NVIDIA legacy binary driver - version 304.131
rc  nvidia-340                                                  340.96-0ubuntu3                                     amd64        NVIDIA binary driver - version 340.96
rc  nvidia-361                                                  361.45.11-0ubuntu0~gpu16.04.1                       amd64        NVIDIA binary driver - version 361.45.11
ii  nvidia-367                                                  367.44-0ubuntu0~gpu16.04.1                          amd64        NVIDIA binary driver - version 367.44
ii  nvidia-cuda-dev                                             7.5.18-0ubuntu1                                     amd64        NVIDIA CUDA development files
ii  nvidia-cuda-doc                                             7.5.18-0ubuntu1                                     all          NVIDIA CUDA and OpenCL documentation
ii  nvidia-cuda-gdb                                             7.5.18-0ubuntu1                                     amd64        NVIDIA CUDA Debugger (GDB)
ii  nvidia-cuda-toolkit                                         7.5.18-0ubuntu1                                     amd64        NVIDIA CUDA development toolkit
ii  nvidia-opencl-dev:amd64                                     7.5.18-0ubuntu1                                     amd64        NVIDIA OpenCL development files
rc  nvidia-opencl-icd-304                                       304.131-0ubuntu3                                    amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-304-updates                               304.131-0ubuntu3                                    amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-340                                       340.96-0ubuntu3                                     amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-361                                       361.45.11-0ubuntu0~gpu16.04.1                       amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-367                                       367.44-0ubuntu0~gpu16.04.1                          amd64        NVIDIA OpenCL ICD
rc  nvidia-prime                                                0.8.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-profiler                                             7.5.18-0ubuntu1                                     amd64        NVIDIA Profiler for CUDA and OpenCL
ii  nvidia-settings                                             370.23-0ubuntu0~gpu16.04.1                          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-visual-profiler                                      7.5.18-0ubuntu1                                     amd64        NVIDIA Visual Profiler for CUDA and OpenCL
ii  system76-driver-nvidia                                      16.04.8                                             all          Latest nvidia driver for System76 computers

```

---

### Post by watchpocket on 2016-09-04
When I enter ```
sudo lshw
```

the screen turns black with a blinking white cursor in the upper left.  (And this is on the drive I'm posting from now which has UbuntuMate 14.04.  The problem system is 16.04 and is on another drive (SSD).

---

### Post by Bashing-om on 2016-09-04
watchpocket; Well ...

I am torn as to which way to look at this .
Do we have a driver conflict between:
> 
ii  nvidia-367 
ii  system76-driver-nvidia

 and or maybe .. the DE wall paper configs are hosed ??

We got any info for the system76 driver ?
```

apt show system76-driver-nvidia

```
same same function as the PPA driver 367 ?

And what alternative DE's are installed - of any others ?
```

echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
ls -al /usr/share/xsessions
apt-cache policy ubuntu-desktop
cat /etc/X11/default-display-manager

```

Mind ya I have never seen the Mate DE. do not know what to expect here .

[INDENT][INDENT]poke poke poke
[INDENT][INDENT]'til something gives
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2016-09-04
> **Bashing-om said:**
> 
We got any info for the system76 driver ?
```

apt show system76-driver-nvidia

```
Here is a more fundamental question about entering commands between drives:  

I obviously am logged into my drive that has a working 14.04 system and net connection.  But we're trying to discover things about the malfunctioning 16.04 system, which is on a separate (SSD) drive.  For a command like ***cat .xsession-errors***, as long as I have the 16.04 drive mounted on my 14.04 desktop, I can easily enter a command (from a 14.04 terminal) like:

[I][B]cat /media/rj/UbuntuMATE-16.04/home/rj/.xsession-errors
[/B][/I]
and have immediate access to the output of that 16.04 homedir file, right there at the 14.04 terminal.  

But for a command like ***apt show system76-driver-nvidia***, I'm not sure if there is a way to do that from the 14.04 drive & terminal, or if the only way to do it is to log out of drive/system 14.04, log into drive/system 16.04, and do it from there.  Is there a way to do it from the 14.04 drive?

(In other words accessing a 16.04-drive **file** from a 14.04-drive terminal is easy,  accessing 16.04-drive **command-output** may require actually being logged into 16.04.)

If there is a way to do it from 14.04, it would greatly help speed things up.  If not, I'll just go ahead and switch between the systems, and access command-outputs by sending them to a file when I'm in 16.04, and then accessing that file from 14.04.  Thanks for any clarification on this point.

---

### Post by Bashing-om on 2016-09-04
watchpocket; Well ...

How about we take the graphic's driver out of the equation ?
Then see what we have.
Boot the 16.04 hard drive to the grub boot menu, and let's boot to a terminal:
at the grub menu 'e' key for edit mode -> boot parameters screen;
arrow down to the line " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " and replace quiet splash and all after with " systemd.unit=multi-user.target" - with out the quotes .
Key combo ctl+x to continue the boot process to TTY1.
log in here with user name and password.
we may want networking, and will have to tell the system so:
```

systemctl enable NetworkManager.service
systemctl start NetworkManager.service

```

Do we have a working interface ?
```

ping -c3 ubuntu.com

```

now what returns:
```

apt show system76-driver-nvidia

```

as a place to see what is .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2016-09-04
Before I respond to your most recent post, I do have the output of all the commands you asked for previously.  Here it is:
```
*--> apt show system76-driver-nvidia*
Package: system76-driver-nvidia
Version: 16.04.9
Priority: extra
Section: utils
Source: system76-driver
Maintainer: System76, Inc. <dev@system76.com>
Installed-Size: 21.5 kB
Depends: system76-driver (>= 16.04.9), ubuntu-drivers-common, nvidia-367
Download-Size: 8,834 B
APT-Manual-Installed: yes
APT-Sources: http://ppa.launchpad.net/system76-dev/stable/ubuntu xenial/main amd64 Packages
Description: Latest nvidia driver for System76 computers
 This dummy package depends on the latest driver tested with and recommended for
 System76 products with an nvidia GPU.
 .
 When this package is installed, you will automatically be upgraded to newer
 nvidia driver versions after System76 has thouroughly tested them.
 .
 This driver will generally depend on a newer nvidia driver than the official
 nvidia-current-updates Ubuntu package.
 .
 If you don't want to be automatically upgraded to newer nvidia drivers, simply
 remove this package.
```

```
[I]
\--> sudo lshw -C display[/I]
  *-display
       description: VGA compatible controller
       product: GF106 [GeForce GTS 450]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:35 memory:ec000000-ecffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:e000(size=128) memory:ee000000-ee07ffff

```

```
*--> echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP*
mate   MATE

```

```
*--> ls -al /usr/share/xsessions*
total 32
 4 drwxr-xr-x   2 root root  4096 Aug 17 14:52 ./
20 drwxr-xr-x 492 root root 20480 Aug 29 02:01 ../
 8 -rw-r--r--   1 root root  6756 Aug 17 10:51 mate.desktop

```

```
*--> apt-cache policy ubuntu-desktop*
ubuntu-desktop:
  Installed: (none)
  Candidate: (none)
  Version table:

```

```
*--> cat /etc/X11/default-display-manager*
/usr/sbin/lightdm

```

---

### Post by Bashing-om on 2016-09-04
watchpocket; Welp;

Read what the apt show output ? shows :
> 
If you don't want to be automatically upgraded to newer nvidia drivers, simply
 remove this package.


I read it that If one installs the nVidia driver, then we have a driver conflict . 
What do you reckon ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2016-09-04
So I should remove either the one or the other -- I should remove either the *system76-driver-nvidea 16.04.8*, or remove the *nvidia-367.44* driver.

If I remove the system76 driver, and also remove it from synaptic (so that I don't continue to get auto-updates for the system76 drivers), and leave the 367.44 nvidia driver, (as well as  leave the line* deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial main*
in /etc/apt/sources, so that I can continue to get updates from it -- right now I'm getting driver updates from both, which probably isn't good), I shouldn't have a conflict.  

And if I don't have that conflict between the 2 drivers, I shouldn't have a flickering screen.  

I just wonder why they never conflicted with each other before.  Maybe it was an accident waiting to be triggered by something. (like the installation of Calibre).

If there's anything I might need to know before I remove the system76 driver, let me know.  Otherwise I'll go ahead and uninstall it.

---

### Post by CantankRus on 2016-09-04
**system76-driver-nvidia** installs the the latest nvidia driver tested by system76, which I believe is **nvidia-367**.
> **system76-driver-nvidia**
This dummy package depends on the latest driver tested with and recommended for
System76 products with an nvidia GPU.

When this package is installed, you will automatically be upgraded to newer
nvidia driver versions after System76 has thouroughly tested them.

This driver will generally depend on a newer nvidia driver than the official
nvidia-current-updates Ubuntu package.

The **graphics-drivers/ppa**  contains the nvidia-370 driver which has not been tested by system76 so you should purge that ppa.

PS: For calibre I would be looking at python version issues.

---

### Post by Bashing-om on 2016-09-04
watchpocket; Yeahl

I am with you in that I would prefer the PPA 367 version driver , so yeah uninstall the system76-driver-nvidia package.
However, we do not know how system76-driver-nvidia calls home . Might check sources and see what references exist ?
This might turn into a learning experience for the both of us !  I have yet to lay my hands on a system76 so we may have to fumble our way around a bit .

[INDENT][INDENT]just what I wud do
[/INDENT][/INDENT]

---

### Post by watchpocket on 2016-09-04
> **CantankRus said:**
> **system76-driver-nvidia** installs the the latest nvidia driver tested by system76, which I believe is **nvidia-367**.

As long as I've got the right version for my graphics card, according to the GeForce site, I should be allright, is my thinking.

I realize that by not sticking with the system76-tested I'm "walking on the wild side" just a bit, but at the moment I'm inclined to not worry about the testing and go with the graphics PPA.  I'll keep the sys76 PPA (so I get other system76 stuff, though even that is mostly minor stuff like wallpaper) but I'll un-install the sys76 driver in synaptic.  If I get a problem from a new driver from graphics-driver PPA I'll swap it out for the sys76 tested driver.

(Re: Calibre, I uninstalled it the minute it (or something associated with it -- I have the right python version) corrupted the desktop.)

Which command would be better for this -- 

[I]sudo apt install --uninstall system76-driver-nvidia 

or

sudo apt purge system76-driver-nvidia[/I]

(To answer my own question, the ***apt*** command doesn't have the word "purge" in its manpage, but the **apt-get** manpage says that "purge is identical to remove except that packages are removed and purged (any configuration files are deleted too)."

By the way, is it OK to uncheck the deb-src line below a deb line, in etc/apt/sources.list?  Are there any consequences to that?  I don't generally need source code.

---

### Post by Bashing-om on 2016-09-04
watchpocket; Hey;

Hold onto your horses.
I would not think that the launchpad PPA for system76 has anything directly to do with the driver.

As to src codes sources, In my work install I have no need of source code and all sources for src are commented out . Makes for a much faster update process too .

sudo apt purge system76-driver-nvidia should workie great for this use case .


[INDENT][INDENT]keep'n it clean
[/INDENT][/INDENT]

---

### Post by CantankRus on 2016-09-04
> **watchpocket said:**
> By the way, is it OK to uncheck the deb-src line below a deb line, in etc/apt/sources.list?  Are there any consequences to that?  I don't generally need source code.
Yes.
After adding a ppa I open the software and updates gui (software-properties-gtk --open-tab=1) and remove the source line and then edit the ppa to show what it contains.
The "Comment" field will replace the ppa URI.

---

### Post by watchpocket on 2016-09-04
Right I was planning on keeping the system76 launchpad ppa, and just uninstalling the system76-driver-nvidia package.  I'm going to do that right now.  If the flickering persists, I'll have to continue troubleshooting.

---

### Post by watchpocket on 2016-09-04
> [I]The "Comment" field will replace the ppa URI.

[/I]Oh, that's a great idea --  I have all these PPAs & look at them and don't know why I installed any particular PPA. Now I can identify them. Thanks for the tip!

---

### Post by watchpocket on 2016-09-04
So I've purged both *system76-driver-nvidia* and autoremoved *system76-driver*, rebooted, no change.  Next step is to look further through the .xsession-errors file.

In fact my 16.04 .xsession-errors file is a bit of a train-wreck.  Looking at its first several lines alone leaves me not knowing where to start:
```

openConnection: connect: No such file or directory  
cannot connect to brltty at :0 
mate-session[4376]: WARNING: Unable to find provider '' of required component 'dock' 
Sep 04 23:46 : socket: Failed to bind to '127.0.0.1:6600': Address already in use  

(update-notifier:4650): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/TraditionalOkTest/gtk-3.0/img/border.svg': Unrecognized image file format 

(update-notifier:4650): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/TraditionalOkTest/gtk-3.0/img/border-insensitive.svg': Unrecognized image file format

```
Update: the first 2 lines aren't errors. They're just debugging messages. They come from xbrlapi which is trying to connect to a braille display, but I, we generally have none, so it can't. Nothing to worry about, apparently.

 But, I'm still back at square one, with a flickering desktop, looking for any possible attack vector.

---

### Post by Bashing-om on 2016-09-05
watchpocket; Welp;

How about we take a look and see what X has to say about the driver build ?
```

cat /var/log/Xorg.0.log 

``` and what might be taking place within the X layer.

[INDENT][INDENT]when all else fails;
[INDENT][INDENT][INDENT]read the instructions ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2016-09-06
See [https://paste.ubuntu.com/23140022/](https://paste.ubuntu.com/23140022/)  for the Xorg.0.log file. Thanks for sticking with this.

---

### Post by Bashing-om on 2016-09-06
watchpocket; Well ...

I am at a loss, 

I do not understand why or what 

> 
->Device "System76 nVidia Card"

this means . 

Nor do I recognize why 
numerous :
> 
[m[34m*.......[

should appear or what they signify . Never ever seen such before.

[INDENT][INDENT]just not a thing I can add at this point
[/INDENT][/INDENT]

---

### Post by watchpocket on 2016-09-06
->Device "System76 nVidia Card"

That may be a leftover from yesterday.  The date there is yesterday at any rate.

Ok thanks, I'm going to pick this up tomorrow when I'm a bit fresher, thanks for looking at that.

---

### Post by watchpocket on 2016-09-12
This issue was solved today with a simple upgrade using the Software Updater.  I think a new version of the MATE desktop was updated, and I think this was as a result of my having added a key ubuntu-mate repository that I did not previoulsy have in my software sources.

---

