---
title: "Firefox crashed and won't open - error message"
date: 2011-05-26
forum: Desktop Environments
---

### Post by Jonners59 on 2011-05-26
I am on 11.04
Firefox suddenly stopped working after reboot.  I get the error message as shown in the enclosed screen shot.

Have gone in to Synaptic Package Manager to remove FF and reinstall, but I still get the same messages.

---

### Post by wildmanne39 on 2011-05-27
> **Jonners59 said:**
> I am on 11.04
Firefox suddenly stopped working after reboot.  I get the error message as shown in the enclosed screen shot.

Have gone in to Synaptic Package Manager to remove FF and reinstall, but I still get the same messages.
Hi, thats a strange message it mentions chrome and you are talking about firefox. You can use this command to get rid of all files that might have been left behind when you uninstalled ff the first time, you might want to uninstall chrome and reinstall it as well.
```
sudo apt-get --purge remove packagename
```

---

### Post by Jonners59 on 2011-05-27
> **wildmanne39 said:**
> Hi, thats a strange message it mentions chrome and you are talking about firefox. You can use this command to get rid of all files that might have been left behind when you uninstalled ff the first time, you might want to uninstall chrome and reinstall it as well.
```
sudo apt-get --purge remove packagename
```

Thanks for this wildmanne39
Yes, it is odd.  I think I have installed something whilst looking for an alternative/fix for the Evolution bug issue.

Any way.  Tried the purge, rebooted and then re-installed via Synaptic Manager....  Failed again with the same message.  I have just installed Chromium to reply to you, which as you can see works.

Any other ideas?

---

### Post by wildmanne39 on 2011-05-27
> **Jonners59 said:**
> Thanks for this wildmanne39
Yes, it is odd.  I think I have installed something whilst looking for an alternative/fix for the Evolution bug issue.

Any way.  Tried the purge, rebooted and then re-installed via Synaptic Manager....  Failed again with the same message.  I have just installed Chromium to reply to you, which as you can see works.

Any other ideas?
Hi, I am sorry I am fresh out of ideas.

---

### Post by Jonners59 on 2011-05-27
> **wildmanne39 said:**
> Hi, I am sorry I am fresh out of ideas.

Cheers anyway....  Maybe someone else will see this and advise

---

