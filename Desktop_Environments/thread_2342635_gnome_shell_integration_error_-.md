---
title: "gnome shell integration error -"
date: 2016-11-08
forum: Desktop Environments
---

### Post by davehenson on 2016-11-08
Apologies for asking yet another question.  I am running UB 16.04LTS, UNITY desktop and I had gnome shell integration extension installed on chromium when I was running fedora. Now that I have installed UB, I log into chromium with my google account, it loads all my bookmarks, extensions etc and now I get a constant pop up that there is a Gnome Shell Integration error. "no such interface 'org.gnome.Shell.Extensions' on...???

screen pic attached. I'm at wit's end as it looks like I cannot remove the extension either. 

I tried several google searches as well as searches here but can't seem to find one that is newer than 3yrs old. 

Any ideas?  Let me know if there's more needed to help and I'll gladly post the info!

thanks. 

[ATTACH=CONFIG]272037[/ATTACH]

---

### Post by davehenson on 2016-11-08
sigh.....ever have a day that nothing seems to be going right?  The picture was right side up when I uploaded it!

---

### Post by davehenson on 2016-11-09
polite bump

---

### Post by davehenson on 2016-11-10
the answer is!!!!!!

```
sudo apt remove chrome-gnome-shell
```

---

### Post by dorian7 on 2017-09-01
This thread isn't exactly current, but I wanted to point out that if you remove chrome-gnome-shell and you're using the Gnome DE, it will also want to remove ubuntu-gnome-desktop.  You do NOT want to do this if you're using Gnome!

To disable shell integration updates in Chrome or Chromium, just right-click the foot icon next to the address bar, to go options, and turn off automatic updating.  Done.

---

### Post by oldos2er on 2017-09-02
Back to sleep.

---

