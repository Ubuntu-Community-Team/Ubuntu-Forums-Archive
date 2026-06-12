---
title: "Windows maxmise height when moved from one screen to another"
date: 2011-11-30
forum: Desktop Environments
---

### Post by IanWood on 2011-11-30
Hi,

I am using Kubuntu 11.10 with KDE 4.7.3. with three screens.

With certain applications when moving a window from one screen to another it maximise height wise, the width is unaffected. 

It only happens to some things, Thunderbird and one java app so far. 

Kate and Konsole used to fill horizontally but there was a conf changed I made in ~/.kde/share/config/konsolerc and katerc.

This problem is very annoying and I would appriciate any advice.

Best regards,

Ian

---

### Post by IanWood on 2011-12-02
Fixed by fiddling with the settings in WindowMenu - Advanced - Special Application Settings - Size & Position Tab. I changed the Maximised vertically setting to "Do Not Affect". 

I don't think I ever changed to it be maximised vertically but this seems to have fixed it.

---

### Post by drmrgd on 2011-12-02
I think something changed in KDE recently to do that.  I've been having similar problems with some windows in the last week or so, although I really don't know what was changed / updated to do it.  Anyway, I've found that messing with those settings you mentioned also seems to have fixed it for me too.  I wonder if this is some kind of bug.

---

### Post by IanWood on 2011-12-02
ummmm, perhaps its a bug. 

Ironically enough, the app causing me the most problems is an internal tool writren by us to view logs, which we often call the "BugViewer". It starts of maximised vertically, so I suspect that somehow sticks..

Kate and Konsole for a while maximised horizontally...

These settings are pretty usefull, I was able to set the shortcut for Thunderbird to be Meta+E so whenever I start it I can get it from any desktop easily.

---

### Post by drmrgd on 2011-12-02
One other thing that seems to work for me is when I open a window that seems to abnormally maximize in the way you describe, I right click on the window title in the taskmanager in the panel and uncheck the "maximize" button.  After doing that, the application seems to work normally again.

Also, for what it's worth, Kate and Konsole were the first two that started doing it for me too.

---

### Post by IanWood on 2011-12-05
Thanks - may look at using that technique too.

---

### Post by IanWood on 2011-12-05
yes - that works. Firefox just started playing up, ffs. 

Thanks for the tip.

---

### Post by drmrgd on 2011-12-05
Cool!  I'm glad that worked for you!

---

