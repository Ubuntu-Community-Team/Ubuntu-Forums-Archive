---
title: "Using Cron to Open GUI Program"
date: 2005-12-15
forum: General Help
---

### Post by xtacocorex on 2005-12-15
I have dailystrips set up to download Dilbert everyday at 6:30 am with a cron.

The cron looks like this
```

30 6 * * * /home/bobw/pictures/dilbert/getdilbert.sh

```

The cron runs the script, but after getting the comic I want kuickshow to open with the day's comic. 

Here is the script code
```

#!/bin/sh

# script to download dilbert every morning
# and then open the picture in kuickshow
# for viewing

# get comic
picloc=~/pictures/dilbert
dailystrips -l -q --noindex --basedir ~/pictures/dilbert dilbert

# get date in format that dailystrips uses
mydate=`date +%Y.%m.%d`

# get comic picture filename since 
# we won't know what downloaded
htmlfile="dailystrips-$mydate.html"
daycomic=`cat $picloc/$htmlfile | grep "img" | cut -d '"' -f2`

# show comic
kuickshow /home/bobw/pictures/dilbert/$daycomic

```

I've searched around, but couldn't find anything useful about it, mainly just how-to's on setting up cron jobs.

Is opening a GUI program allowed with cron and if it is, what am I doing wrong in the script?

---

### Post by xtacocorex on 2005-12-15
Answered my own question after further searching.

[http://ubuntuforums.org/showthread.php?t=73125&highlight=cron](http://ubuntuforums.org/showthread.php?t=73125&highlight=cron)

Sorry for the wasted thread space.

I really need to look harder before I post a thread...

---

