---
title: "No boot-up options"
date: 2011-04-10
forum: Desktop Environments
---

### Post by SheldonJ on 2011-04-10
I installed the Windows installer for Ubuntu, but when I re-booted, there were no boot options and it just booted up normally into windows. Does anyone know what the problem is?

Thanks.

---

### Post by Dutch70 on 2011-04-10
Hi and welcome to UF

You may be able to find some answers in the Wubi Megathread. 
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1639198[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by bcbc on 2011-04-10
> **SheldonJ said:**
> I installed the Windows installer for Ubuntu, but when I re-booted, there were no boot options and it just booted up normally into windows. Does anyone know what the problem is?

Thanks.

One reason is that Wubi failed to set the boot manager timeout to > 0 and so you don't get a prompt. Another is that it failed to create an ubuntu entry in the boot manager.

Check by right clicking on My Computer, Properties, Advanced, Startup and recovery settings. 
In there you should see a drop down that shows Windows (default) and Ubuntu. The timeout should be 15 or 30. If the timeout is zero increase it. 

If Ubuntu is missing, it's possible to add a manual entry but the method depends on what version of windows you are using.

---

### Post by SheldonJ on 2011-04-12
Thank you! It works fine now.

---

### Post by Dutch70 on 2011-04-12
Great! glad to hear you got it working.

If you're satisfied, please mark this thread "Solved" with Thread Tools at the top of the page.

---

