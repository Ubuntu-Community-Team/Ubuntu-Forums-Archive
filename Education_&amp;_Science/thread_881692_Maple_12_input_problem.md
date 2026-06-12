---
title: "Maple 12 input problem"
date: 2008-08-06
forum: Education &amp; Science
---

### Post by c03 on 2008-08-06
Hi, I did the export awkat workaround thingy to go from a blank window in Maple 12 to something that works, that's great, BUT.

If I open a window in maple, "Save as..", "Insert Spreadsheet" any of the tutors or what so ever, I can't input any text, numbers, etc. the worksheet anymore!

If I close maple, and restart it, it works fine again, but I can't input any text, numbers, etc. into anything after opening an internal java window in maple.

I can copy and pasty by clicking, but the keyboard does nothing!

Also, the CommandAutoComplete (Ctrl+space) doesn't work.


I really suspect java in this one =/

What can I do?
- Regards c03

---

### Post by manualfaderen on 2008-08-24
I just wanted to let everyone know that I have the same problem.

I'm running maple 12 on 8.04 on a lenovo T61

---

### Post by mali2297 on 2008-08-25
Do you use Sun Java or GCJ (GNU Java)?

---

### Post by HK1 on 2008-08-31
I am experiencing the same problem.
maple12 on hardy.
sun-java6-jre

---

### Post by baggins on 2008-09-09
> **mali2297 said:**
> Do you use Sun Java or GCJ (GNU Java)?

Maple ships with its own java, and it's broken!
Sun fixed the compiz problem :
[http://http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775]("http://http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775")
At least they have if the lines: 
> Release Fixed  :  6u1(b01)
State 	       : 10-Fix Delivered
Means what I think it does :)

So maybe maple will release a update that uses this fix.
Or maybe it's possible to force maple to use the "real" sun-java vm.

Other than that only "fix" seems to be disabling compiz (easy to do if you use [Compiz-Switch]("http://forlong.blogage.de/entries/pages/Compiz-Switch")). Only don't use the AWT_TOOLKIT fix if you disable compiz, or it still wont work.

-- Jon

---

### Post by baggins on 2008-09-09
> **baggins said:**
> Maple ships with its own java, and it's broken!
Sun fixed the compiz problem :

...

Or maybe it's possible to force maple to use the "real" sun-java vm.

Yep it's possible to edit the script that starts maple, so it will use what ever java you choose.
Looks like everything works fine too. Wonder why thy ship their own java?
Anyway the fix is:
[LIST=1]
[*]locate your maple script, location differs depending on where you installed.
[*]open in a editor, and locate the section that matches your hardware (for most that will be : bin.IBM_INTEL_LINUX
[*]In that section there is two lines starting with MAPLE_JRE_BIN and JRE_ROOT. They contain the folowing $MAPLE/jre.IBM_INTEL_LINUX/ swap this with the path to your jre of choice.
[/LIST]

In my "fixed" maple script I have the following.
In the top I set a variable :
[INDENT]export JRE_BASE='/usr/lib/jvm/java-6-sun/jre'
[/INDENT]

Further down in the file I comment the lines
[INDENT]MAPLE_JRE_BIN="$MAPLE/jre.IBM_INTEL_LINUX/bin/"
JRE_ROOT="$MAPLE/jre.IBM_INTEL_LINUX/lib"[/INDENT]
and add these
[INDENT]MAPLE_JRE_BIN="$JRE_BASE/bin/"
JRE_ROOT="$JRE_BASE/lib"[/INDENT]

-- Jon

---

### Post by cantinflasa on 2008-10-26
thank you very much, that was really useful, sorry if my english is not so good, it´s not my native language. That really worked for me, i&#7743; really thank.. i did just what you told me to do, and at moment everything is going good...

---

### Post by walki on 2008-11-30
Thanks, this solved my problem also. Note edit the

```
MAPLE_JRE_BIN="$MAPLE/jre.X86_64_LINUX/bin/"
JRE_ROOT="$MAPLE/jre.X86_64_LINUX/lib"
```

lines if using the 64 bit version!

---

### Post by c03 on 2008-12-10
Thank you very much, this solved the problem! =)

---

### Post by c03 on 2008-12-10
I still can't use Auto-completion though. Ctrl+space does nothing =/

---

### Post by GjesBolan on 2009-02-14
Thank you  very  much to all of you, this solves my problem!
:) :) :)

Good luck to all

---

### Post by FranzZdyb on 2009-02-23
Thank you so much...!

How do you people achieve such a level of expertise?

---

### Post by gian666 on 2010-08-04
with maple 12, on ubuntu 10.04 64 bit, it seems that the java workaround above (thank you, btw !) does not work using sun java, but DOES work if the "default java" package is installed and used (i.e. /usr/lib/jvm/java-1.6.0-openjdk/jre/).

---

