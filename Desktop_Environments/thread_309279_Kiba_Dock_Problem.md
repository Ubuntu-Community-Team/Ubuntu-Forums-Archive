---
title: "Kiba Dock Problem"
date: 2006-11-29
forum: Desktop Environments
---

### Post by Nirva on 2006-11-29
Hi,

I tried installing Kiba-dock so I followed some manuals.  This is what I did :

sudo aptitude install build-essential automake cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev libglade2-dev

Then I made sure I had automake 1.9 instead of 1.4.


cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock

cd ./kiba-dock

filip@Filip:~/kiba-dock$ sudo ./autogen.sh



autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/filip/kiba-dock/missing: Unknown `--run' option
Try `/home/filip/kiba-dock/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for gettimeofday... yes
checking for memset... yes
checking for sqrt... no
checking for strrchr... yes
checking for strstr... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for GTK... yes
checking for CAIRO... yes
checking for PANGO... yes
checking for GCONF... yes
checking for GLADE... yes
checking for SVG... yes
checking for GLITZ... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating akamaru/Makefile
config.status: creating dock/Makefile
config.status: creating gset-kiba/Makefile
config.status: creating icons/Makefile
config.status: creating utils/Makefile
config.status: creating files/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands



filip@Filip:~/kiba-dock$ sudo make



make  all-recursive
make[1]: Entering directory `/home/filip/kiba-dock'
Making all in akamaru
make[2]: Entering directory `/home/filip/kiba-dock/akamaru'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/filip/kiba-dock/akamaru'
Making all in dock
make[2]: Entering directory `/home/filip/kiba-dock/dock'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/filip/kiba-dock/dock'
Making all in gset-kiba
make[2]: Entering directory `/home/filip/kiba-dock/gset-kiba'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/filip/kiba-dock/gset-kiba'
Making all in icons
make[2]: Entering directory `/home/filip/kiba-dock/icons'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/filip/kiba-dock/icons'
Making all in utils
make[2]: Entering directory `/home/filip/kiba-dock/utils'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/filip/kiba-dock/utils'
Making all in files
make[2]: Entering directory `/home/filip/kiba-dock/files'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/filip/kiba-dock/files'
make[2]: Entering directory `/home/filip/kiba-dock'
make[2]: Leaving directory `/home/filip/kiba-dock'
make[1]: Leaving directory `/home/filip/kiba-dock'




filip@Filip:~/kiba-dock$ sudo make install



Making install in akamaru
make[1]: Entering directory `/home/filip/kiba-dock/akamaru'
make[2]: Entering directory `/home/filip/kiba-dock/akamaru'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'akamaru' '/usr/bin/akamaru'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/filip/kiba-dock/akamaru'
make[1]: Leaving directory `/home/filip/kiba-dock/akamaru'
Making install in dock
make[1]: Entering directory `/home/filip/kiba-dock/dock'
make[2]: Entering directory `/home/filip/kiba-dock/dock'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'kiba-dock' '/usr/bin/kiba-dock'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/filip/kiba-dock/dock'
make[1]: Leaving directory `/home/filip/kiba-dock/dock'
Making install in gset-kiba
make[1]: Entering directory `/home/filip/kiba-dock/gset-kiba'
make[2]: Entering directory `/home/filip/kiba-dock/gset-kiba'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'gset-kiba' '/usr/bin/gset-kiba'
test -z "/usr/share/kiba-dock" || mkdir -p -- "/usr/share/kiba-dock"
 /usr/bin/install -c -m 644 'gset-kiba.glade' '/usr/share/kiba-dock/gset-kiba.glade'
make[2]: Leaving directory `/home/filip/kiba-dock/gset-kiba'
make[1]: Leaving directory `/home/filip/kiba-dock/gset-kiba'
Making install in icons
make[1]: Entering directory `/home/filip/kiba-dock/icons'
make[2]: Entering directory `/home/filip/kiba-dock/icons'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/icons/hicolor/128x128/apps" || mkdir -p -- "/usr/share/icons/hicolor/128x128/apps"
 /usr/bin/install -c -m 644 'kiba_128.png' '/usr/share/icons/hicolor/128x128/apps/kiba_128.png'
test -z "/usr/share/icons/hicolor/16x16/apps" || mkdir -p -- "/usr/share/icons/hicolor/16x16/apps"
 /usr/bin/install -c -m 644 'kiba_16.png' '/usr/share/icons/hicolor/16x16/apps/kiba_16.png'
test -z "/usr/share/icons/hicolor/24x24/apps" || mkdir -p -- "/usr/share/icons/hicolor/24x24/apps"
 /usr/bin/install -c -m 644 'kiba_24.png' '/usr/share/icons/hicolor/24x24/apps/kiba_24.png'
test -z "/usr/share/icons/hicolor/48x48/apps" || mkdir -p -- "/usr/share/icons/hicolor/48x48/apps"
 /usr/bin/install -c -m 644 'kiba_48.png' '/usr/share/icons/hicolor/48x48/apps/kiba_48.png'
test -z "/usr/share/icons/hicolor/64x64/apps" || mkdir -p -- "/usr/share/icons/hicolor/64x64/apps"
 /usr/bin/install -c -m 644 'kiba_64.png' '/usr/share/icons/hicolor/64x64/apps/kiba_64.png'
make[2]: Leaving directory `/home/filip/kiba-dock/icons'
make[1]: Leaving directory `/home/filip/kiba-dock/icons'
Making install in utils
make[1]: Entering directory `/home/filip/kiba-dock/utils'
make[2]: Entering directory `/home/filip/kiba-dock/utils'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
 /usr/bin/install -c 'kiba-icon-editor.py' '/usr/bin/kiba-icon-editor.py'
 /usr/bin/install -c 'kiba-systray.py' '/usr/bin/kiba-systray.py'
 /usr/bin/install -c 'populate-dock.sh' '/usr/bin/populate-dock.sh'
test -z "/usr/share/kiba-dock" || mkdir -p -- "/usr/share/kiba-dock"
 /usr/bin/install -c -m 644 'kiba-icons.glade' '/usr/share/kiba-dock/kiba-icons.glade'
make[2]: Leaving directory `/home/filip/kiba-dock/utils'
make[1]: Leaving directory `/home/filip/kiba-dock/utils'
Making install in files
make[1]: Entering directory `/home/filip/kiba-dock/files'
make[2]: Entering directory `/home/filip/kiba-dock/files'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/python2.4/site-packages" || mkdir -p -- "/usr/lib/python2.4/site-packages"
 /usr/bin/install -c -m 644 'SimpleGladeApp.py' '/usr/lib/python2.4/site-packages/SimpleGladeApp.py'
test -z "/etc/gconf/schemas" || mkdir -p -- "/etc/gconf/schemas"
 /usr/bin/install -c -m 644 'kiba.schemas' '/etc/gconf/schemas/kiba.schemas'
make[2]: Leaving directory `/home/filip/kiba-dock/files'
make[1]: Leaving directory `/home/filip/kiba-dock/files'
make[1]: Entering directory `/home/filip/kiba-dock'
make[2]: Entering directory `/home/filip/kiba-dock'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/filip/kiba-dock'
make[1]: Leaving directory `/home/filip/kiba-dock'


And when Everything is finished and I try starting it up by :

kiba-dock

Nothing happens, he doesn't gives an error and he does not start kiba-docks .

Does anyone knows?

---

### Post by Bob_Mendon on 2006-11-29
Did you try to start it from your "/home/filip/kiba-dock" directory?

---

### Post by Nirva on 2006-11-30
Yes, i tried

---

### Post by igknighted on 2006-12-01
are you sure kiba-dock is the command to start it?  perhaps try kibadock.

---

### Post by Nirva on 2006-12-02
When I type kibadock, the terminal says : 

bash: kibadock: command not found

When I type kiba-dock, the terminal doesn't says anything.  And I don't get a new inputline.  But the kibadock does not start.

---

### Post by 4KvRMU7Nnv on 2006-12-02
dude, i bet it is working you just can't see it.  Drag an icon from your desktop to the bottom of the screen in the middle.  see if there are some arrows indicating you can place it there.  if so, just place it there and the dock will appear.  try it! :)

---

### Post by Nirva on 2006-12-02
You're right.  I found that exactly 1 minute ago.  I just had to run the populate.sh script :-)
But now I have another problem.  When I change settings in gset-kiba and close gset-kiba and reopen it.  The settings haven't been saved nor applied so I can't change any settings.  Maybe because I have to close it by clicking in the right upper corner on the x  .  Does anyone has a solution?

---

### Post by Game_Ender on 2006-12-06
At first the settings were being applied, now they aren't its quite wierd.  The non-graphical ones are getting applied fine, just not the others.

---

