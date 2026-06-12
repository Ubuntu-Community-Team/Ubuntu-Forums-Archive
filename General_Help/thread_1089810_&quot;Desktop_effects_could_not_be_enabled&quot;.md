---
title: "&quot;Desktop effects could not be enabled&quot;"
date: 2009-03-07
forum: General Help
---

### Post by Kyle5 on 2009-03-07
I need help with this, I recently had Ubuntu and XP then decided to do a restore. Everything worked before I did the restore what could be wrong now?
I go to make a desktop effect and it says not enabled.
Driver Intel 845G I believe. 
Also this is Terminal of compiz

kyle@kyle-desktop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 

Thanks in advance

---

### Post by Kyle5 on 2009-03-07
Been stuck on this for 4 hours...

---

### Post by Svensk023 on 2009-03-07
So just so my perspective is correct.
You have your latest driver installed?
You have compiz and its manager installed?

---

### Post by Kyle5 on 2009-03-07
Yeah, I have the latest driver updates, and compiz manager. Might know why it's doing this.. I go to System>Administration>Hardware Drivers and it says loading 0%... Then loads up and says "No proprietary drivers are in this system".
Any ideas?

---

### Post by Svensk023 on 2009-03-07
ok, well to run all the extra effects you do need a proprietary driver, and it seems that you don't have one. search google for a recent driver that goes to your graphics card and download it.
then in terminal type

```
sudo sh 
```
then drag the .sh file that you have extracted from the driver download and hit enter.
restart your computer, and then try to enable extra effects.

---

### Post by Kyle5 on 2009-03-07
Ok thanks so much I got to go but I'll be back to say if it worked.

---

### Post by Svensk023 on 2009-03-07
alrighty.
if u need to contact my by e-mail dont hesitate. my ICQ and e-mail are both listed in my profile.

---

### Post by RiceMonster on 2009-03-07
As far as I know, there are no proprietary drivers for Intel; they're all open source, so you shouldn't have to go searching google for a driver. What version of Ubuntu are you using? I have an Intel 965 card, and on an older version of Ubuntu I could not use compiz because my card was blacklisted, due to compiz being very buggy with the Intel driver. This appears to be the case for you as well, as stated in the error message.

---

### Post by dtom2444 on 2009-03-07
Yea, i've been having the same problem for about a week on my Sony Vaio. I started a thread and got a possible solution. It didn't work for me, but i hope it will help you. Go to this site:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

and follow the directions. It didn't work for me because of my graphics card being an integrated card.

---

### Post by zika on 2009-03-07
> **Kyle5 said:**
> I need help with this, I recently had Ubuntu and XP then decided to do a restore. Everything worked before I did the restore what could be wrong now?
I go to make a desktop effect and it says not enabled.
Driver Intel 845G I believe. 
Also this is Terminal of compiz

kyle@kyle-desktop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 

Thanks in advance
[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)
[http://ubuntuforums.org/showthread.php?t=962520](http://ubuntuforums.org/showthread.php?t=962520)
[http://ubuntuforums.org/showthread.php?t=981644](http://ubuntuforums.org/showthread.php?t=981644)
sorry ...

---

