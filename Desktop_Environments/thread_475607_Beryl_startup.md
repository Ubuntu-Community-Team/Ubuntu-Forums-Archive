---
title: "Beryl startup"
date: 2007-06-16
forum: Desktop Environments
---

### Post by 71CH on 2007-06-16
Hi all
I want beryl to startup when I turn on my laptop.  What I usually do is do ALT+F2 and open up beryl-manager and then do ALT-F2 again and startup beryl.  I know about sessions but beryl never works right when I do that.   I'm thinking part of the problem is the timing of when beryl startsup in relation to other startup programs?  Is there a way to delay beryl-manager and beryl starting up maybe like 30 seconds after GNOME and everything else startsup?  I'm not sure if I'm making much sense but can somebody please help me.

---

### Post by Soybean on 2007-06-16
Shouldn't beryl-manager launch beryl on its own? Why do you have to do both?

Anyway, sure, if a delay is all you need, make a script.
```

#!/bin/sh
sleep 30
beryl-manager &
sleep 1
beryl &

```
 
Drop the last 2 lines if you can get beryl-manager to auto-launch beryl. Adjust the 30 at the top if you find it's taking too long... that waits 30 seconds.

Anyway, save that script somewhere, let's call it "launchberyl.sh", then do a ```
chmod 755 launchberyl.sh
``` and then add the script as a startup program in your session.

---

### Post by 71CH on 2007-06-16
Hi
Thanks for your help.  I couldn't get this to work.  I tried to add the script as a startup by typing launchberyl.sh as the command.  Am I doing this wrong?

---

### Post by 71CH on 2007-06-16
nvm I got it working
thanks for your help

---

