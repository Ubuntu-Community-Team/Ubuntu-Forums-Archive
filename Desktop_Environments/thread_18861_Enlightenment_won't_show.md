---
title: "Enlightenment won't show"
date: 2005-03-09
forum: Desktop Environments
---

### Post by Stefan Sager on 2005-03-09
I have read all the threads about enlightenment and found no solution to my problem.

I have installed Enlightenment but it won't show up among sessions when GDM-screen is started. I did put a file called enlightenment.desktop under /usr/share/xsessions with the following in it.
```
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Enlightenment
Exec=/usr/bin/enlightenment
Icon=
Type=Application
```

---

### Post by Qdlaty on 2005-03-09
Most obvious question - did you restart your gdm ?

---

### Post by lizardking on 2005-03-09
[QUOTE=Qdlaty]Most obvious question - did you restart your gdm ?[/QUOTE]
**watch the exec value: ** 

try with 

```
exec: enlightment
``` 

 :-({|=

---

### Post by lizardking on 2005-03-09
[QUOTE=Qdlaty]Most obvious question - did you restart your gdm ?[/QUOTE]
**watch the exec value: ** 

try with 

```
exec: enlightenment
``` 
not Exec=/usr/local/bin/enlightenment

 :-({|=

---

### Post by Stefan Sager on 2005-03-09
[QUOTE=Qdlaty]Most obvious question - did you restart your gdm ?[/QUOTE]
Yes, GDM restarts everytime one logs out?

[QUOTE=lizardking]**watch the exec value: ** 

try with 

```
exec: enlightenment
``` 
not Exec=/usr/local/bin/enlightenment

 :-({|=[/QUOTE]
Okey, I'll try that.

---

### Post by Qdlaty on 2005-03-09
NO!! GDM restarts every time you reboot yor machine or kill X!

---

### Post by Stefan Sager on 2005-03-09
[QUOTE=Qdlaty]NO!! GDM restarts every time you reboot yor machine or kill X![/QUOTE]
Or invoke-rc.d gdm restart

---

### Post by Stefan Sager on 2005-03-09
Enlightenment still won't show up among sessions... :-#

EDIT: It works, it works!
I had missed the Exec-parameter... ops!

---

