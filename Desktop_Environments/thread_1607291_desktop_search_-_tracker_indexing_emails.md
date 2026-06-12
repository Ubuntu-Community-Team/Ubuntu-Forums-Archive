---
title: "desktop search - tracker indexing emails"
date: 2010-10-27
forum: Desktop Environments
---

### Post by ShouriChatterjee on 2010-10-27
Hello everyone,

Is there a way for tracker to index emails that are archived on disk, in a maildir format?

I do not use evolution or kmail or thunderbird. All my emails are on disk as maildirs. Earlier (till lucid), beagle was available - and beagle would index all of my email (and recognize it as email...) Now beagle is off the maverick repositories - it is no longer supported as development has ceased.

Now tracker does not index any of my email (in ~/Mail/) by default.

Do you recommend any other desktop search tool? Searching email is my primary requirement.

Thanks.

---

### Post by ShouriChatterjee on 2010-11-13
Sad to see that no one replied. I have a working solution, though.

1) tracker does not work. It cannot handle maildirs as of now. Someone has to write the code for it to do so. The developers say that the hooks are there.

2) I stumbled upon something called "mu" or "maildir-utils".

```
sudo apt-get install maildir-utils

```

mu (old name is maildir-utils) is a maildir indexer.

One needs to put it into the crontab:
```
*/5 * * * * mu index -m /home/shouri/Mail/

```

And this is the script I wrote for searching and viewing results in pine/alpine:

```

#!/bin/bash
searchfor=$(zenity --entry --text="Search for:" --title="E-mail search")
FOLDER=results
COLLECTIONID=4
LINKS="--linksdir=$HOME/Mail/Search/$FOLDER"
CLEAR="--clearlinks"
if [ "$searchfor" ] ; then
    mu find $LINKS $CLEAR "$searchfor"
    execstring="alpine -f $FOLDER -c $COLLECTIONID -I \"i\""
    gnome-terminal -e "$execstring"
else
    exit
fi

```

Suit the above code for yourself. This is specific to alpine (which is what I use to handle my email.)
$COLLECTIONID is the n-th email collection. 4th in my case.

---

