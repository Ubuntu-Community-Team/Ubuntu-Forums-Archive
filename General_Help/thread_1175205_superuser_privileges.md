---
title: "superuser privileges"
date: 2009-05-31
forum: General Help
---

### Post by candymanmike on 2009-05-31
you guys helped me out with an installation problem problem a few days ago. i'm hoping you can be of some assistance again. i tried to listen to music on my computer and rhythmbox music player said i was missing the codecs. so it searched and found 2. i try to install them and i get an error message:
> [B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B] 
so i opened terminal and entered [B]dpkg --configure -a
[/B]terminal then told me:
> **dpkg: requested operation requires superuser privilege**

so since i am the** ONLY** user of this computer and obviously the admin, how am i possibly not authorized to do this? and how do i change it so i can? any help is truly appreciated. thank you in advance.

---

### Post by kk0sse54 on 2009-05-31
Type 'sudo' in front of the command and then enter your password when prompted (note when typing your password the field will still appear blank).

Basically what this means is that in most linux and Unix like OSs for enhanced security, your normal user account has restricted access to system files such as those under your root filesystem. This means whenever you want to install a piece of software you need to enter your password to gain temporary superuser access which is accomplished through the command "sudo." In this case we aren't installing a new package but the program that you're trying to run requires root priviliges so the command needs to be entered as ```
sudo dpkg --configure -a
```

Read here for more info on sudo, [http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo) and here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by candymanmike on 2009-05-31
thanks for the help. that did the trick.

---

