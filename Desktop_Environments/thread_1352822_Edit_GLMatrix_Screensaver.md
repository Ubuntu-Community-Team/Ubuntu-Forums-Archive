---
title: "Edit GLMatrix Screensaver"
date: 2009-12-12
forum: Desktop Environments
---

### Post by blue_ on 2009-12-12
Hello All, I am new around here so hope I am posting this in the correct section. I am not a pro at Linux or anything. I have used it on servers for the last 5 years, I understand most the basics but haven't really compiled anything until I installed Ubuntu on my desktop.


My Main question is has anyone ever edited the GLMatrix and recompiled it on karmic/gnome? If so can you tell if I am doing anything wrong? If you haven't and have any insight it would be greatly appreciated. 


I am trying to edit the GLmatrix screen saver to change the color from Green to Blue. I tried to use this tutorial [http://santhoshtr.livejournal.com/7078.html](http://santhoshtr.livejournal.com/7078.html) for the basics on how to do it. It is not for the color its for the text but same process I believe. What I did was download the source then edited the xpm file to make it blue an changed GLMatrix.c to the new module "Blue Matrix" as the tutorial says then when I recompiled I receive a error


First Error
.configure runs through checks for a few seconds then posts this error.
```
configure: error: Couldn't find X11 headers/libs.  Try `./configure --help'.
```After googling around awhile I found out this was because the libs weren't included so I ran this.

 ./configure --x-includes=/usr/include --x-libraries=/usr/lib

The first time I ran it, it only gave me 1 warning so I thought it configured but there was no make file to run to finish the compile? I believe the warning was in regards to XPM Library but can't really remember.

In frustration I thought maybe it was because gnome-screensaver and a bunch of xscreensavers were installed so I completely removed everything having to do with screen saver. Tried to configure it again and received a bunch of warnings for library's missing. So I re-installed gnome-screensaver and xscreensaver-gl. 

Now when I try to configure it with ./configure --x-includes=/usr/include --x-libraries=/usr/lib I receive this.

```

Above this was a bunch of checks didn't think you needed them if you do let me know.

configure: creating ./config.status
config.status: creating Makefile
config.status: creating utils/Makefile
config.status: creating driver/Makefile
config.status: creating hacks/Makefile
config.status: creating hacks/glx/Makefile
config.status: creating po/Makefile.in
config.status: creating driver/XScreenSaver.ad
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
config.status: executing default-2 commands

    #################################################################

    Warning: The GTK libraries do not seem to be available; the
             `xscreensaver-demo' program requires them.

    Warning: The GDK-Pixbuf library was not found.

    Warning: The XPM library was not found.

             Some of the demos will not use images as much as they could.
             You should consider installing GDK-Pixbuf and re-running
             configure.  (GDK-Pixbuf is recommended over XPM, as it
             provides support for more image formats.)

       Note: The JPEG library was not found.
             This means that it won't be possible for the image-manipulating
             display modes to load files from disk; and it also means that
             the `webcollage' program will be much slower.

       Note: The OpenGL 3D library was not found.

             Those demos which use 3D will not be built or installed.
             You might want to consider installing OpenGL and
             re-running configure.  If your vendor doesn't ship
             their own implementation of OpenGL, you can get a free
             version at <http://www.mesa3d.org/>.  For general OpenGL
             info, see <http://www.opengl.org/>.

    #################################################################

    Warning: There is already an installed dpkg of xscreensaver
             version "5.08-0ubuntu5" on this system.

             The dpkg was installed in ???,
             with demos in /usr/lib/xscreensaver/.

    #################################################################

User programs will be installed in /usr/local/bin/
Screen savers will be installed in /usr/local/libexec/xscreensaver/
Configuration dialogs will be installed in /usr/local/share/xscreensaver/config/
System-wide default settings will be installed in /usr/lib/X11/app-defaults/

```Am I just missing running another command after I do .configure or what. Also what are the Library's it says I am missing i checked and I have libxpm4, libjpeg62, libqt4-opengl ect so why is it sending me warnings saying there not installed?

Thanks in advance,
Blue_

---

### Post by drinky76 on 2010-10-20
Sorry to reply so long after your post, but I came across it while I was googling something related to GLMatrix.

My bet is you're missing the build dependencies, these are the libraries and header files used when compiling something. They're not normally required on a regular desktop system so they won't be installed.

You need to do 2 things. Install the build-essential package. This provides the compilers and basic libs. Then install the build dependencies for the package which provides the GLMatrix screensaver, which I thought would be xscreensaver, but that is not installed on my system, so maybe the build-deps for gnome-screensaver instead. Maybe install the build-deps for both if you're having trouble ;)

You can install build-deps without working out what they are by using:

apt-get build-dep <packagename>

Hope that's enough to point you in the right direction. Sorry if it's not the right solution.

---

