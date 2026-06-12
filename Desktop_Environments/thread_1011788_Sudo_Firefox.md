---
title: "Sudo Firefox"
date: 2008-12-15
forum: Desktop Environments
---

### Post by macca5 on 2008-12-15
i've been unable to navigate firefox properly for a few days, ie can't move backwards or forwards, the keys are greyed out. i discovered if i run firefox with sudo then i regain the navigation keys. i've also noticed i can't change my system settings, tell a lie i can for about a second then the settings revert back. i guess it's some permissions issue.

---

### Post by Vantrax on 2008-12-15
make sure you own your .mozilla file and you have access write access to the programs folder.

---

### Post by RJARRRPCGP on 2008-12-15
If that happened to me, I would fire someone! LOL! 

>root and internet DON'T go together!< 

!Even saying root and internet in the same sentence is blasphemy!

That would be like *cough cough* Microsoft, with XP and earlier.

---

### Post by cammin on 2008-12-15
It's probably a corrupted firefox profile.

---

### Post by aysiu on 2008-12-15
**Step 1**
Close Firefox completely

**Step 2**
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R $USER:$USER ~/.mozilla
```

**Step 3**
Start Firefox normally

**Step 4**
_Never_ run the command *sudo firefox* ever. If you're using the Mozilla Firefox (not Ubuntu repositories Firefox), you can use the command ```
gksudo firefox
``` to install updates.

For more information, read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by macca5 on 2008-12-23
Thanks Aysiu, that fixed it. I'm guessing it's a similar problem for my system settings any ideas how i chmod that

thanks again

---

### Post by s3gfault on 2008-12-23
Just do the same thing, but to your whole profile
```

cd
sudo chown -R $USER *

```
The -R means recursive (so it goes into subdirs), the asterik matches every file and directory.  

Stuff like this happens when you run programs as root.  The thing is, root is a completely different user, not a different operating mode for the same user.  So processes launched by root create files that are owned by root.  and then you cannot access those files as your normal user.

---

