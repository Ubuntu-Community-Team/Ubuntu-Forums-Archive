---
title: "Java Apps Blank Windows/Hot Keys"
date: 2009-01-02
forum: General Help
---

### Post by Gotit on 2009-01-02
I am having a problem with my Java Apps intermittently rendering blank/empty windows.  I have searched the forms and found a work-a-round (unitl Java 1.6.0_10 is in the repos) by adding:
```
export AWT_TOOLKIT="MToolkit"
```
to the end of: 
```
/etc/profile
```
and that fixed the blank window problem. **But** (and there's always a but) that "fix" causes my hot-keys (ctrl+f to invoke a "find" form window) not to work in the Java App.

Does anyone know of another command to add to etc/profiles that will allow hot-keys to work with MToolKit? 
Thanks.

---

### Post by Gotit on 2009-01-22
Running my Java/Swing apps on a local 1.5.16 version of Java seems to have resolve all my problems with the Java/swing app functionality. The font isn't as good as Java 6, but hey, it works!! 

Note: I also tried a local 1.6.10 and 1.6.11 but those version of Java also have this same issue.  Maybe someday Java 7 will do the trick :-?

---

