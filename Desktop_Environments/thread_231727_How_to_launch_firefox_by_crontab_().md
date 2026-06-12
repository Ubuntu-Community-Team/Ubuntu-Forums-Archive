---
title: "How to launch firefox by crontab (?)"
date: 2006-08-07
forum: Desktop Environments
---

### Post by tassoman on 2006-08-07
Hi to all, while this simple crontab is working,

```
* * * * * echo date >> Desktop/date.txt
```

This other crontab wouldn't work:

```
* * * * * ~/runFFox.sh
```

```

#!/bin/bash

FF=`ps aux | grep firefox-bin | wc -l`
 
if [ "$FF" == 1 ];
then
	DISPLAY=:0.0 && zenity --info --text "I run Firefox" && firefox
else
	DISPLAY=:0.0 && zenity --info --text "Firefox is running"
fi

```

What's missing?

---

### Post by ardchoille on 2006-08-07
Firstly, you need to use a full path in a crontab. Change "~/runFFox.sh" to /path/to/runFFox.sh

Secondly, I believe the way you are handling DISPLAY in your script needs to be changed. Try this in your script:

```

#!/bin/bash

FF=`ps aux | grep firefox-bin | wc -l`
 
if [ "$FF" == 1 ];
then
	env DISPLAY=:0. zenity --info --text "I run Firefox" && firefox
else
	env DISPLAY=:0. zenity --info --text "Firefox is running"
fi

```

See if that works.

---

### Post by tassoman on 2006-08-08
Nothing new happened :(

The script is working only invoked by CLI

**edit: It's working. There was some typo in source code**
Thanks for help! :D

---

### Post by tassoman on 2006-08-08
Seems there's a problem finding firefox already running.

[B]FF=`ps aux | grep firefox-bin | wc -l`
 
if [ "$FF" == 1 ];[/B]

Isn't working well. There's some way to get list of opened process and parse it with grep?

Something similar to /proc/apps/running/now

---

### Post by ardchoille on 2006-08-08
> **tassoman said:**
> Seems there's a problem finding firefox already running.

[B]FF=`ps aux | grep firefox-bin | wc -l`
 
if [ "$FF" == 1 ];[/B]

Isn't working well. There's some way to get list of opened process and parse it with grep?

Something similar to /proc/apps/running/now

Well, running "ps aux | grep firefox-bin | wc -l" will return "2" becuase it returns the firefox-bin process **and** the grep firefox-bin command.

---

