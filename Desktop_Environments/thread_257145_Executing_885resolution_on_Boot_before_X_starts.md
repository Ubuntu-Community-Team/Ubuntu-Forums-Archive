---
title: "Executing 885resolution on Boot before X starts"
date: 2006-09-14
forum: Desktop Environments
---

### Post by esoteric4334 on 2006-09-14
Greetings,

First, let me preface this by saying Ubuntu is the cleanest and easiest to use linux distro around. I've been toying with linux for awhile now and I've found Ubuntu's install to be the most compelete and easiest to use yet!

That being said I'm still a bit of a linux newb. I have a widescreen laptop that can display a resolution of 1280x800 using the 885resolution program, however, to get this to work I have to stop X and run the 885resolution program with the desired parameters, then startx again.

How do i go about making this 885resoluton program run on boot before x starts? I imagine is as simple as adding a line to a configuration file at startup, but I've yet to find that file. Any and all help is appreciated.

Thanks!
Edit/Delete Message

---

### Post by dentaku65 on 2006-09-14
I think you can use update-rc.d
Please refer to the manual...

man update-rc.d


:rolleyes:

---

### Post by esoteric4334 on 2006-09-16
Danke schön!

---

### Post by esoteric4334 on 2006-09-17
Ok, so I've been reading the manual and various webpages, and from what I can tell startup script should work but no luck. 

Here is my /etc/init.d/885resolution file:
#! /bin/sh
#

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

case "$1" in
  start)
        echo -n "Starting 885resolution"
        /sbin/885resolution 50 1280 800
#       885resolution 50 1280 800


        echo "."
        ;;
stop|reload|restart|force-reload)
        ;;
esac

exit 0
~

i added the symlinks via the command:
 sudo update-rc.d 885resolution start 01 S . 

to test if it would run i did:
sudo invoke-rc.d 885resolution start

but i either get the following errors:
line 11: 885resolution: no such file or directory

when i have verified 885resolution is indeed in /sbin/
the script also has been chmod 755 'd.

Plz help im at the end of my rope here....

---

