---
title: "gedit has trouble opening some files"
date: 2006-02-27
forum: Desktop Environments
---

### Post by ashrack on 2006-02-27
When I try to open the following text file, I get the following error:
[ATTACH]6483[/ATTACH]
what can I do?

ps. I can open it without problems with NANO,ABIWORD, KWRITE 
ps2. the same thing also happens on my desktop(see sig)

---

### Post by taurus on 2006-02-27
See if you can view it from a terminal with more,

```

more /var/log/hibernate.log

```

---

### Post by ashrack on 2006-02-28
[QUOTE=taurus]See if you can view it from a terminal with more,

```

more /var/log/hibernate.log

```[/QUOTE]
ups, forgot to write an important thing to the first messeage. 
Yes it opens. 

ps. Just tried this:
I deleted multiple entries in 'hibernate.log' with ABIWORD so that it is now only 5.5kb in size, whilst B4 it was more arround 400KB and now GEDIT opens it.
So it is my believe that this error is caused by the size of a certain file.
Is this a bug in GEDIT or more of a "feature"?? 
ps. I have tested this on a another computer and I get the same results there

---

### Post by ashrack on 2006-03-02
bump

---

