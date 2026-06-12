---
title: "Kaffeine is crazy (even after the .deb fix  install for buggy Kaffeine)"
date: 2005-05-20
forum: Desktop Environments
---

### Post by bdmp on 2005-05-20
I was using kaffeine with no problems.  I happend apon a faq that had a fix for a buggy kaffeine that was in the install. I thought it couldn't hurt so I installed it. After that there were no problems, but then one day (after the time that I installed Realplayer.  Might be related. So now, If I click on a video or audio file I get the error:
"Sorry-Konqueror: KDEInit can not launch '/media/sda1/blahblah.avi' "   

So then I right click on it and open it with Kaffeine and up pops a dialog that says,"Kaffeine Player: 1/1" it just sits there and teh bouncing icon bounces and the applet shows up in the tool bar and then it does nothing till I try to close it and it a dialog pops up and it says "kaffeine not responding........"

What can I do to fix this?  -thanks in advance

---

### Post by bdmp on 2005-05-22
Doing apt-get remove kaffeine --purge did the trick.

---

