---
title: "netbeans-beryl wont showup"
date: 2007-03-04
forum: Desktop Environments
---

### Post by artificialman on 2007-03-04
Hi guys..

I use linux from last 9 years. 8 months back i shifted to ubuntu.. Recently i formatted my system  , as i am a Ruby/j2ee developer. i loaded jdk6 and netbeans with jboss and it runs like mustang. Unfortunately i was not fascinated for 3d desktop. As a matter of reasearch, I installed beryl on my dell xps m140 laptop.. beryl works fine , where as netbeans wont show up in the view/window,
what to do ? eliminate beryl or is there any solution... needed urgent solution?

artificialman

---

### Post by artificialman on 2007-03-04
hi guys 

never mind  i got the solution

added to /etc/environment

AWT_TOOLKIT="MToolkit"

and for look and feel executed the following

export _JAVA_OPTIONS="-Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel"

.........................god thanks...........................to this forum

artificiaman

---

### Post by yota on 2007-03-31
Thanks a lot!

AWT_TOOLKIT="MToolkit" worked great for me.

---

