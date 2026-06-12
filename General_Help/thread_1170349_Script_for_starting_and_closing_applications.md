---
title: "Script for starting and closing applications"
date: 2009-05-26
forum: General Help
---

### Post by K.L. on 2009-05-26
Hello!
 

 I'd like to know if it's possible to make a script, which would do something like this:
 

 It should look if the program (FireFox, for example) is running, if so, then it should close it, but if the program isn't running, it should start it.
 

 Thanks!

---

### Post by K.L. on 2009-05-26
I did it :)

```

#!/bin/sh

if firefox > /dev/null
then
    pkill firefox
else
    firefox
fi
```One question... Is **pkill** right command to close programs? It gets the job done, but I am not sure about it...

---

### Post by kpkeerthi on 2009-05-26
pkill should be fine. You could also use **kill** or **killall**. 

But I'm quite doubtful about your script, although I'd love to be proved wrong :) Does it close firefox if it is already running? It appears to me that it would only launch firefox.

---

### Post by K.L. on 2009-05-26
Well, it works for me :D

What the... It worked for me once, but it doesn't close FireFox now... Back to Googling I guess :D

EDIT: Nevermind what I wrote... It works... Most of the time... :D

---

### Post by K.L. on 2009-05-26
I have changed my script a bit. So far the new one works well (Actually I have no idea what's the difference between **firefox **and **./firefox**, but it did the job)

```

#!/bin/sh

if firefox > /dev/null
then
    pkill firefox
else
    ./firefox
fi
```

---

### Post by geirha on 2009-05-26
pkill will return true if it finds a process by that name and successfully kills it. If it doesn't find the process, or it's unable to kill it, it will return false. So, you could do that on one line
```
pkill firefox || firefox &
```

---

### Post by K.L. on 2009-05-26
Thank you, geirha. It works! :D

---

