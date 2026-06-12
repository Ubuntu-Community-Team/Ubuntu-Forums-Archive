---
title: "Calendar start of week incorrect"
date: 2005-10-18
forum: Desktop Environments
---

### Post by wolovids on 2005-10-18
I upgraded from Hoary to Breezy via an apt-get dist-upgrade.  It now appears that my Calendar week starts on Monday instead of Sunday (I live in the USA).  The strange thing is that there is a setting in Evolution to select the day that starts off the week.  The calendar in Evolution is correct, but the calendar that gets displayed in the panel (in the clock applet) is incorrect.  The calendar displayed adjusting the Date/Time settings is also incorrect but it doesn't have an option to change the start day.  I assumed that the setting in Evolution would carry over to the panel applet but that doesn't seem to be true.  I do have the correct language selected in the "Language Selector" application.  Is there anything else that I can try to fix this issue?  

Thanks for your help.

---

### Post by yage on 2005-10-18
I would think this follows the language selection... so if you change your selection to english-us and restart gnome, what happens?

---

### Post by dave9191 on 2005-10-18
Hmm, I'd like to know this too. But my cal starts on Sunday and I want it to start on Monday. 

Thanks 

Dave

---

### Post by michael_salcher on 2005-10-18
one should be able to change the start of the week disregarding the language or country you live in. i live in australia, but my week starts on monday.

if no one knows how to change this, a bug report should probably be filed. and if there is some config file setting that does change this, a bug report should still be filed requesting a gui way (and I'm not talking about the gconf gui) of changing this)

---

### Post by stoffe on 2005-10-18
I've set Sweden as my location, but use US English for language, and my weeks start with monday, which is correct.

I agree that this should be an easy choice instead though, I think that some other install my week started on sunday for no apparent reason.

The clock preferences is where I would look for such a setting.

---

### Post by iimess on 2005-10-20
[QUOTE=yage]I would think this follows the language selection... so if you change your selection to english-us and restart gnome, what happens?[/QUOTE]
sorry to bump this but...

My clock's start-of-week in hoary was correct (in en-US). After a distro upgrade it now starts on Monday even I set the language explicitly to English (American)

---

### Post by PhilOSparta on 2005-11-04
It appears that a bug has been submitted for this problem.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=16168](http://bugzilla.ubuntu.com/show_bug.cgi?id=16168)

Actually, I think it tells you how to fix it locally, but it's really confusing in its use of character codes like 
2158-abday       "<U0073><U00F8><U006E>";"<U006D><U0061><U006E>";/

These don't mean a lot to the casual user.
Any additional info on this would be helpful.

Actually, I added 
first_weekday 7
first_workday 7

just after the LC_TIME-flag in the locales. Then run

locale-gen and reboot.
It worked for me.

---

