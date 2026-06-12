---
title: "Mathematica 6.0.1 - Documantation center"
date: 2008-02-22
forum: Education &amp; Science
---

### Post by sotiriss on 2008-02-22
Hi. I have a problem with Mathematica 6.0.1. When i open the documetantation center,  i can't see any  graphics and plots 
For example, when i go to PLOT function in documentation center, the plots  of the examples don't appear. Only when i evaluate the cells there, i can see graphics and plots.
I have this problem only in documentation center and not in a notebook.
Sorry for my English.
Thanx.Sotiris

---

### Post by euler_fan on 2008-02-22
One workaround is to use Mathematica's online documentation. If memory serves it's mostly static content, but will let you see the outputs from the examples they use.

---

### Post by sotiriss on 2008-02-23
> **euler_fan said:**
> One workaround is to use Mathematica's online documentation. If memory serves it's mostly static content, but will let you see the outputs from the examples they use.

This is a solution that will help me. Online documentation is exactly like documentation center. Thanks

---

### Post by Geremia on 2011-03-02
> **euler_fan said:**
> One workaround is to use Mathematica's online documentation. If memory serves it's mostly static content, but will let you see the outputs from the examples they use.Has anybody found a better solution than this? Some people say using KDE solves the problem, but not for me (Maverick 10.10 64-bit on MacBook). Thanks

---

### Post by Geremia on 2011-03-03
I figured out the solution (you might need to sudo the mv and ln and change the details of the path in the mv command to suit your system):

```
cd /usr/local/Wolfram/Mathematica/6.0/SystemFiles/Java/Linux-x86-64/bin
mv ./java ./java.backup
ln -s /usr/bin/java ./java
```For when you get errors in Mathematica like:
> LinkObject::linkn: Argument \
LinkObject['/usr/local/Wolfram/Mathematica/6.0/SystemFiles/\[Ellipsis]\
      m.wolfram.jlink.Install -init "/tmp/m00000219781",10,4] in \
      LinkWrite[LinkObject['/usr/local/Wolfram/Mathematica/6.0/Syste\
      \[Ellipsis]am.jlink.Install -init       "/tmp/m00000219781",10,4],<<1>>] \
      has an invalid LinkObject number; the link may be closed.
      
      LinkObject::linkd: Unable to communicate with closed link \
LinkObject['/usr/local/Wolfram/Mathematica/6.0/SystemFiles/\[Ellipsis]\
      m.wolfram.jlink.Install -init "/tmp/m00000219781",10,4].
      
      PacletManager::fail: The PacletManager could not start. Certain \
      operations will not function correctly in this session unless the       \
      PacletManager can run. It will attempt to restart when needed,       unless \
      you set PacletManagerEnabled[] = False.
      
      LinkObject::linkn: Argument \
LinkObject['/usr/local/Wolfram/Mathematica/6.0/SystemFiles/\[Ellipsis]\
      m.wolfram.jlink.Install -init "/tmp/m00000319781",13,4] in \
      LinkWrite[LinkObject['/usr/local/Wolfram/Mathematica/6.0/Syste\
      \[Ellipsis]am.jlink.Install -init       "/tmp/m00000319781",13,4],<<1>>] \
      has an invalid LinkObject number; the link may be closed.

---

### Post by jeff788 on 2011-03-16
I know that this is an old thread, but it solved my longstanding problem with Mathematica since I updated java.  Thanks!

---

### Post by guyguyguy on 2011-04-15
Second the thanks. 
This was a very annoying problem for me - mathematica kept on complaining about everything since I upgraded java.
I had this problem for a while and couldn't find a solution anywhere.
Your solution works and makes sense :)

Thanks
Guy

---

