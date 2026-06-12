---
title: "File Templates not working"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by xlinuks on 2007-12-02
Hi,
I have Gutsy and I have read around that to create a new "file template" (which is appears as a new option at right-click->Create Document->Your new file template) one has only to create the folder "Templates" and to drop there any templates you would like to pop up.
For some reason after doing this there seems to be no effect..
Could anyone share any idea why that might happen.
As a proof here's a screenshot which shows that I do have a folder with templates, and the right-click showing "No templates preinstalled" (as usually):
[http://xlinuks.googlepages.com/screenshot.jpg](http://xlinuks.googlepages.com/screenshot.jpg)

PS: I have even restarted the computer, that didn't help..

---

### Post by wjp.reg on 2007-12-02
[This helped me]("http://www.extremetech.com/article2/0,1697,2126528,00.asp") set them up..

Good Luck

---

### Post by xlinuks on 2007-12-02
Thanks.. I managed to add the option to open a terminal window in current folder using a right-click (which was another issue I was willing to solve some time later, but thanks to you I did it now).
The question about the non-working Templates folder is still open, did it work for you? If so, maybe there's something wrong with my installation..

---

### Post by wjp.reg on 2007-12-02
I created an Openoffice document template by saving a blank file in the tempate folder as directed.

---

### Post by xlinuks on 2007-12-02
Thanks! now I know that it's an issue with my _personal_ installation..

---

### Post by wjp.reg on 2007-12-02
> **xlinuks said:**
> Thanks! now I know that it's an issue with my _personal_ installation..

Did you install the *nautilus-actions* package?

---

### Post by xlinuks on 2007-12-02
Yep.. it works fine, but it has to do (only) with context sensitive menus..

---

### Post by Tweenk on 2008-01-01
I have the same issue. Using Go->Templates in Nautilus menu goes to my home directory. I'm clueless already.

---

### Post by peddy on 2008-04-01
anyone found a fix?

---

### Post by tehkain on 2008-04-11
I am still having this issue, I deleted the folder(not needing templates at the time) and the recreated it. Now like the others it just takes me to my home folder and templates are not working.

Is there a gconf key?
[b]
edit: I solved the issue

nano ~/.config/user-dirs.dirs
and add the template directory
[/b]

---

