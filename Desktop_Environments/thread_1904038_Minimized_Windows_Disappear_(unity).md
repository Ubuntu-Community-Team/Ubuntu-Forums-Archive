---
title: "Minimized Windows Disappear (unity)"
date: 2012-01-03
forum: Desktop Environments
---

### Post by dvlchd3 on 2012-01-03
I'm having a problem with Unity.  I recently re-installed Ubuntu 11.10, and ever since, when I minimize certain applications, I cannot restore them.  Clicking the icon on the bar starts a new instance, and Alt+Tab does not list the open window.

It appears to only be limited to a few applications I use: Eclipse and VMware Workstation.

Is anyone else experiencing this issue and have a potential fix/workaround??

---

### Post by Lovegain on 2012-05-17
I have a similar problem on 12.04. I have only experienced this with Eclipse, and the projects I run from Eclipse. I don't know how VMWare functions, but I guess this could be a Java related issue.

To me, it doesn't happen everytime I minimise a window. Rather, it happens randomly even when I don't.

I can always reach the window by moving or minimising windows that are in the way. However if I happen to minimise the Eclipse window, there's no way to get back to it. Then I have to kill and start it again.

---

### Post by markbl on 2012-05-17
This bug is one of the ones I complained about in 11.04. It was in 11.10 and I was shocked to see it also in 12.04. Some apps either always or sometimes just don't appear in the Unity launcher once minimised. For me it is kmymoney that fails to appear. Not in alt+tab either but I do see it in super+w. There are various bugs about it across launchpad but, as anybody who visits launchpad would know, bugs can sit there for years with no activity other than massive "me too" comments being added.

This is one of the reasons I use gnome-shell. Gnome-shell never loses apps from the launcher. I just don't understand how the Unity launcher can be so flaky that this bug can not be fixed after all this time. There must be sometime flawed about it's design?

---

### Post by mchurichi on 2012-06-07
Same problem here :(
Is there a bug ticket for this issue?
Ubuntu 12.04, with MySQL Workbench, DBeaver and a few others Java applications.

---

### Post by markbl on 2012-06-07
> **mchurichi said:**
> 
Is there a bug ticket for this issue?

Here is [bug 772063](https://bugs.launchpad.net/unity/+bug/772063) I refer to. Note that a fix for this appeared in the repos only about 2 days ago in the unity package. So make sure you update your system and try again.

---

### Post by mchurichi on 2012-06-07
> **markbl said:**
> Here is [bug 772063](https://bugs.launchpad.net/unity/+bug/772063) I refer to. Note that a fix for this appeared in the repos only about 2 days ago in the unity package. So make sure you update your system and try again.

It works like a charm!!

---

### Post by roudy1989 on 2012-10-13
Just had this bug again. After restoring my laptop from sleep I could ALT+Tab to the applications and they get "restored" but there was nothing shown but the global menu of either application. Those applications has been (not all I can remember) thunderbird, eclipse. So it is not really fixed at all.

---

