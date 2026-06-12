---
title: "Launching Firefox at startup"
date: 2010-11-07
forum: Desktop Environments
---

### Post by scuccii on 2010-11-07
Okay - I just upgraded to 10.10 and I was previously able to run the following command in startup applications preferences menu "command" box to have firefox launch around the time that my wireless card came up:

sleep 20; firefox

For some reason this doesn't work anymore. I can run the command from the terminal and it works fine. Is there something that I'm missing?

Thanks.

---

### Post by P4man on 2010-11-08
Now that you mention it. To help someone else out as test I added something to startup applications (sleep 10; feh whatever) and I forgot about it until I tried KDE and the app would start on logging in. In gnome it doesnt start anymore. It used to though. No idea either. Ill look further in to it.

---

### Post by P4man on 2010-11-08
Yep. Confirmed. If I remove the sleep 5 then it launches on session start. With the sleep command, it doesnt work.

When I put the exact same command (with sleep) in a bash script and I run that script on startup, it works again.

I wonder if this is related to this bug I reported a while ago:
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/661271](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/661271)

---

### Post by scuccii on 2010-11-08
Very weird - If I wanted to create a persistent bash script that would run at logon how would I do this?
 
I know the command "sleep 20; firefox" works fine. But how would I get it setup as a script that runs at startup?
 
Thanks.

---

### Post by P4man on 2010-11-08
just create an text file and put this in:

```

#!/bin/bash
sleep5; firefox
```

Save, right click the file and  in properties make it executable. Now call that script from startup applications. Im sure there are more elegant ways but it works.

---

### Post by scuccii on 2010-11-08
Thank you!!

---

