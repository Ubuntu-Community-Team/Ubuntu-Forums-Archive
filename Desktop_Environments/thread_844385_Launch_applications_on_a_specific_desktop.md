---
title: "Launch applications on a specific desktop"
date: 2008-06-29
forum: Desktop Environments
---

### Post by christophe.agostini on 2008-06-29
Hello there !

A few weeks ago I finally forsake Windows and switch to Ubuntu. Everything is just perfect, I'm so happy about this move ! Of course I had some problems but with the help of this forum and a book about how to use shell everything went fine. :guitar:

However I have a quick question : Is it possible to start an application directly on a specific desk? Let me explain: I add "transmission bittorent client" to the ubuntu sessions preference in order to make it launch when I log in. But I would like to make it start in my second desktop, not the main one. 

I searched a lot before but I didn't find anything, maybe I didn't the right keywords... Anyway, thanks a lot for your reading and your help :KS

---

### Post by pauper on 2008-07-19
Install either "wmctrl" or "devilspie".

```
sudo apt-get install wmctrl
man wmctrl
```

---

### Post by sdennie on 2008-07-19
If you are running compiz, you can do this.  First, get ccsm:

```

sudo apt-get install compizconfig-settings-manager

```

Then, go to System->Preferences->Advanced Desktop Effects->Place Windows (it will be towards the bottom).  In the Fixed Window tab, click new and for the text area type, "class=Transmission" and then select the viewport you want the app to appear on.

---

### Post by AzizLight on 2008-11-19
> **vor said:**
> If you are running compiz, you can do this.  First, get ccsm:

```

sudo apt-get install compizconfig-settings-manager

```

Then, go to System->Preferences->Advanced Desktop Effects->Place Windows (it will be towards the bottom).  In the Fixed Window tab, click new and for the text area type, "class=Transmission" and then select the viewport you want the app to appear on.

Thank you!

---

