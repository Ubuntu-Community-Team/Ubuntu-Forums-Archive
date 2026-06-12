---
title: "Executing a program via init.d"
date: 2006-09-20
forum: Desktop Environments
---

### Post by esoteric4334 on 2006-09-20
Ok, so I've been reading the manual and various webpages, and from what I can tell my startup script, intended to run 885resolution enabling widescreen resoltuion, should work but no luck.

Here is my /etc/init.d/885resolution file:
#! /bin/sh
#

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

case "$1" in
start)
echo -n "Starting 885resolution"
/sbin/885resolution 50 1280 800
# 885resolution 50 1280 800


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

