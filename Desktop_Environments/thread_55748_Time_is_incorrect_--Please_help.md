---
title: "Time is incorrect --Please help"
date: 2005-08-10
forum: Desktop Environments
---

### Post by donk on 2005-08-10
I am running Kubuntu and when I went through the install I made the mistake of setting the time to UTC.  

I am trying to change the time to local time (BST).  I have tried date -s 'correct time/date' and this changes it temporarily until the next reboot when it goes back to UTC.  How does K/Ubuntu handle time changes, is there a timeconfig (can't find it) or some other command?  I think something strange may be happening as I can't always get in and "Adjust Date and Time..." (bottom right hand corner of screen & right hand mouse click).

Can someone help, I just want the correct time, however it always one hour behind! Or do I have to reinstall?

Cheers

Donk

---

### Post by heimo on 2005-08-10
[QUOTE=donk]
Can someone help, I just want the correct time, however it always one hour behind! Or do I have to reinstall?[/QUOTE]

At least theres tzconfig (on terminal/command line) that sets local timezone. I don't know how it works, but it's called without parameters, so try:
 ```
sudo tzconfig

```

---

### Post by jeremy on 2005-08-10
You can change it in Control Centre -> System Administration -> Date & Time, click 'Administrator Mode'.

---

### Post by nocturn on 2005-08-10
I think I know what is happening.

You should set your correct timezone (like posted before).  Your changes do not stay over reboot because Ubuntu automaticly synchronizes to an NTP server, which resets the internal clock (always in UTC).

---

### Post by donk on 2005-08-10
OK I tried the command tzconfig and was able to change the time, etc:

Your default time zone is set to 'Europe/London'.
Local time is now:      Wed Aug 10 12:26:16 BST 2005.
Universal Time is now:  Wed Aug 10 11:26:16 UTC 2005.

However, when I tried to change the clock it won't accept the sudo password and so seems to display the univeral time.  When I look at the clock (not in administrator mode) then it is correct, ie 12:26:16 BST - I think something is corrupted in KDE?

Do you have any other ideas?  Thanks for all your help in the meantime.

Donk

---

### Post by donk on 2005-08-10
I think I have solved my problem, but I don't know why.  I just changed the clock from 'plain' to 'digital' and back again and then bingo the time displays BST.  However, I still cannot edit the time by going into administrator mode.  However, I can live with it, because it at least displays the correct time and my calendar in Kontact also now displays the correct time.

Thank you all for your help, it is much appreciated.

Donk :-)

---

