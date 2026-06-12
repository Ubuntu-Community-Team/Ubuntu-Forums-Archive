---
title: "Watchdog script"
date: 2008-10-12
forum: Desktop Environments
---

### Post by WoPr on 2008-10-12
Hi all!

I need to make a program to control a file. If the file have a 0, the the process do nothing, but if the file have a 1, the process will execute a script.

Is there anyway to have a watchdog process or something like that?

Thanks in advance :)

---

### Post by jordilin on 2008-10-12
```

#!/bin/bash

while [ 1 ]
do
    NUM=`cat dog.txt`
    if [ $NUM == "0" ]
    then
        echo "hello"
    elif [ $NUM == "1" ]
    then
        echo "bye"
    else
        echo "nothing"
    fi
    sleep 2
done
```

You could put this in a cron job and remove the sleep and while. If you wanna learn bash scripting I would go to [The linux documentation project]("http://www.tldp.org")

---

### Post by WoPr on 2008-10-12
It works like a charm! :)

Thanks and best regards!!

---

### Post by lswb on 2008-10-12
You may also be interested in these and similar packages: dnotify and inotify-tools.

---

