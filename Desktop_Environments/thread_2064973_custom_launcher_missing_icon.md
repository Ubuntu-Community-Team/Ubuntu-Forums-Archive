---
title: "custom launcher missing icon"
date: 2012-09-30
forum: Desktop Environments
---

### Post by markMDW on 2012-09-30
In 12.04 I created a custom launcher by right clicking the desktop, creating an empty document, filling in the script, then renaming it to mylauncher.desktop and then finally moving it to the Unity Panel (I can't remember what the proper name for that bar is).  It opens the program but my icon doesn't show up.  Can anyone tell me what's wrong?  I kept checking the path over and over again, but it appears correct.  Is the Unity Panel unable to display png files as icons perhaps?  Instead of showing the icon it shows a blank question-mark. 

```
[Desktop Entry]
Type=Application
Terminal=False
Name=SnowFlakePro
Icon=/usr/local/Snowflake\ Pro\ 1.1.1/JExpress/SnowflakePro.png
Exec=/usr/local/Snowflake\ Pro\ 1.1.1/SnowPro
```

---

### Post by markMDW on 2012-09-30
Got it to work now.  I created a new launcher by the same method.  For some reason I didn't have to us the backslash to escape out the spaces in the path.  The Exec command accepted it fine, but not the Icon command.  Could someone explain this to me?

Oh I forgot to mention in the earlier post that I did go to [properties] for the document and check it [x] as executable, just for other information of other newbies reading this.. the program has always executed it just didn't have the nifty icon.

well, if I want to figure out how to do something, it never fails, I always have to ask the question here first.  :guitar:

```
[Desktop Entry]
Type=Application
Terminal=False
Name=SnowFlakePro
Icon=/usr/local/Snowflake Pro 1.1.1/JExpress/SnowflakePro.png
Exec=/usr/local/Snowflake\ Pro\ 1.1.1/SnowPro
```

---

