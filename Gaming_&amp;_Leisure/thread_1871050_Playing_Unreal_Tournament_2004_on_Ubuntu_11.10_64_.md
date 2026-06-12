---
title: "Playing Unreal Tournament 2004 on Ubuntu 11.10 64 bit with sound"
date: 2011-10-28
forum: Gaming &amp; Leisure
---

### Post by razorxpress on 2011-10-28
There are two issues. If I try to run ut2004-bin under System directory of Unreal Tournament sound appears but background graphics does not show up and if I try to run ut2004-bin-linux-amd64 game works without any issue but sound does not come. I now realize how sound of a game is as important as the game itself. If you try ls under System directory of Unreal Tournament you will see three files.

$ ls *.so*
libSDL-1.2.so.0  libstdc++.so.5  openal.so

To make the application run with sound on a 64 bit, remove these files are replace them with corresponding files of 64 bit Linux.

In my computer I replaced as follows.

cp /usr/lib/libopenal.so.1.13.0 openal.so
cp /usr/lib/x86_64-linux-gnu/libstdc++.so.5 .
cp /usr/lib/libSDL-1.2.so.0.11.3 libSDL-1.2.so.0

If you have updated these files the version numbers might be different.

Now run ut2004-bin-linux-amd64

$ ./ut2004-bin-linux-amd64

---

### Post by not12listen on 2011-11-13
i'll be installing UT2004 shortly and be testing this very soon... :)

thank you for the info that you posted - i'll reply back if it worked or not. :)

---

### Post by not12listen on 2011-11-13
so, many thanks to your information posted above, i've got UT2004 running...  just not sound.

i admit that i'm very new with linux.  so, i'm trying to find the 3 listed files, but i'm having a bit of trouble.

i'm going to check to see if they're available via the software update manager.

otherwise, i'll report here asking for a bit of assistance. :)

---

### Post by not12listen on 2011-11-13
when i try to open UT2004, it does open and play without issue.  just no sound.

here is the error that i get:
open /dev/[sound/]dsp: No such file or directory

i did open the console and go to that location.  the only folder that i see remotely close is
'snd'


i've made sure to update the following packages:
libopenal
libstdc++
libSDL

help! :)

---

### Post by Larian on 2012-10-23
I recently had trouble launching this game in Ubuntu 12.04, but I managed to solve the problem. Manually edit the ~./ut2004 file under the "# Let's boogie!" section from

if [ -x "${UT2004_DATA_PATH}/ut2004-bin" ]
then
	cd "${UT2004_DATA_PATH}/"
	exec "./ut2004-bin" $*
fi

To read as follows:

if [ -x "${UT2004_DATA_PATH}/ut2004-bin" ]
then
	cd "${UT2004_DATA_PATH}/"
	exec padsp "./ut2004-bin" $*
fi

For those who would rather have the change explicitly spelled out, I changed line 49 to use the PulseAudio wrapper before executing the game. Thus far I've noticed no lag whatsoever.

I hope this helps!

---

