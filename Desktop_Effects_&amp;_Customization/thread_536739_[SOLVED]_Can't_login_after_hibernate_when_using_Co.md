---
title: "[SOLVED] Can't login after hibernate when using Compiz"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by mindhaq on 2007-08-28
Hi,

I'm using Ubuntu 7.04 with Desktop Effects enabled (plain Compiz, no Beryl or Fusion) with an Nvidia card. This works quite well, even with my dual monitor setup.

But I effectivly can't use Hibernate. When the PC wakes up, I need to enter my password. In this dialog, hitting enter or clicking the OK buttons does nothing, not even an error. The password is correct 100%. I can switch back to the user selection screen, and restart the PC from there, but if I select the already logged in user, I'm stuck again with entering my password.

When I disable desktop effects, this works without a problem.

Did anyone stumble upon this as well, and can help me on this?

Thanks a lot,

mindhaq

---

### Post by michael37 on 2007-08-30
Your question is going stale... Do you use an USB keyboard or/and mouse?  I recall someone modified hibernate scripts to unload USB drivers before hibernate and load them after wake up.  Try googling for this, sorry, I don't have any more details.

---

### Post by mindhaq on 2007-08-31
Yes, I'm using an USB mouse.

But I don't think it is related to USB. I can use the mouse and keyboard just fine - except that action for submitting the login credentials. Hitting Enter does nothing, clicking OK neither. And this is just for the login dialog.

---

### Post by michael37 on 2007-08-31
Try using hibernate using this method: [thread]471855[/thread]

---

### Post by mindhaq on 2007-09-01
I followed this thread, where I followed to a more stable howto here: [http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

But I didn't try changing hibernate behavior.

But in that thread, I found a link to here:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

So I put this into my xorg.conf

```
Section "Device"
        ...
        Option          "NvAGP"       "1"
EndSection

```

and after a restart I tried Hibernate and now I was able to log in

:popcorn:

---

### Post by michael37 on 2007-09-01
Woohoo, mark the thread "SOLVED"

:popcorn:

---

