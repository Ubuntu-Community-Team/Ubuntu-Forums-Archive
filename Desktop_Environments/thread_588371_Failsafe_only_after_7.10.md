---
title: "Failsafe only after 7.10"
date: 2007-10-23
forum: Desktop Environments
---

### Post by samjaynes on 2007-10-23
Thank you for reading this thread.  I have a Dell GX260 tower which I have ran both Edgy and Feisty releases on it.  I dowloaded the Alternate CD, and run the upgrade which seem OK (with a few confusing keep, replace dialog boxes).   On Saturday, it said there was 192 patches available which I applied.   There was a message about xorg or xsession, but just info.  After restart, I tried to sign on and the screen would just flash a couple times and go back to the log-in.  I tried all four options before results to failsafe.  Failsafe will load, and I am able to access my FE/BE MythTV, etc... but I would like to get this back to normal.   Thoughts, suggestions, log files needed?

---

### Post by alastair on 2007-10-23
> **samjaynes said:**
> Thoughts, suggestions, log files needed?

X is not starting properly.

Probably something to do with a driver upgrade i.e. NVIDIA or ATI card driver. 
What card?

You need to look in :

```
/var/log/
```

for files :

```
/var/log/Xorg.0.log*
```

The GUI you are running might be a "failsafe" vesa mode - logged in Xorg.0.log.
The failing (ATI/NVIDIA) driver load might be in /var/log/Xorg.0.log.old.

The log files might help.

Cheers,

Alastair

---

### Post by samjaynes on 2007-10-29
Thank you for your response.  I have looked at the logs, with and without the .old extension.  Honestly, I am having a hard time understanding the content as it refers to the display adapters several times.  Would it be helpful to post the log file, and if so, are you looking for the log created when under fail safe conditions, or after the screen flashes and sends you back to the logon screen?  

Thanks again...

---

