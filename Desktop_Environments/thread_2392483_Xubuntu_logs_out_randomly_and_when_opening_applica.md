---
title: "Xubuntu logs out randomly and when opening applications"
date: 2018-05-21
forum: Desktop Environments
---

### Post by vermox on 2018-05-21
I've done some research on this issue but none of the answers seem to be specific to this issue.

I installed Xubuntu 18.04 on a desktop yesterday. It has an issue where it will log me out and when I log back in all my applications are closed which is a huge problem when I'm in the middle of something and haven't saved for a few minutes. Most of the time it will happen when I open an application with no apparent pattern as to which application, and sometimes it will do it randomly, seemingly without any connection to opening applications.

These are my system details:
```


GNOME 3.28.1 (Ubuntu)
CPU AMD FX(tm)-6300 Six-Core Processor
Graphics NVIDIA Corporation GP108(rev a1)(prog-if 00 [VGA controller]}
        Subsystem: Gigabyte Technology Co.. Ltd GP108 [GeForce GT 1030]


```

Any help is very much appreciated as I'm considering installing a different OS but would like to stick to Xubuntu if possible.

---

### Post by kerry_s on 2018-05-21
so you installed xubuntu on top of ubuntu?
> GNOME 3.28.1 (Ubuntu)

---

### Post by vermox on 2018-05-21
I can't remember if I downloaded it from the Ubuntu site or the Xubuntu site. However, this would indicate that it is Xubuntu over Ubuntu which is not what I wanted. I didn't know that would be the case when I installed it. Does this make a difference?

---

### Post by kerry_s on 2018-05-21
i don't think so, but i make it a rule to never mix, to many unexpected crap.

xfce4 is the ui & it sounds like it's crashing, which throws you to the login.
do you have the proper nvidia drivers installed for your card?

---

### Post by Autodave on 2018-05-22
A RAM stick is also another possibility. Especially since it happens when opening a program.  You may want to run a memory test to make sure.

---

### Post by kazakore on 2018-05-22
Is there anything logged by dmesg which may give you some pointers of where the problem lies?

---

