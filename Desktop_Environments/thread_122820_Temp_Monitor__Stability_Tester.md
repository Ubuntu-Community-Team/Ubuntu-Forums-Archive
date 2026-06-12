---
title: "Temp Monitor / Stability Tester"
date: 2006-01-28
forum: Desktop Environments
---

### Post by Rock Lobstah on 2006-01-28
I want to see if I can get a higher OC in Ubuntu (64).. but I'm obviously going to need a temp monitor, and something to test stability and stress my CPU.

In windows I just used PCWizard and Prime95.

Any tips?

---

### Post by dcstar on 2006-01-28
[QUOTE=Rock Lobstah]I want to see if I can get a higher OC in Ubuntu (64).. but I'm obviously going to need a temp monitor, and something to test stability and stress my CPU.

In windows I just used PCWizard and Prime95.

Any tips?[/QUOTE]
lm-sensors to monitor.

---

### Post by Rock Lobstah on 2006-01-28
[QUOTE=dcstar]lm-sensors to monitor.[/QUOTE]

[http://secure.netroedge.com/~lm78/download.html](http://secure.netroedge.com/~lm78/download.html)

Should I get the latest version of those? (top one)

---

### Post by dcstar on 2006-01-28
[QUOTE=Rock Lobstah][http://secure.netroedge.com/~lm78/download.html](http://secure.netroedge.com/~lm78/download.html)

Should I get the latest version of those? (top one)[/QUOTE]
No idea, the current version works fine on my system.

---

### Post by Rock Lobstah on 2006-01-28
[QUOTE=dcstar]No idea, the current version works fine on my system.[/QUOTE]

I checked, and it is compatible with my kernel version.. so I got that.

But what the hell do I extract? I'm so bad with this stuff.. =/

[http://img72.imageshack.us/img72/9586/lmsensors4ad.jpg](http://img72.imageshack.us/img72/9586/lmsensors4ad.jpg)

---

### Post by bobpaul on 2006-02-26
Just use Apt, man.  Newest lm-sensors on the website, 2.10. Newest in aptitude, 2.9

```
 apt-get install lm-sensors 
```

Edit: Found a [HowTo](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm+sensors) in the forums.

---

