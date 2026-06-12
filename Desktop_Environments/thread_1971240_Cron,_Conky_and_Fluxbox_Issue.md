---
title: "Cron, Conky and Fluxbox Issue"
date: 2012-05-02
forum: Desktop Environments
---

### Post by Aphotic on 2012-05-02
First, I have tried the advice posted [here.]("http://ubuntuforums.org/archive/index.php/t-796233.html")

Seeing as none of those suggestions resolved it, here's my issue:

I have in the past setup cron jobs to change my desktop background every 10 or 15 minutes. Back then I didn't bother specifying a display so sometimes it worked better than others.

I now have a conky configuration which I have 3-4 color schemes for. I thought "how neat would it be to have the conky colors change to match the backgrounds?"

I modded the conky themes and found a command to accomplish everything I wanted as follows:
```

killall conky && fbsetbg ~/.fluxbox/backgrounds/hypex.jpg && conky -c ~/.conky/conkyrcgreen

```

If I plug this string of commands into the terminal it executes flawlessly, however if I try and run it through cron it successfully kills conky but none of the other commands appear to execute. So effectively conky vanishes from my desktop but it doesnt reload and the background doesn't change.

Any suggestions would be greatly appreciated.

---

### Post by LewisTM on 2012-05-02
My guess would be that cron won't interpret those && and ~ symbols which are shell aliases.
So either create a shell script with your commands inside and make it executable, or use a command like this:
```
bash -c "killall conky && fbsetbg /home/you/.fluxbox/backgrounds/hypex.jpg && conky -c /home/you/.conky/conkyrcgreen"
```

Cheers!

---

### Post by Aphotic on 2012-05-02
I tried both of your suggestions and neither work -.-
Thanks for the advice though.

I have written my scripts and placed them in ~/.scripts even using the full path in cron they run automatically but I experience the same issue as before. Conky is killed and then nada.

One thing of interest is that every time I try and execute a task through gnome-schedule (I call up the program from a terminal) it returns with a failed status or -1

---

### Post by Aphotic on 2012-05-02
I resolved the issue by piddling around with different variations of the advice already posted. I'm posting one of the 4 scripts and my crontab below:

Crontab:
```

SHELL=/bin/bash
HOME=/home/stefan
PATH=/usr/sbin:/usr/bin:/sbin:/bin

0 * * * * sh /home/stefan/.scripts/gopurple.sh
15 * * * * sh /home/stefan/.scripts/goblue.sh
30 * * * * sh /home/stefan/.scripts/gogreen.sh
45 * * * * sh /home/stefan/.scripts/goorange.sh

```

Script:
```

#!/bin/sh
export DISPLAY=:0
killall conky
fbsetbg ~/.fluxbox/backgrounds/protophonic.jpg
conky -c ~/.conky/conkyrcpurp

```

Even within the shell script cron didn't seem to like the && command ties. 

I've attached an image showing the 4 appearances it cycles through. Thank you for your help and I hope some of this can help someone else in the future.

---

