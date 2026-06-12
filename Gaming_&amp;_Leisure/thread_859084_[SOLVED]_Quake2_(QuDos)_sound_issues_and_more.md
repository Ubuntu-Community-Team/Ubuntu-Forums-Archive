---
title: "[SOLVED] Quake2 (QuDos) sound issues and more"
date: 2008-07-14
forum: Gaming &amp; Leisure
---

### Post by quanumphaze on 2008-07-14
I have finally got QuDos to successfully install. But have run into 2 issues.

Firstly the sound refuses to work. I don't know if it is a PulseAudio problem or what. Modifying the Makefile to support different sound systems didn't work. I tried to have is use only OSS and use the padsp wrapper for it without success.

Secondly some of the graphics are messed up. Things like bullet holes, blood, lights and sparks are big squares. This is less important than the sound but still an eyesore.

A third issue is that "Can't find pic: /gfx/mouse_cursor.pcx" is constantly pumped out to the console when ever I am in the menu. Seems like some mouse support for the menus is broken. This is not very important, just annoying.

I believe some of these problems are related to the options in the Makefile. Options are:```
# Client and Renderers
BUILD_QUAKE2?=YES	# Build client.
BUILD_DEDICATED?=NO	# Build dedicated server.
BUILD_GLX?=YES		# Build OpenGL renderer.
BUILD_SDLGL?=YES	# Build SDL OpenGL renderer.
ifeq ($(OSTYPE),linux)
BUILD_ALSA_SND?=YES     # Enable support for ALSA (default sound on 2.6 Linux).
endif
BUILD_OSS_SND?=YES      # Enable support for OSS (default) sound.
BUILD_SDL_SND?=YES      # Enable support for SDL sound.

# Mods
BUILD_GAME?=YES		# Build original game modification (game$(ARCH).so).
BUILD_3ZB2?=NO		# Build 3zb2 (bots) modification.
BUILD_CTF?=NO		# Build CTF (Capture The Flag) modification.
BUILD_JABOT?=NO		# Build JABot (bots) modification.
BUILD_ROGUE?=NO		# Build Rogue modification.
BUILD_XATRIX?=NO	# Build Xatrix modification.
BUILD_ZAERO?=NO		# Build Zaero modification.

# Configurable options.
WITH_BOTS?=YES		# Enable Ace Bot support in modifications (Quake2, Rogue, Xatrix and Zaero).
WITH_DATADIR?=NO	# Read from $(DATADIR) and write to "~/.quake2".
WITH_DGA_MOUSE?=NO	# Enable DGA mouse extension.
WITH_GAME_MOD?=YES	# Enable custom addons in the main modification (Quake2, Rogue, Xatrix and Zaero).
WITH_IPV6?=NO		# Enable IPv6 support. Tested on FreeBSD.
WITH_JOYSTICK?=NO	# Enable joystick support.
WITH_LIBDIR?=NO	# Read data and renderers from $(LIBDIR).
WITH_QMAX?=YES		# Enable fancier OpenGL graphics.
WITH_REDBLUE?=NO	# Enable red-blue 3d glasses renderer.
WITH_RETEXTURE?=YES	# Enable retextured graphics support.
# THe below options can't be both enabled at the same time, so use Xmms or Audacious for now 
WITH_AUDACIOUS?=NO	# Enable AUDACIOUS support (thanks AprQ2).
WITH_XMMS?=NO		# Enable XMMS support (thanks AprQ2).

# General variables.
LOCALBASE?=	/usr/local
SYSBINDIR?=	$(LOCALBASE)/bin
X11BASE?=	/usr/X11R6
PREFIX?=	$(LOCALBASE)

```
Any help is welcome

---

### Post by quanumphaze on 2008-07-15
I managed to fix the sound problem by using```
"echo 'QuDos 0 0 direct' > /proc/asound/card0/pcm0p/oss" above : exit 0
```in a root terminal, (echo doesn't work with sudo, must use sudi -i)
This is a modification of the [GamesNativeQuake2]("https://help.ubuntu.com/community/Games/Native/Quake2") Ubuntu wiki page.

The /etc/init.d/bootmisc.sh file needed to be edited contains stuff which I don't think was there in previous Ubuntu versions.
It asks you to do this:```
sudo vi /etc/init.d/bootmisc.sh
add "echo 'quake2 0 0 direct' > /proc/asound/card0/pcm0p/oss" above : exit 0
```But the exit part may screw up the script in Hardy. I slapped it in somewhere I thought looked ok and the script now looks like:```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          bootmisc
# Required-Start:    $local_fs hostname $remote_fs
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:
# Short-Description: Miscellaneous things to be done during bootup.
# Description:
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin
[ "$DELAYLOGIN" ] || DELAYLOGIN=yes
. /lib/init/vars.sh

do_start () {
	#
	# If login delaying is enabled then create the flag file
	# which prevents logins before startup is complete
	#
	case "$DELAYLOGIN" in
	  Y*|y*)
		echo "System bootup in progress - please wait" > /var/lib/initscripts/nologin
		;;
	esac

	# Create /var/run/utmp so we can login.
	: > /var/run/utmp
	if grep -q ^utmp: /etc/group
	then
		chmod 664 /var/run/utmp
		chgrp utmp /var/run/utmp
	fi

	# Set pseudo-terminal access permissions.
	if [ ! -e /dev/.devfsd ] && [ -c /dev/ttyp0 ]
	then
		chmod -f 666 /dev/tty[p-za-e][0-9a-f]
		chown -f root:tty /dev/tty[p-za-e][0-9a-f]
	fi

	# Update motd
	uname -snrvm > /var/run/motd
	[ -f /etc/motd.tail ] && cat /etc/motd.tail >> /var/run/motd

	[COLOR="Blue"]# QuDos (Quake2) sound fix[/COLOR]
	[COLOR="Red"]echo 'QuDos 0 0 direct' > /proc/asound/card0/pcm0p/oss[/COLOR]

	# Save kernel messages in /var/log/dmesg
	if which dmesg >/dev/null 2>&1
	then
		savelog -q -p -c 5 /var/log/dmesg
		dmesg -s 524288 > /var/log/dmesg
		chgrp adm /var/log/dmesg || :
	elif [ -c /dev/klog ]
	then
		savelog -q -p -c 5 /var/log/dmesg
		dd if=/dev/klog of=/var/log/dmesg &
		sleep 1
		kill $!
		[ -f /var/log/dmesg ] && { chgrp adm /var/log/dmesg || : ; }
	fi

	# Remove bootclean's flag files.
	# Don't run bootclean again after this!
	rm -f /tmp/.clean
}

case "$1" in
  start|"")
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: bootmisc.sh [start|stop]" >&2
	exit 3
	;;
esac

:
```

I still am having problems with the graphics. It works fine now except that these squares are everywhere that 2D objects are with bright coloured borders. Attached is a screenshot of the basement area with water in the 1st level as I shoot the pistol. Those red squares are supposed to be sparks. The water bed also had a red grid on it.

---

### Post by quanumphaze on 2008-07-15
Wow, I fixed it all by myself. (Why do all my threads end this way?) Marking as [Solved]

Anyway the problem with the squares and mouse_cursor.pcx is that the makefile doesn't put the data/qudos.pk3 file into the quake2/base2 directory. Now it works. Yay!

If anyone else has problems with getting the QuDos Quake 2 port to work feel free to PM me about your thread. One day Linux gaming will work right (at least now we have PulseAudio).

---

### Post by Brebs on 2008-08-06
For sound, QuDos supports ALSA, OSS and SDL.

See [my qudos src.rpm](ftp://brebs.me.uk/fedora/9/) for build info and some small patches. Yes it's an RPM, but you can open it, see the patches and read its .spec file.

---

### Post by quanumphaze on 2008-08-07
Thanks for that, unfortunately I'm not that good at packaging and don't understand how everything works. I'm sure your info will help someone eventually.

BTW it seems to of had problems with permissions when it's installed in /usr/share/games/quake2 where the quake2-data package installs the game files. It seems to expect to be installed into ~/quake2 where it expects to be able to write settings and save game data. For some reason it decided to be created under my ownership so there's a mix of files owned by me and root (from the quake2-data package). I'm not changing anything in case it fails but this is hardly ideal for a proper package. Any suggestions?

---

### Post by Brebs on 2008-08-07
Take a look at the make options for qudos:
> WITH_DATADIR?=NO	# Read from $(DATADIR) and write to "~/.quake2".
Same for WITH_LIBDIR. These are important options.

Fix the file and directory permissions, with e.g.:
```
find /usr/share/games/quake2 -type f -exec chown games:games '{}' \;
find /usr/share/games/quake2 -type f -exec chmod 644 '{}' \;
find /usr/share/games/quake2 -type d -exec chmod 755 '{}' \;
```
Also see my [kmquake2 RPMS and .spec files](ftp://brebs.me.uk/fedora/9/) - [Mark Shan's Quake 2 maps](http://www.markshan.com/thesinraven/) are excellent :)  - They need the full CD Quake 2 data, as opposed to just the shareware data.

---

### Post by quanumphaze on 2008-08-07
Compiling with those options turned on and using sudo make install causes a make error```
* Copying files to your /home/andrew/quake2 dir ...
* Removing symbols...
strip: quake2/baseq2/qudos.pk3: File format not recognized
make: *** [install] Error 1

```
Caused by the red line```
ifeq ($(strip $(STRIP)),YES)
	@printf "* Removing symbols...\n"
	[COLOR="Red"]@strip $(BIN_DIR)/ref_* $(BIN_DIR)/QuDos $(BIN_DIR)/*/*[/COLOR]
endif
```
Any clues? I'll have to install manually or keep my current "you're doing it wrong" one.

---

### Post by Brebs on 2008-08-07
If you're installing into /home/yourname/quake2, then there is no point in using sudo - that will create files owned by root rather than yourself. sudo is for installing into e.g /usr/bin and /usr/share/... - that's why your permissions were messed up.

For the strip option, the obvious thing to do is set it to NO ;)  It's not needed, and anyway, wouldn't conflict, with the way I install it:
```
$ rpm -ql qudos
/usr/bin/qudos
/usr/bin/qudos-wrapper
/usr/lib64/qudos/baseq2/game.so
/usr/lib64/qudos/baseq2/particles/fly_3.png
/usr/lib64/qudos/baseq2/particles/fly_4.png
/usr/lib64/qudos/baseq2/qudos.pk3
/usr/lib64/qudos/ref_q2sdlgl.so
/usr/lib64/qudos/snd_alsa.so
/usr/lib64/qudos/snd_oss.so
/usr/lib64/qudos/snd_sdl.so
/usr/share/applications/qudos.desktop
/usr/share/doc/qudos-svn344
/usr/share/doc/qudos-svn344/Ogg_readme.txt
/usr/share/doc/qudos-svn344/QuDos.txt
/usr/share/doc/qudos-svn344/todo.txt
/usr/share/pixmaps/qudos.png
```
qudos-wrapper is just a little Fedora script to do a simple check that opengl is set up. fly_?.png adds two entries which are missing from qudos.pk3. Fedora doesn't usually use a "games" subdir.

---

