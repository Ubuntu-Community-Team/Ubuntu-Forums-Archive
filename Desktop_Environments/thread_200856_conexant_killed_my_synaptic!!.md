---
title: "conexant killed my synaptic!!"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Kishore Sundara-Rajan on 2006-06-20
I was trying to get conexant drivers installed on my Dell Inspiron 6000 just incase I ever needed to use dial-up. Somewhere in something went terribly wrong during the instal process, and now synaptic gives me an error everytime I try to apply any changes. Here is what I get when I try to un-install the errornous package, and synaptic now wouldn't even let me "unmark" the package. HELP!!!

```

Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--remove):
subprocess post-removal script reutnred error exit status 1
Errors were encountered while preocessing:
 conexant
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

```

PS: The terminal window wouldn't allow copy-paste, so the error above was manually typed in.

---

### Post by Kishore Sundara-Rajan on 2006-06-24
Hello, Anybody? Please? Pretty Please?

---

### Post by YinZen on 2007-02-08
I have the exact same problem. I seem to have tryed everything that people have done during similar problems, the most promising being:
```
sudo dpkg --remove --force-depends --force-remove-reinstreq conexant
```
but even this gives the same output as in the top post.

Its really annoying as i cannot use any packadge management tools as it continuousely errors out. If i try and open synaptic i get..

```
E: The package conexant needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

..and then its just a blank packadges window with no options to uninstall or remove.
Would clearing the cache help?

Thanks
Jake

---

### Post by YinZen on 2007-02-08
Just realised this is a thread posted in the wrong section

Im going to end posting now and start a new thread in the right section

-----------------------------------------------------------------------------------------------

---

