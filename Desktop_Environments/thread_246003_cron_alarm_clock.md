---
title: "cron alarm clock"
date: 2006-08-28
forum: Desktop Environments
---

### Post by charbo on 2006-08-28
Hello,

I am trying to use cron to use my computer as an alarm clock, just because;) 
I basically followed the following link but I simplified it greatly.
[http://grimthing.com/archives/2004/01/23/cron-mp3-alarm-clock/](http://grimthing.com/archives/2004/01/23/cron-mp3-alarm-clock/)

I am tryint to use rhythmbox, and I am trying to play only one song.
My alarm script looks like the following.

#!/bin/sh
rhythmbox --play /home/charbo/songForAlarm.mp3

(I literally copied the song to my home dir and named it as above, because specifying the file path did not work, and I assumed it was because of escaped white spaces in path and file name.)

My cron entry looks like the following.

# m h  dom mon dow   command
45 7 * * 1-5 /home/charbo/alarm

syslog reports that it ran the script.

Aug 28 16:17:01 charbo-ubuntu /USR/SBIN/CRON[1322]: (charbo) CMD (/home/charbo/alarm)

When I run the script, ./alarm, it works.
The script has 755 permission.
-rwxr-xr-x  1 charbo charbo         56 2006-08-28 16:16 alarm

What am I doing wrong?
Thanks!

---

### Post by gtcom on 2007-02-16
> **charbo said:**
> I am tryint to use rhythmbox, and I am trying to play only one song.
My alarm script looks like the following.

#!/bin/sh
rhythmbox --play /home/charbo/songForAlarm.mp3

First off, after the #/bin/bash declaration, add:

```
export DISPLAY :0
```

Secondly, you'll need the full path to the executable, i.e. /usr/bin/rhythmbox

Third, make sure you *also* use the full path in your crontab.

Last, I'm not sure what version of rhythmbox you're using, but in 0.9.7.90 the method by which you call rhythmbox from the command line to play a song is by using rhythmbox-client.  So, your script should look something like the following:

```

#!/bin/bash

export DISPLAY :0
/usr/bin/rhythmbox-client --play-uri=/home/charbo/songForAlarm.mp3

```

If you'd like to play a directory of mp3's, change the last line to read:

```

/usr/bin/rhythmbox-client --enqueue /home/charbo/music/*.mp3 --play

```

Hope this helps.

---

