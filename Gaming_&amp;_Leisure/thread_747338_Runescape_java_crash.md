---
title: "Runescape java crash"
date: 2008-04-06
forum: Gaming &amp; Leisure
---

### Post by The Number Pi on 2008-04-06
Ok, I have looked all over to find a solution on the website, but I have not found any solution to my problem. I had runescape working for one morning, and then it quit working in the afternoon. I have sun java 6, and I can load runescape fine, but once I try to log in, Mozilla is shutdown immediately. I run runescape on the sun java loader, which works, but getting to play crashes mozilla. Can anyone help me?

---

### Post by twig43 on 2008-04-09
i have that same problem but i could pnly run runescape once then it started crashing

---

### Post by Crafty Kisses on 2008-04-09
Have you tried running Runescape on a different browser?

---

### Post by twig43 on 2008-04-10
i have tried to run it on firefox using sun java and i get the same error or if i use a different run option it wont run at all  
it worked once on epiphany

---

### Post by The Number Pi on 2008-04-13
> **Codename said:**
> Have you tried running Runescape on a different browser?

I have not, but I think I will try running it through IE7 in WINE and see if that works, it should.

---

### Post by bucknasty on 2008-04-14
I am having the same crash after the login screen

---

### Post by akurashy on 2008-04-15
You should know that:

If you are using firefox 2.0.x.x you should be aware that the new java plugin available in java 1.6.0 + have worked with firefox to bring a solid one. the draw back is that you can't use it in FF2

At the moment, I logged into runescape with (java 1.6.0 b5 and FF3 beta 5 (check backports i think jdong ported it already) and played for an hour or so , sound worked great and it didn't crash.

ALSO. while i said all this,  disable all plugins and extensions and try playing again (GO SAFEMODE) 
type in your terminal $ firefox -safe-mode

to check your plugin version go to about:plugins

---

### Post by The Number Pi on 2008-04-16
Ok, I put firefox in safemode, and I tried installing jre 6. I checked terminal, and this is what it posted:

GCJ PLUGIN: thread 0x805e520: NP_Initialize return
GCJ PLUGIN: thread 0x805e520: NP_GetValue
GCJ PLUGIN: thread 0x805e520: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e520: NP_GetValue return
Failed to create Java VM
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb781b48b, pid=20745, tid=2975333264
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_13-b05 mixed mode, sharing)
# Problematic frame:
# V  [libjvm.so+0x1d248b]
#
# An error report file with more information is saved as hs_err_pid20745.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
INTERNAL ERROR on Browser End: Pipe closed during read? State may be corrupt
System error?:: Success
Segmentation fault (core dumped)

I'm not sure what to do next.

---

### Post by akurashy on 2008-04-17
Let me get this straight, you are trying to install java runetime 1.6.0?
what version of firefox do you have?

---

### Post by The Number Pi on 2008-04-17
No, sorry, I tried switching to sun java 5, and then back to sun java six. I have j2re 1.4, and I am running firefox 2.0.0.13. Maybe I can try the ffx3 beta, that might work.

---

### Post by akurashy on 2008-04-17
good luck on updating, you might some help updating those two programs (specially jre)

---

### Post by m14213 on 2011-01-15
Ok so I got it working perfectly on Prism, Google Email version, I recommend everyone to try this, please respond, I want to know if I was the only one who got it working:)

---

