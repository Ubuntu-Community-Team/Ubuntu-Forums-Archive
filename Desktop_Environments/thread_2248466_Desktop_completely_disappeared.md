---
title: "Desktop completely disappeared??"
date: 2014-10-15
forum: Desktop Environments
---

### Post by Comicalizard on 2014-10-15
I was surfing the web and received an empathy crash update. I hit continue and tried to relaunch and crashed again. Then I could not open the input keys or whatever it was under settings because it crashed (was trying to get rid of the "EN" box at the top right of the screen. Somehow I opened Steam just fine and then I tried to restart it and now no dash is showing besides my wallpaper. I cant even bring up terminal with the hot keys. If I type it open a little box in the bottom right hand corner of the screen and if I hit enter it goes away and nothing happens. I can however for whatever reason right click the desktop and am able to see "New Folder" "New Document" "Paste (greyed out of course)" "Organize Desktop by Name" "Keep Aligned" "Change Desktop Background". I am at a total loss right now and I am unable to get into terminal. Help! ](*,)

Edit: I am currently running 14.04 LTS

---

### Post by Bucky Ball on 2014-10-15
Personally, I would use ctrl+alt+F1, login then issue:

```
sudo reboot -h now
```

... and see if a restart fixes the issue. It will at least allow you to dig further for what may have caused the issue.

---

### Post by Comicalizard on 2014-10-15
I tried Ctrl+alt+F1 as well It just sends me to a black screen and shows absolutely nothing. The only thing I see is my backlight is on.

---

### Post by Bucky Ball on 2014-10-15
Tried ctl+alt+F2 or F* up to F6? Any different?

---

### Post by Comicalizard on 2014-10-15
No, Same thing. The only thing I can see is F7..which just brings me back to where I was haha.

---

### Post by Comicalizard on 2014-10-15
From the Installer boot menu on my USB I selected the check for disk defects option and after a short period this is the result...
"Checked finished: errors found in 2 files! Press any key to restart"

---

