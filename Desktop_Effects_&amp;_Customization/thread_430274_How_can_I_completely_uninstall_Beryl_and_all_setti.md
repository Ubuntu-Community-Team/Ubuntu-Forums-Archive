---
title: "How can I completely uninstall Beryl and all settings?"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by TheCleaner on 2007-05-02
On a whim I installed the beryl unsupported plugins, and now Beryl's cube is gone completed...the shortcuts don't even show rotation shortcuts, etc. in the Beryl Manager.

I tried uninstalling beryl and deleting the hidden directory with the ini file in it and then reinstalling beryl but it's the same as it was...no cube effect.

Anyone?  I'd hate to have to reinstall the OS just for this...but I like my cube!

---

### Post by Sand Lee on 2007-05-02
hmm have you tried:
starting synaptic package manager, 
searching for beryl, 
then selecting each installed component  with the  "Mark for Complete Removal" option?

---

### Post by TheCleaner on 2007-05-02
Yeah, I've done that...it seems to keep the settings for some odd reason...

---

### Post by rolf-c on 2007-05-02
You could also fire up a terminal and:

```
rm -r .beryl .beryl-managerrc
```

Just to be sure.

---

### Post by TheCleaner on 2007-05-02
Nope...no go...the folders aren't there anymore...man this sucks...

---

### Post by rolf-c on 2007-05-02
Hmm.

Which Beryl settings do you still encounter?

---

### Post by TheCleaner on 2007-05-02
I just got it working Rolf...but strange on how I did it.

I had to install .21 (I was on version .20 because of the Nvidia drivers and the whitescreen), then not launch it but uninstall completely and remove those .beryl files/folders.

Then I was able to reboot and install .20 again and it works...

Thanks for the help!

---

