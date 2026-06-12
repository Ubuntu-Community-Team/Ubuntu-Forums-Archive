---
title: "SimCity3000, Loki_Compat, audio works even though crash to desktop"
date: 2007-09-02
forum: Gaming &amp; Leisure
---

### Post by Jeruleus on 2007-09-02
Wow, so I've spent the past 5 hours today, and about an hour and a half each of the past two days, trying to get SimCity 3000 Unlimited to work.  It doesn't.  I've scoured various forums, tried different things, but still, nothing.  The farthest I've gotten is just now when I followed instructions from [this]("http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games") gentoo-wiki which called for running sc3u with old libraries.  But then I read [this]("http://forums.fedoraforum.org/archive/index.php/t-118038.html"), which suggested the use of a different set of libs, so I followed the aforementioned wiki, substituting the libs of the latter link.  So I ran:
```

 LD_LIBRARY_PATH=/usr/local/games/SC3U/Loki_Compat/ /usr/local/games/SC3U/Loki_Compat/ld-linux.so.2 /usr/local/games/SC3U/sc3u
```
But I had a musicplayer running, so all I got was the following error message:
```
open /dev/dsp: Device or resource busy
X Error:  BadMatch
  Request Major code 141 (XVideo)
  Request Minor code 19 ()
  Error Serial #19
  Current Serial #20

```
I killed the musicplayer and tried running it again.  My screen went black, as though the game were starting up, my mouse cursor changed from small and white to big and black, I got excited, music was playing, but then the video crashed.  The music, however, kept on playing.  I got the following error message:
```
fcntl: Operation not permitted
fcntl: Operation not permitted
X Error:  BadMatch
  Request Major code 141 (XVideo)
  Request Minor code 19 ()
  Error Serial #19
  Current Serial #20
```
Now, when I get this error, the music keeps playing, and my term acts as though the program's running - which is to say, the cursor blinks on a blank line, without the usual username@computername: prefix.

I don't know what to do.  Any help would be greatly appreciated.

---

### Post by aschaetter on 2007-10-02
I have EXACTLY the same problem. I'm willing to try anything if someone has a sugestion. Several people have sugested that I look for a config file to change the video settings but I am at a loss.

My error was the same except the "Error Serial" was "#20" and the "Current Serial" was "#21"

---

### Post by icechen1 on 2008-01-21
Same problem here,linux mint 4.0

---

### Post by skoruppa on 2008-01-24
ehhh
1. Install without videos or delete videos from game dir
2. My launcher
```
#!/bin/bash
###############################################################################
#
## Thx to LIFLG and LOKI
#
# Skoruppa
#
###############################################################################


# readlink replacement for older bash versions
readlink() {
	local path=$1 ll

	if [ -L "${path}" ]; then
		ll="$(LC_ALL=C ls -l "${path}" 2> /dev/null)" &&
		echo "${ll/* -> }"
	else
		return 1
	fi
}


SCRIPT="$0"
COUNT=0
while [ -L "${SCRIPT}" ]
do
	SCRIPT=$(readlink ${SCRIPT})
	COUNT=$(expr ${COUNT} + 1)
	if [ ${COUNT} -gt 100 ]
	then
		echo "Too many symbolic links"
		exit 1
	fi
done
GAMEDIR=$(dirname ${SCRIPT})
LOKI=${GAMEDIR}/Loki_Compat
cd ${GAMEDIR}

export LD_LIBRARY_PATH=$LOKI
if [ $@ = -pl ]; then
LANG=pl
LD_ASSUME_KERNEL=2.4.26 $LOKI/ld-linux.so.2 ./sc3u
elif [ $@ = -wpl ]; then
LANG=pl
LD_ASSUME_KERNEL=2.4.26 $LOKI/ld-linux.so.2 ./sc3u -w
elif [ $@ = -w ]; then
LANG=english
LD_ASSUME_KERNEL=2.4.26 $LOKI/ld-linux.so.2 ./sc3u -w
else
LANG=english
LD_ASSUME_KERNEL=2.4.26 $LOKI/ld-linux.so.2 ./sc3u
fi
```
-pl to run game in polish ;>
-w for window mode

And this is all

---

