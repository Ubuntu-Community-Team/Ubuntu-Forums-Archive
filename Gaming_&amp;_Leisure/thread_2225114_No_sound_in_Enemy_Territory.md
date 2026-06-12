---
title: "No sound in Enemy Territory"
date: 2014-05-19
forum: Gaming &amp; Leisure
---

### Post by El_Salado_MX on 2014-05-19
Hello to the community. I have a sound problem with playing Enemy Territory only in the game I have no audio, but if I have UBUNTU audio, this is the file that has the following ET configuration lines, if anyone can help  I will be very grateful, just me I'm starting on LINUX. Greetings to all and thanks for your time.

#! /bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/enemy-territory/"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec ./et.x86 "$@"

---

### Post by mastablasta on 2014-05-21
how did you install the game?

---

### Post by El_Salado_MX on 2014-05-23
Hi mastablasta.

No, I need to know how to restore the sound.

---

### Post by mikemelendrez on 2014-05-27
> **El_Salado_MX said:**
> Hi mastablasta.

No, I need to know how to restore the sound.
I think in order to help you with your sound, mastablasta was asking you, how did you install ET?

---

### Post by Coup_Cutter on 2014-05-28
Enemy Territory has long been known to experience sound issues when being played in a linux environment.  
One oft-cited fix for this has been to follow the posts relating to installing **et-sdl-sound **as found here: [http://nullkey.kapsi.fi/et-sdl-sound/](http://nullkey.kapsi.fi/et-sdl-sound/)

There is, however, a new wrinkle to the problem which occurs when a user installs the **Steam**
 program...some will find sound no longer works.

I found a fix posted for this at:
[http://www.vereinte-nationen.de/kw_joomla/index.php/en/forum/43-kw-public/45990-sound-on-linux-won-t-work-after-installing-steam](http://www.vereinte-nationen.de/kw_joomla/index.php/en/forum/43-kw-public/45990-sound-on-linux-won-t-work-after-installing-steam)

Essentially, the et-sdl-sound script uses a locate command to find all incidences of the SDL libraries, the steam variant of which
cause problems for Enemy Territory.  The fix is to comment out some annoying aspects of the script:

Essentially edit your et-sdl-sound script file using your text editor of choice to make this section:

> 
if [ "$LIBSDL" = "" ]; then
	LOCATE_LIBSDL=`locate -r libSDL[^_]*so[^_]* 2> /dev/null`
	for i in $LOCATE_LIBSDL; do
		testlibsdl $i
		[ "$LIBSDL" != "" ] && break
	done
fi


Look like this:

> 
#if [ "$LIBSDL" = "" ]; then
#	LOCATE_LIBSDL=`locate -r libSDL[^_]*so[^_]* 2> /dev/null`
#	for i in $LOCATE_LIBSDL; do
#		testlibsdl $i
#		[ "$LIBSDL" != "" ] && break
#	done
#fi



The '#' character being placed in front of the appropriate lines causes the line to be "commented out" and essentially
ignored during script execution.

Save the resulting file and fire it up to once more sail into the game with sound.

Hope this helps someone.

---

