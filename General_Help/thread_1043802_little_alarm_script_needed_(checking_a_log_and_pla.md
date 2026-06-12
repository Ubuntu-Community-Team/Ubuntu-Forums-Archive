---
title: "little alarm script needed (checking a log and play mp3)"
date: 2009-01-18
forum: General Help
---

### Post by okapio on 2009-01-18
Hi,

I'm quite new to Ubuntu, and I need it mostly for this thing: a script that each 30 seconds check a text file and, when in this file there is the string "ERROR", it should play a MP3 file.

I think it's possible, but I have no idea about what commands/programs should be used.

Thanks in advance,

Okapio

---

### Post by pytheas22 on 2009-01-18
This should work (provided you substitute in the correct file names and paths, of course):

```

#!/bin/bash

if grep -e ERROR text-file.txt
then mplayer music-file.mp3
fi
```

You would need to have mplayer installed first; you can install it by typing:
```

sudo apt-get install mplayer
```

You can run it as a cron job every 30 seconds; if you're not familiar with how to do that and can't figure it out through Google, let me know.

---

### Post by zman58 on 2009-01-18
Then...
After you debug it and have it working, you will also need a crontab entry to run it every minute...

First you will need to learn a little about text editor vim.


Then you can open a terminal session and type...
crontab -e

Crontab will run programs at regular intervals for you.

For more details on crontab, open a terminal and type "man crontab". Here are some examples: [http://www.pantz.org/software/cron/croninfo.html](http://www.pantz.org/software/cron/croninfo.html)

---

