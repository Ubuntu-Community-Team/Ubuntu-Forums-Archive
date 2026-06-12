---
title: "Runescape (bad java method errors)"
date: 2005-12-26
forum: Gaming &amp; Leisure
---

### Post by Smaskens on 2005-12-26
I have been trying to play Runescape with Firefox + Java ([www.runescape.com)](www.runescape.com)). However Firefox quits randomly (when all memory is used) and following errors are printed:

```

:~/.mozilla/plugins$ firefox

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************

**************** SERVER ERROR **************
CSecureJNI2_CallMethod: Bad java method
**************** ************ **************

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************
Out of memory while attempting to throw JSException
Out of memory while attempting to throw JSException

**************** SERVER ERROR **************
SecureCallStaticMethod: bad method
**************** ************ **************
Segmentation fault


```

---

### Post by Smaskens on 2005-12-29
I updated Java and made the new link to the plugins directory, but still firefox crashes. Darn, this drives me crazy ](*,)

---

### Post by minisori on 2006-01-01
u have to add the option to java -mx256x so it would not crash in sun java 1.5 or sun java 1.4.2.

---

### Post by Smaskens on 2006-01-02
[QUOTE=minisori]u have to add the option to java -mx256x so it would not crash in sun java 1.5 or sun java 1.4.2.[/QUOTE]

Where I should add it?  Command prompt just informs me about invalid heap size :rolleyes: 

```

x@x:/usr/share$ java -mx256x
Invalid maximum heap size: -Xmx256x
Could not create the Java virtual machine.
x@x:/usr/share$

```

---

### Post by ysse on 2006-01-02
You would use the Java Plugin Control Panel (System/Settings/Java Plugin Control Panel), the "Advanced" tab, Java Run Time parameters.

And it's -Xmx256M for 256 Mb maximum heap size, not 256x.

Good Luck

---

### Post by minisori on 2006-01-02
Oopss right misspelled it ](*,) but i think its -mx256m.

Nvm both parameters work.

---

### Post by Mustard on 2006-01-03
Just as an aside.

This won't help you with your Firefox problem, but Runescape runs very well in epiphany-browser.  I had someone on my computer trying to get it working in firefox for quite a while.  I eventually suggested they try it in epiphany-browser and it worked very well.  Firefox and java don't seem to like each other too much.  I find Firefox will often start using 100% of the cpu when some type of java thing exists on the webpage.

Epiphany-browser is able to be installed via synaptic or apt-get.

---

### Post by Smaskens on 2006-01-03
[QUOTE=ysse]You would use the Java Plugin Control Panel (System/Settings/Java Plugin Control Panel), the "Advanced" tab, Java Run Time parameters.

And it's -Xmx256M for 256 Mb maximum heap size, not 256x.

Good Luck[/QUOTE]

I dont have such Java Plugin Control Panel at the menu but that control panel was at following location:

```

x@x:/usr/java/jre1.5.0_06/bin$ ls -la
-rwxr-xr-x  1 root root   4153 2005-11-10 23:47 ControlPanel

```

Then I selected Java tab, "Java Applet Runtime Settings" and added to the "Java Runtime Parameters" a value "-Xmx256x".

Now Runescape seems to work without problems. 

And thanks for the hint, maybe I'll try Epiphany. However so far Firefox has been good enough for me.

---

### Post by Crazywhiteboy_760 on 2006-06-04
i want to be able to play runescape yet after i clixk what world i play in then it says that i need a plugin - java runtime environment. when i try to install this plugin it says its not availible...  i was ganna try to use Epiphany-browser but i dont know how to use synaptic to install it or apt-get  ... im a beginer at linux so i dont know how to really do anything if someone could help me i would greatly appreciate it

---

### Post by Qstosh on 2006-07-24
i have the same problem

---

### Post by involutaryhaxor on 2006-08-12
when i do manage to get my jre working (such a pain) it always works out of the box so to speak

---

### Post by DougZ on 2006-08-18
Interesting the comment about Firefox and Java not liking each other.

I have experienced the CPU spiking to 100% when Java loads under both Windows and Linux versions of Firefox. Really drives me nuts.

---

### Post by DougZ on 2006-08-18
Oh and I am experiencing the same issue with Runescape right now (I think). It loads fine, I can login, and when I click the large button (click to continue) Firefox just "goes away". Grrrr.

---

### Post by Toxicity999 on 2006-08-24
Linux Is Alergic to crappy games... No okay I'll be fair... For me as well Firefox doesn't too much enjoy any Java usage... (I have a few friends that insist on geocitying up their myspaces, and NO I don't use myspace they just make me look at their 'page' for some reason.)

---

### Post by madking on 2007-08-18
open up terminle, konsole, or what ever console you use and type:
"sudo apt-get install Epiphany-browser"
:KS

---

### Post by r3ymysterio9 on 2007-09-28
too complicated for me, i give up :\

---

### Post by r3ymysterio9 on 2007-09-28
too complicated for me, i give up \\:D/

---

### Post by pboxinator on 2009-04-29
try

sudo apt-get epiphany-browser

it should work this time but i havnt tried

---

