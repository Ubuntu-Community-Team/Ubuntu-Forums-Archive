---
title: "Mute Commercials for 2 Minutes"
date: 2005-06-13
forum: Desktop Environments
---

### Post by gkchicago on 2005-06-13
I listen to talk radio online and the commercials are driving me nuts.  But when I remember to mute the volume so I don't have to listen I forget to unmute it so i miss some of the broadcasts.  I've noticed that no breaks are shorter than 2minutes and longer than 3 minutes.  

I'd like to put an icon on my top gnome menu-bar that simply brings the volume down to 20% (or lower) for two minutes and then returns it to the previous state automatically.

Anyone know where to start?  alsactl?

---

### Post by tread on 2005-06-13
a small script might work .. something on the lines of

reduce volume using a commandline tool
sleep 2 minutes
raise volume using the commandline tool

I think the command line tool might be alsamixer .. not sure though.
Then all you need to do is add a launcher for the script on your taskbar.

---

### Post by tread on 2005-06-13
Try putting this in a script:

```

#!/bin/bash
amixer -set 0%
sleep 120
amixer -set 100%

```

and creating a launcher for it. I'm not in Linux so I cannot verify if the amixer parameter is correct, but thats the one you need to use. Try amixer --help.

---

### Post by gkchicago on 2005-06-13
```
cat bin/mute_commercials.sh
#!/bin/sh
#
#
VOLUME_LEVEL=10
DELAY_TIME=120


# Run Script
amixer -q set PCM $VOLUME_LEVEL%
sleep $DELAY_TIME
amixer -q set PCM 80%
```

This did the trick.  I'm listening to the stream using RealPlayer so I had to reduce the PCM sound item.  To see the list of things you can control with amixer type:

```
$> amixer scontrols
```

This will come in handy, thanks for the help!

---

### Post by gkchicago on 2005-06-13
I increased the timer because the commercial breaks are longer but I also put in an "Unmute" ability (using a temp file) that makes it so I can just click the same button on the menu.

```
#!/bin/sh
#
#
VOLUME_LEVEL=10
DELAY_TIME=180
TMP_PIDFILE="/tmp/mutepid.pid"


if [ -f $TMP_PIDFILE ]; then
  amixer -q set PCM 80%
  rm -rf $TMP_PIDFILE
else
  # Run Script
  amixer -q set PCM $VOLUME_LEVEL%
  echo "1" > $TMP_PIDFILE
  sleep $DELAY_TIME
  rm -rf $TMP_PIDFILE
  amixer -q set PCM 80%
fi
```

---

