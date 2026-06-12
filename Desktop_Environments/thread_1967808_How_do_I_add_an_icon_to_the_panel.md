---
title: "How do I add an icon to the panel?"
date: 2012-04-28
forum: Desktop Environments
---

### Post by walterbyrd on 2012-04-28
I want to add the Screenshot icon to the panel. I want to be able to launch the screenshot application from the panel, instead of having to go to the menu. 

Any advice appreciated. Thanks in advance.

---

### Post by Rex Bouwense on 2012-04-28
Right click the panel, then go to Add Remove Panel Items.  Choose Application Launch Bar->edit->Accessories->LXScreenshot.  Click add and there you are.

---

### Post by JC Cheloven on 2012-04-28
Mmm... what's wrong about just hiting the PrntScr key (or Alt-PrntScr for a picture of the active window)?

Perhaps it doesn't work for you? It didn't work for me either, due to a small misconfiguration in the file ~/.config/openbox/lubuntu-rc.xml. At some point (for picture of current window) it says <execute>scrot -s</execute>, and it should say ```
<execute>scrot -u</execute>
```

If that was your problem, I hope this will help.

JC

---

### Post by kansasnoob on 2012-04-28
Since you used the Lubuntu tag I'll assume you're using lxpanel so this may be helpful:

[http://ubuntuforums.org/showpost.php?p=11780626&postcount=4](http://ubuntuforums.org/showpost.php?p=11780626&postcount=4)

---

### Post by rg4w on 2012-04-28
> **Rex Bouwense said:**
> Right click the panel, then go to Add Remove Panel Items...
I haven't been able to get a context menu in the top panel since the advent of Unity.  Is this supposed to work in 11.10?

---

### Post by kansasnoob on 2012-04-28
> **rg4w said:**
> I haven't been able to get a context menu in the top panel since the advent of Unity.  Is this supposed to work in 11.10?

Since this thread has the Lubuntu tag it likely has nothing to do with Unity.

---

