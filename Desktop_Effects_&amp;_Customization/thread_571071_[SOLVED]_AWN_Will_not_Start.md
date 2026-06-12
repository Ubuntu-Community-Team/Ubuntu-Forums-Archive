---
title: "[SOLVED] AWN Will not Start"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by michiel.patrick on 2007-10-08
I have search everywhere and have not found an answer to this problem. I installed AWN and everything seemed to go fine with no error messages. I ran glxinfo | grep direct and my pc supports direct rendering. Has anyone found a solution to this problem?

---

### Post by michiel.patrick on 2007-10-08
I ran # awn-manager and got the following: (I have tried restarting also

/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:182: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 162, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 182, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue

---

### Post by Faud on 2007-10-08
I just want to make sure to ask. You are running beryl or compiz-fusion right ?

---

### Post by Faud on 2007-10-08
annnnnnnnnnnd someone please, please correct me if Im worng..Do you need python running for AWN. I dont remember. That could be a problem with Python

---

### Post by michiel.patrick on 2007-10-09
I got it working. I cannot remember how now but i went to awn forums and found out the problem. It was something simple.

---

### Post by hvc123 on 2007-10-12
i get that error ,, what was the fix ?

---

### Post by michiel.patrick on 2007-10-12
I have been running... i guess beryl. But i installed compiz and now am getting the problems. I am not sure if compiz caused the problems b/c i was installing quite a bunch of software when this happened. AWN was running fine before this.

---

### Post by michiel.patrick on 2007-10-12
Anyone have any ideas?

---

### Post by Islington on 2007-10-12
how did you install it? repo? make?

---

### Post by michiel.patrick on 2007-10-12
Not sure about that lingo... ha  im a windows guy. I installed compiz with synaptics package manager

---

### Post by michiel.patrick on 2007-10-13
bump ^

---

### Post by michiel.patrick on 2007-10-13
Ok I solved the problem and uninstalled compiz and reinstalled beryl.

---

