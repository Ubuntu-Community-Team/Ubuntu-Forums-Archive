---
title: "Heli-X 0.9 Free version for Linux"
date: 2011-08-06
forum: Gaming &amp; Leisure
---

### Post by Gemu on 2011-08-06
I've been using Heli-x Helicopter flight simulator for a long time but have never managed to get sound working. The error I get when starting is the openal sound driver can't be found.

Has anyone figured out a way to fix this or maybe just knows what might be the problem.


 The download can be found here- 0.9 free version [http://www.heli-x.info/download_e.shtml#DownloadHeliX]("http://www.heli-x.info/download_e.shtml#DownloadHeliX")


and the openal driver is here - [http://connect.creativelabs.com/openal/Downloads/Forms/AllItems.aspx]("http://connect.creativelabs.com/openal/Downloads/Forms/AllItems.aspx")

 Im running a 64 bit computer which the have scripts for both 32 and 64 bit. Openal builds fine and then make seems to do like it should but still no sound.


here is my results of cmake

downloads/HELI-X/openal-soft-1.13/build$ cmake
-- The C compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of long
-- Check size of long - done
-- Check size of long long
-- Check size of long long - done
-- Check size of unsigned int
-- Check size of unsigned int - done
-- Check size of void*
-- Check size of void* - done
-- Checking if C compiler supports -Wextra
-- Checking if C compiler supports -Wextra - Success
-- Performing Test HAVE_GCC_DESTRUCTOR
-- Performing Test HAVE_GCC_DESTRUCTOR - Success
-- Checking if C compiler supports -fvisibility=internal
-- Checking if C compiler supports -fvisibility=internal - Success
-- Performing Test HAVE_GCC_VISIBILITY
-- Performing Test HAVE_GCC_VISIBILITY - Success
-- Performing Test HAVE_GCC_FORMAT
-- Performing Test HAVE_GCC_FORMAT - Success
-- Looking for fenv.h
-- Looking for fenv.h - found
-- Looking for float.h
-- Looking for float.h - found
-- Looking for powf in m
-- Looking for powf in m - found
-- Looking for sqrtf in m
-- Looking for sqrtf in m - found
-- Looking for acosf in m
-- Looking for acosf in m - found
-- Looking for atanf in m
-- Looking for atanf in m - found
-- Looking for fabsf in m
-- Looking for fabsf in m - found
-- Looking for fesetround in m
-- Looking for fesetround in m - found
-- Looking for strtof
-- Looking for strtof - found
-- Looking for _controlfp
-- Looking for _controlfp - not found
-- Looking for stat
-- Looking for stat - found
-- Looking for strcasecmp
-- Looking for strcasecmp - found
-- Looking for strncasecmp
-- Looking for strncasecmp - found
-- Looking for snprintf
-- Looking for snprintf - found
-- Looking for vsnprintf
-- Looking for vsnprintf - found
-- Looking for isnan
-- Looking for isnan - found
-- Looking for dlfcn.h
-- Looking for dlfcn.h - found
-- Looking for dlopen in dl
-- Looking for dlopen in dl - found
-- Looking for windows.h
-- Looking for windows.h - not found
-- Looking for gettimeofday
-- Looking for gettimeofday - found
-- Looking for nanosleep
-- Looking for nanosleep - found
-- Checking if C compiler supports -pthread
-- Checking if C compiler supports -pthread - Success
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for include files HAVE_PTHREAD_NP_H
-- Looking for include files HAVE_PTHREAD_NP_H - not found.
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Looking for pthread_setschedparam in pthread
-- Looking for pthread_setschedparam in pthread - found
-- Looking for clock_gettime in rt
-- Looking for clock_gettime in rt - found
-- Looking for alsa/asoundlib.h
-- Looking for alsa/asoundlib.h - not found
-- Looking for sys/soundcard.h
-- Looking for sys/soundcard.h - found
-- Looking for sys/audioio.h
-- Looking for sys/audioio.h - not found
-- Looking for dsound.h
-- Looking for dsound.h - not found
-- Looking for portaudio.h
-- Looking for portaudio.h - not found
-- Looking for pulse/pulseaudio.h
-- Looking for pulse/pulseaudio.h - not found
-- 
-- Building OpenAL with support for the following backends:
--      OSS, WaveFile, Null
-- 
-- Building utility programs
-- 
-- Configuring done
-- Generating done
-- Build files have been written to: /home/guest1/downloads/HELI-X/openal-soft-1.13/build
guest1@guest1-desktop:~/downloads/HELI-X/openal-soft-1.13/build$ 



A lot of stuff is not found in there and I have no idea where to get them.

Thanks in advance for any suggestions.

---

### Post by KIAaze on 2011-08-07
Interesting, I had never heard of that simulator before. :)

As for your problem: Most header files (.h files) come from *-dev packages.
You can search for the packages containing the files you need using [http://packages.ubuntu.com/](http://packages.ubuntu.com/) ("Search the contents of packages" feature).

Another solution is installing and using apt-file: [http://en.wikipedia.org/wiki/Apt-file](http://en.wikipedia.org/wiki/Apt-file)

---

### Post by Gemu on 2011-08-08
> **KIAaze said:**
> Interesting, I had never heard of that simulator before. :)

As for your problem: Most header files (.h files) come from *-dev packages.
You can search for the packages containing the files you need using [http://packages.ubuntu.com/](http://packages.ubuntu.com/) ("Search the contents of packages" feature).

Another solution is installing and using apt-file: [http://en.wikipedia.org/wiki/Apt-file](http://en.wikipedia.org/wiki/Apt-file)



 Thanks for the reply KIAase, Its a beautiful program with nice graphics. The flying fields are top notch. This is my favorite. Its called Altac [IMG]http://www.helifreak.com/picture.php?albumid=6767&pictureid=59296[/IMG]

Another Altac image [IMG]http://www.helifreak.com/picture.php?albumid=6767&pictureid=59244[/IMG]

This one is called Marbach_Sommer [IMG]http://www.helifreak.com/picture.php?albumid=6767&pictureid=59500[/IMG]

 I think it would be much better if I purchase a cord to work with my Spektrum DX 7. I'm using a 17.00 USB Dynam controller that looks like a remote control from Helix.com. It works great on Helisim another wonderful free simulator but limited to one flying field and lesser graphics. Its what I use most because it flys so much better and easy to edit and editing actually works.

---

