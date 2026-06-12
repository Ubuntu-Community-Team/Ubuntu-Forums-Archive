---
title: "Add Open Terminal to the RIght Click Menu"
date: 2005-11-01
forum: Desktop Environments
---

### Post by dez on 2005-11-01
Hi all, 
       I recently updated to Breezy, it all worked fantastically, congrats. Just one quick question: How do I get Open Terminal back into the right Click menu. (i.e. in Hoary, I could right click anywhere and get a terminal, the option has been replaced with New Folder, so I keep putting new Folders all over my desktop :) 

       Any help with this would be much appreciated, I apologise if this is the wrong place to ask this question, it seems like a Desktop issue.

---

### Post by psychicdragon on 2005-11-01
Yo,

**sudo apt-get install nautilus-open-terminal** will get it back for you.

---

### Post by dez on 2005-11-01
Bingo. 

4 minutes must be a record, I had barely finished my tea before I got the answer. 

Thanks psychicdragon.

Des

---

### Post by Othersider on 2005-11-23
```

me@localhost:~$ sudo apt-get install nautilus-open-terminal
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nautilus-open-terminal

```

Any idea what's wrong?

---

### Post by dbott67 on 2005-11-23
It could be a couple of things:

1. The packages list could be out of date.  Update your packages by typing:
```
sudo apt-get update
```
Then try installing nautilus-open-terminal again.

2. If that doesn't help, it may be in another repository.   Have you [enabled the other repos]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse")? 

-Dave

---

### Post by heimo on 2005-11-23
nautilus-open-terminal is in Universe, adding repositories:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by Othersider on 2005-11-23
Thanks for all the help.  I used the tutorial in heimo's post.

---

### Post by hvtuananh on 2008-01-13
> **psychicdragon said:**
> Yo,

**sudo apt-get install nautilus-open-terminal** will get it back for you.
It's not work for Ubuntu 7.10

---

### Post by jnylen on 2008-01-13
> **hvtuananh said:**
> It's not work for Ubuntu 7.10

nautilus-open-terminal IS available in 7.10, I have it installed.  Try enabling the extra official repositories like other posts in this thread have mentioned.  An easy way is to open Synaptic, go to Settings -> Repositories, and make sure everything on the Ubuntu Software tab is checked.  Then click Reload on Synaptic's toolbar.

---

### Post by hvtuananh on 2008-01-13
> **jnylen said:**
> nautilus-open-terminal IS available in 7.10, I have it installed.  Try enabling the extra official repositories like other posts in this thread have mentioned.  An easy way is to open Synaptic, go to Settings -> Repositories, and make sure everything on the Ubuntu Software tab is checked.  Then click Reload on Synaptic's toolbar.
Yeah. After install and restart, finally it works!

---

