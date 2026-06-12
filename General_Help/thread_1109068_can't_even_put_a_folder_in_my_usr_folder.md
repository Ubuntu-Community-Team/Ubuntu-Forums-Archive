---
title: "can't even put a folder in my usr folder??"
date: 2009-03-28
forum: General Help
---

### Post by Shukero on 2009-03-28
I thought I'd try out ubuntu because I heard it was easier and much more reliable to use than windows, but I can't even put folders in my usr directory in order to make a theme work without getting a "permission denied." how can I remove this crap permanently? I'm tired of having to rely on the terminal for EVERYTHING.

---

### Post by Yownanymous on 2009-03-28
Unfortunately security comes at a cost, and Microsoft dump security for "satisfaction". To get root access to the file manager, type this in (yes, I know, Terminal): sudo nautilus

---

### Post by overdrank on 2009-03-28
You may use the alt, F2 keys and enter ```
gksu nautilus
```
Be very careful on any changes made.

---

### Post by VCoolio on 2009-03-28
Why don't you install themes the drag and drop way in the themes tab? (right mouse button on your desktop > desktop background). Themes will then be copied to /home/[you]/.themes (a hidden folder, press ctrl+h in nautilus to see them). No console needed. If you want the theme to be used by root apps like synaptic, you do need to move themes to /usr/share of course.

---

### Post by dcstar on 2009-03-28
> **Shukero said:**
> I thought I'd try out ubuntu because I heard it was easier and much more reliable to use than windows, but I can't even put folders in my usr directory in order to make a theme work without getting a "permission denied." how can I remove this crap permanently? I'm tired of having to rely on the terminal for EVERYTHING.

It is **not** "your" /usr directory, it is a system directory that you should never touch in normal operation.

Themes are supposed to be installed by admin level scripts that do have permissions to use that folder.

The reason you are not allowed to put things in there is because you - as a user- are not supposed to put things in there - your system is working perfectly.

---

### Post by ethoxyethaan on 2009-03-28
to install themes drag them in the theme window;

perhaps you should edit the root user account and run ubuntu as root like you do in windows, however it comes at a cost i'm not willing to pay.

---

### Post by 3Miro on 2009-03-28
Here is a nice article for new Linux users. Got it from someone else's signature and it is very good.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Do not run Linux as root (for that matter do not run windows as administrator). Most things under Linux can be done via graphical interface, people just give advices like: "type this in terminal", because it is easier than to explain: go to system -> admin -> blah blah, click blah click blah ....

You shouldn't have to install themes by manually moving files around (I wouldn't think so).

---

