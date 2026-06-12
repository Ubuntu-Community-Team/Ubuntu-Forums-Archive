---
title: "Different UI Language per User -- possible?"
date: 2008-06-01
forum: Desktop Environments
---

### Post by Luffield on 2008-06-01
Hi,
I'm using Ubuntu 8.04 with the Gnome desktop, with English interface. I want to open a new user account which will have a different UI language, but I can't find a way to do it -- I can only change the UI language for *all* users (from the language settings application). Am I missing something or is it just impossible to do what I want?

---

### Post by KaliVoid on 2008-06-05
hi

look here : ["Per-user language support?"]("http://ubuntuforums.org/showthread.php?t=542463&highlight=user+language+interface"), that worked great for me

i just "sudo gedit" to the user file add the language, switch user and it work.

to find all your currently installed locales type in terminal
```
locale -a
```

---

### Post by Luffield on 2008-06-05
Thanks KaliVoid, it worked perfectly on my machine as well.
Funny, I searched the forums before I opened this thread but somehow managed to miss the thread you linked to.

---

### Post by czigor on 2010-06-22
For me editing the .dmrc file did not work. What did work was adding these lines to .profile:

export LANG=hu_HU.UTF-8
export LC_ALL=hu_HU.UTF-8
export LANGUAGE=hu_HU.UTF-8

---

