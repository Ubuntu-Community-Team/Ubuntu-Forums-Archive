---
title: "Need help getting bootscript to work"
date: 2006-09-01
forum: Desktop Environments
---

### Post by mikuskuikku on 2006-09-01
Need to get vlc to start streaming on startup (without needing to login on gdm).

Created /usr/bin/streamtv.sh
```
#!/bin/sh
vlc -v pvr/ps:/dev/video0 :sout=#transcode{venc=ffmpeg,vcodec=WMV2,vb=512,scale=1,\
acodec=mp3,ab=32,channels=2,samplerate=22050,audio-sync,high-priority}\
:std{access=mmsh,mux=asfh,dst=:8082} --intf dummy vlc:quit
```
Made it executable with "chmod +x /usr/bin/streamtv.sh"
The streamtv.sh works if i just type streamtv.sh in a console.

Created a /etc/init.d/streamtv.sh
```
#!/bin/sh
SSD_ARG="/usr/bin/streamtv.sh"
test -f $SSD_ARG || exit 0
. /lib/lsb/init-functions
case "$1" in
  start)
        start-stop-daemon --start --verbose --oknodo --pidfile $PIDFILE \
        --name vlc --startas $SSD_ARG > /var/log/streamtv.log 2>&1
  ;;
  stop)
    echo "Can not stop streaming"
  ;;
  restart)
    echo "Can not restart streaming"
  ;;
  *)
    echo "Usage /etc/init.d/streamtv start"
  ;;
esac
exit 0
```
Made this work with "chmod +x /etc/init.d/streamtv.sh"
The init.script works when just typing in console
```
/etc/init.d/streamtv.sh start
```

So i tryed to get it to autostart when computer starts up with different commands (run "update-rc.d -f streamtv.sh remove" between the different tests).
```

update-rc.d streamtv.sh start 60 2 3 4 5 .
update-rc.d streamtv.sh defaults
ln -sv /etc/init.d/streamtv.sh /etc/rc2.d/S60streamtv.sh
ln -sv /etc/init.d/streamtv.sh /etc/rcS.d/S60streamtv.sh
```
But nothing starts.
How do I do to get something to startup automatically?
How should this be done in a right whay?

I understand that rc1.d,rc2.d,... has to do with runlevels... but I don't understand which runlevel does what and when.

---

