---
title: "Uknown icon in menu bar"
date: 2017-01-11
forum: Desktop Environments
---

### Post by patslap on 2017-01-11
[[img]https://s30.postimg.org/9gq1ae135/Screenshot_from_2017_01_11_11_25_08.png[/img]](https://postimg.org/image/q4hjcvvul/)[upload pics](https://postimage.org/)

When I click on the 'no entry' icon on the menu bar, there is a drop-down box, but with no text nor indication of what this icon is.

I'd like to remove it. How can I find out what it is so I can remove it?

---

### Post by Habitual on 2017-01-11
Something to do with dropbox...I want to say, a client software left-over?

---

### Post by patslap on 2017-01-12
Any idea how to remove it - it's annoying to have it there - it only appeared a few days ago.

---

### Post by wildmanne39 on 2017-01-12
What version of ubuntu and what desktop are you using?

---

### Post by Taemojitsu on 2017-01-17
You could try looking for all 'indicator-' processes to find one that you don't recognize.

I think I've seen that before, but did have text associated: a problem with either a package upgrade (like not being able to download updates) or, less likely, wireless.

Maybe you could try to kill the indicator processes, one at a time, until none are left. If this is bad advice, someone please correct me.

---

### Post by Habitual on 2017-01-18
> **Taemojitsu said:**
> You could try looking for all 'indicator-' processes to find one that you don't recognize.
Should show up using 
```
lsof | grep -e panel | grep indicator
```

If you save your sessions upon exit, I'd open a terminal and issue a cleaning, eg:
```
rm -fr .cache/sessions/
```

Worth a shot?

---

### Post by patslap on 2017-01-18
Ubuntu 16.10 with Unity DE

---

### Post by Habitual on 2017-01-18
Easy test, 
Create a new user on the system and login as them. Test and Report.
Thanks.

---

