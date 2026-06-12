---
title: "Firefox 2 &amp; 3 crashing"
date: 2008-12-18
forum: General Help
---

### Post by John Long on 2008-12-18
Hey all,

I've been having serious issues with Firefox ever since upgrading to 8.04. My Firefox 3 browser was freezing up and constantly crashing. After going through a number of possible fixes that I found on the forums (uninstalling and reinstalling Flash, etc) I decided to go for Firefox 2 as I read that this version didn't have the same problem. Alas, the same thing is happening again with the same frequency. I'm getting pretty frustrated but would like to keep using Firefox. Any help will be very much appreciated. :confused:

---

### Post by unutbu on 2008-12-18
Quit firefox. Open a terminal and type
```

mv .mozilla .mozilla_20081218
```

This moves your firefox configuration directory to .mozilla_20081218. Now restart firefox. When it sees there is no .mozilla configuration directory, it will create a new one. 

Test out firefox. Does it crash? If it doesn't, we can work on restoring your bookmarks.

If it still crashes, then my guess is that something about your upgrade to 8.04 did not work properly. The "fix" in this case is to do a fresh install of 8.04. (If you have your /home on a separate partition, you can reinstall 8.04 to the / (root) partition without backing up. If /home is not on a separate partition, then you'll have to backup your data first).

---

