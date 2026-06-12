---
title: "Screenlets: some start, some do not"
date: 2011-02-08
forum: Desktop Environments
---

### Post by nmcgrew on 2011-02-08
I installed screenlets last night and the weather widget starts regardless of how many times I delete it.  The cairo clock will not start no matter how many times I add it and tic the auto start box.  So I uninstalled screenlets this morning to start over and it's still doing the same thing.  Does anyone know of a way to fix this?  Thanks.

---

### Post by Frogs Hair on 2011-02-08
Try ```
sudo apt-get remove --purge screenlets 
``` and reinstall . I used Screenlets on 9.10 , but found them to be flaky on 10.04 and 10.10 in terms remembering settings.

---

### Post by nmcgrew on 2011-02-08
> **Frogs Hair said:**
> Try ```
sudo apt-get remove --purge screenlets 
``` and reinstall . I used Screenlets on 9.10 , but found them to be flaky on 10.04 and 10.10 in terms remembering settings.

nope, didn't work.  the weather is still loading although i believe the clock is also loading now.  it's annoying but i'll just keep deleting that screenlet upon start up.  thanks though!

---

### Post by Frogs Hair on 2011-02-08
I have not used screenlets in a while and I thought the purge may wipe out the configuration . I think wiping out the whole thing including the folder/s is the only way to start fresh. The folders are located in File System > usr/share/screenlets/screenlets mananger.

---

### Post by VCoolio on 2011-02-08
I recognize the issue, don't really have an answer. I just run screenlets directly on startup instead of launching the manager. Add a script with a command like this to startup applications:```
sleep 10 && python $HOME/.screenlets/AnotherFolderView/AnotherFolderViewScreenlet.py &
sleep 10 && python $HOME/.screenlets/AnotherScreenlet/AnotherScreenlet.py &
# etcetc if necessary
```

---

### Post by Frogs Hair on 2011-02-08
The configuration folder can be found in Home > Hidden folders .screelets and will remain after the program has been removed. Remove this one also. Use Ctrl+H to display hidden folders.

---

