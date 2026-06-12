---
title: "firefox zombie - continues running after closing"
date: 2009-01-05
forum: General Help
---

### Post by doctordruidphd on 2009-01-05
I have seen posts related to this problem before; I hope I can add some specifics to the discussion.

Firefox: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.4) Gecko/2008102920 Firefox/3.0.4

OS: Ubuntu 8.10, Kde 4.1

After starting firefox, using it and then closing it, I find I cannot start it again. I get the message (don't remember the exact text) that firefox is currently running, and must be closed before starting a new session. Funny, when I really am running firefox on the screen and I try to open another session, I get a new window, not an error message. So something is whacky somewhere. I do not get this problem under debian-lenny/gnome-2.22, so I don't think it's a firefox problem. I can shut the system down with no trouble, and I can also kill it with "ps -e | grep firefox" and then kill the firefox.bin process. 
Also this problem does not occur with Thunderbird or Sunbird.

---

### Post by blubaustin on 2009-01-05
Try disabling all add-ons, it seems like add-ons make firefox continue to run.

---

### Post by scorp123 on 2009-01-05
> **doctordruidphd said:**
> I can also kill it with "ps -e | grep firefox" and then kill the firefox.bin process.  Why not use **pkill**? .... it's far more efficient. ```
pkill firefox*
```

Read here:

"How to get rid of dead processes"
[http://ubuntuforums.org/showpost.php?p=6198154&postcount=4](http://ubuntuforums.org/showpost.php?p=6198154&postcount=4)

---

### Post by binbash on 2009-01-05
I have same problem here and i am bored with pkill

---

### Post by leito666 on 2009-01-05
> **doctordruidphd said:**
> I have seen posts related to this problem before; I hope I can add some specifics to the discussion.

Firefox: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.4) Gecko/2008102920 Firefox/3.0.4

OS: Ubuntu 8.10, Kde 4.1

After starting firefox, using it and then closing it, I find I cannot start it again. I get the message (don't remember the exact text) that firefox is currently running, and must be closed before starting a new session. Funny, when I really am running firefox on the screen and I try to open another session, I get a new window, not an error message. So something is whacky somewhere. I do not get this problem under debian-lenny/gnome-2.22, so I don't think it's a firefox problem. I can shut the system down with no trouble, and I can also kill it with "ps -e | grep firefox" and then kill the firefox.bin process. 
Also this problem does not occur with Thunderbird or Sunbird.


I have the same problem under Windows, so I think is related with Firefox or with some pluggin (as someone says before)

---

### Post by giuspen on 2009-01-05
+1 same problem on gnome and windows

---

### Post by scorp123 on 2009-01-05
> **binbash said:**
> I have same problem here and i am bored with pkill Why not create a custom launcher script for Firefox? e.g. something like this:

**/usr/bin/Firefox-launcher.sh**
```
#! /bin/bash
/usr/bin/firefox
pkill firefox
```

Create a custom launcher e.g. on your desktop or on one of your panels and voila: you click on it and Firefox starts .... But when you quit Firefox "pkill" is triggered and if there are any remainders still around they'd get killed then, so you get to start Firefox again without having to bother to kill it yourself manually each time.

You could use this as workaround perhaps, until there is a definitive solution... ?

---

### Post by doctordruidphd on 2009-01-05
```
#! /bin/bash
/usr/bin/firefox
pkill firefox
```


Nice try, but it didn't work. Whatever is keeping firefox alive, prevents the script from completing its execution. pkill works fine, though. For me, it works perfectly in gnome/debian, and in windows, to the extent that anything works in windows...

---

### Post by scorp123 on 2009-01-05
> **doctordruidphd said:**
>  Whatever is keeping firefox alive, prevents the script from completing its execution. Can you give me the output of this command please _AFTER_ you tried to close Firefox: ```
ps -efH
``` I wonder what's keeping it "alive" ... maybe we could spot something in that output and try and kill it instead?

---

### Post by doctordruidphd on 2009-01-24
Solved
Some update fixed the problem.
Firefox closes normally now.

---

