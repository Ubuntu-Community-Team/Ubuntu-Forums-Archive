---
title: "Need help with resetting menu editor"
date: 2016-06-26
forum: Desktop Environments
---

### Post by andreadixon825 on 2016-06-26
Hi, I’m having trouble with getting my menu editor to save, so I was wandering how I would reset the menu editor back to normal for xubuntu. Thanks

---

### Post by &amp;KyT$0P# on 2016-06-26
Which menu editor are you using?

---

### Post by andreadixon825 on 2016-06-26
just the one that comes with ubuntu and xubuntu.

---

### Post by &amp;KyT$0P# on 2016-06-26
There are several of them and last I checked they save quite differently...

Make sure any menu editors are closed, then try moving the file [FONT=Courier New]~/.config/menus/xfce-applications.menu[/FONT] somewhere else (such as on an external drive), then log out and log back in, and see if your menu is better?

---

### Post by andreadixon825 on 2016-06-26
Hi, I just tryed it and it did not work, for some reason when I try to save in the menu editor it dose not work, and now I cant seem to get it all back I dont know what I did but its mists up now. I will find another way around it thanks everyone.

---

### Post by yoshii on 2016-06-27
This is what I did:  [http://ubuntuforums.org/showthread.php?t=2327706&highlight=whisker+menu](http://ubuntuforums.org/showthread.php?t=2327706&highlight=whisker+menu)

There's a bug in the menu editor on v16.04 LTS of XFCE (in Ubuntu Studio).  I think the bug is listed in the release notes, but I can't remember for sure.  
Anyways, the main idea is if the instructions above work, then don't edit the menus or it will happen again.  But you can still use the Favorites function.

---

### Post by Haven_McClure on 2016-09-06
> **yoshii said:**
> This is what I did:  [http://ubuntuforums.org/showthread.php?t=2327706&highlight=whisker+menu](http://ubuntuforums.org/showthread.php?t=2327706&highlight=whisker+menu)

There's a bug in the menu editor on v16.04 LTS of XFCE (in Ubuntu Studio).  I think the bug is listed in the release notes, but I can't remember for sure.  
Anyways, the main idea is if the instructions above work, then don't edit the menus or it will happen again.  But you can still use the Favorites function.

I ran across this bug too. How do I find this file and how do I delete it?   This might seem like a dumb question, but I genuinely can't find the answer.  Going through the system menus doesn't show me this file.

---

### Post by &amp;KyT$0P# on 2016-09-06
just open a terminal and enter this command
```
mv -v ~/.config/menus/xfce-applications.menu ~/old-xfce-applications.menu
```

This saves the other file to "old-xfce-applications.menu" in your home folder, safer to do this than just outright delete.

---

### Post by Haven_McClure on 2016-09-06
Super awesome--that did the trick!!!  Thank you so much! This thread should probably be marked as "solved."  I don't think I can do that as I didn't start the thread.

---

### Post by &amp;KyT$0P# on 2016-09-06
You're welcome!  :KS

---

