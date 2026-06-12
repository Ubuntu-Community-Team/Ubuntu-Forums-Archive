---
title: "My desktop clock is 14 hours fast, and I can't change it!"
date: 2005-04-16
forum: Desktop Environments
---

### Post by muzza on 2005-04-16
It is now 11:20pm, Saturday the 16th April on the east coast of Australia, but my desktop tells me it's 1:20pm tomorrow.

I opened 'adjust date and time' and all the settings there are already correct, including timezone.

I also noticed that there is an option to synchronize with an internet server, but when I click on it, I get a message that "NTP support is not running"

Any suggestions?

*EDIT:* 

I just noticed that I had the wrong date highlighted, Which I corrected.  So my clock is actually 10 hours slow, which would be Greenwich Mean Time (GMT)  But I'm in Australian Eastern Standard Time (AEST)

---

### Post by kassetra on 2005-04-16
[QUOTE=muzza]II just noticed that I had the wrong date highlighted, Which I corrected. So my clock is actually 10 hours slow, which would be Greenwich Mean Time (GMT) But I'm in Australian Eastern Standard Time (AEST)[/QUOTE]

Question for you - what time zone does it say you're in?

---

### Post by soul_rebel on 2005-04-16
you have to choose if you want the hardware clock to utc (better for linux) or to local time (better for win). This could be the problem

anyway try
```
sudo /etc/init.d/ntpdate start
```

---

### Post by muzza on 2005-04-17
[QUOTE=kassetra]Question for you - what time zone does it say you're in?[/QUOTE]

Brisbane, Australia.  Which is correct.

Soul_rebel, I typed what you suggested and nothing seems to have changed.  Still won't let me sync with a server.  Why is it better to have UTC (GMT?)  I want to know what the time is here, not in London.

*EDIT:*   Hey, hey.  Sorted!  I went into preferences this time (hey, I'm new here!) and found that UTC was ticked.  Unticked said box and now we're cookin'.

Still won't let me sync with a server tho' -  tells me NTP support is not running.

---

### Post by soul_rebel on 2005-04-17
unix likes to have the HARDWARE clock set to utc, than knowing where you are it sets SYSTEM clock to the right time, so you will see the right time.

use 
```
sudo base-config
```
to configure this behavior.

About ntp not working could you post the output of the command i gave you?

---

### Post by muzza on 2005-04-18
I tried typing that command again and this is what it said.

------------------------------------------------------------------------------------------------------------------
muzza@ubuntu:~ $ sudo /etc/init.d/ntpdate start
 * Synchronizing clock to ntp.ubuntulinux.org...                         [ ok ]
--------------------------------------------------------------------------------------------------------------------

Still won't let me sync.

---

### Post by TravisNewman on 2005-04-18
it IS syncing. if it wasn't, it wouldn't say [ok]

but other than that-- very strange. are you dual booting with Windows? If Ubuntu thinks the system clock is set to UTC and Windows thinks its set to local time, it's going to cause weird problems like that, but the sync should fix it.

---

### Post by soul_rebel on 2005-04-18
i'll say it again

```
sudo base-config
```
set to utc if you don't use windows, local if you do.

then please check using

```
date
```

instead of gnome clock.

---

### Post by sonyacarlson on 2005-11-30
My desktop clock is 6 hours slow and I can't change it.  When I go to adjust the time, the calendar opens up, but nothing else happens.

Where would I type the code that has been suggested?
Thanks for any advice
Sonya

---

### Post by varunus on 2005-12-02
Right click on the taskbar clock and choose "Adjust Date and Time."  Also, choose preferences from the same menu and make sure "Use UTC" is not checked.  (If it is, the clock will show you GMT instead of your time zone.)

---

### Post by lindejos on 2006-01-11
RE:
you have to choose if you want the hardware clock to utc (better for linux) or to local time (better for win). This could be the problem

anyway try
Code:

sudo /etc/init.d/ntpdate start

Hey, I just wanted to say thanks to Soul_Rebel.  I was having trouble updating my clock and this worked perfect for me.

---

