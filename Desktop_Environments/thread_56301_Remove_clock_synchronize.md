---
title: "Remove clock synchronize?"
date: 2005-08-12
forum: Desktop Environments
---

### Post by carpediem on 2005-08-12
Is there any way to remove or change the way the clock is synchronized during start up? I run a dual-boot system, and when it synchs to ntp.ubuntulinux.org and I boot into windows, the clock is off by a few hours. Quite annoying!

---

### Post by heimo on 2005-08-12
You probably have wrong timezone. I don't know how you change that in KDE, but it should be quite easy task. Or you can run (in terminal) sudo tzconfig

If that's not an option, you can disable time syncronization with something like:
 ```
sudo chmod a-x /etc/init.d/ntpd

``` 
I'm not 100% sure about that ntpd. If it exists, it's correct. :)

EDIT: As shown below, correct script name is ntpdate

---

### Post by carpediem on 2005-08-12
The time zone is correct, I think that it was just synchronizing to a UTC time. In windows, I don't have a time synchronizer installed but it is set to GMT-5 since I'm in the EST.

I did check out what was in /etc/init.d and there was one called ntpdate running. I used that chmod a-x on it and after rebooting to see if it still synchronized, it's still there. I didn't notice it try to synchronize to ntp.ubuntulinux.org this time though, but maybe it's because I just woke up and didn't see it go by... :P

---

### Post by void_false on 2005-08-12
I have same problem. Updating time according to NTP is ok. I think problem occurs during shutdown when you see message err.. dont remember exactly, something like Saving Hardware Clock...
Dunno how to disable it. I dont want system to touch BIOS in any way. ;)

---

### Post by heimo on 2005-08-12
I think these are responsible for that:
/etc/init.d/hwclock.sh
/etc/init.d/hwclockfirst.sh

I wouldn't disable those, but if that's what you want, chmod a-x will remove execution permissions.

---

### Post by carpediem on 2005-08-12
Okay, I've gotten it straightened out now! I went into windows to set my time right, rebooted to linux to see if it would synchronize, it didn't, rebooted to windows to make sure and it was still set to the same time minus a few minutes of booting time.

On shutdown, I didn't see an error, void. I know what you mean about you not wanting anything to touch your BIOS! run the command ```
ls /etc/init.d
``` and see if anything with ntp is in there. I had ntpdate. Then I ran  ```
sudo chmod a-x /etc/init.d/ntpdate
```

That fixed it for me, try and get that error message so we can see.

---

### Post by Gezzer on 2005-08-12
[QUOTE=carpediem]Okay, I've gotten it straightened out now! I went into windows to set my time right, rebooted to linux to see if it would synchronize, it didn't, rebooted to windows to make sure and it was still set to the same time minus a few minutes of booting time.

On shutdown, I didn't see an error, void. I know what you mean about you not wanting anything to touch your BIOS! run the command ```
ls /etc/init.d
``` and see if anything with ntp is in there. I had ntpdate. Then I ran  ```
sudo chmod a-x /etc/init.d/ntpdate
```

That fixed it for me, try and get that error message so we can see.[/QUOTE]
 there are to files installed
ntp
ntpdate
removing these files will disable the network time update at boot ...

---

### Post by raven on 2005-08-12
[QUOTE=carpediem]Is there any way to remove or change the way the clock is synchronized during start up? I run a dual-boot system, and when it synchs to ntp.ubuntulinux.org and I boot into windows, the clock is off by a few hours. Quite annoying![/QUOTE]

It is not your time zone nor the sync, ubuntu uses UTC while window uses
the local time from the hardware
solution from firetech on this thread
[http://www.ubuntuforums.org/showthread.php?t=54003](http://www.ubuntuforums.org/showthread.php?t=54003)

[QUOTE=Firetech]The file is /etc/default/rcS, and the syntax is yes/no rather than true/false.
There is no need to reboot after changing the value, it will be done when you exit linux the next time.

Linux's software clock is completely independent of the hardware clock, it just uses it to get the time on boot, and set the time to it on shutdown (to save it). If the variable UTC is yes then, it will add/subtract  from the time to make it UTC time, if the variable is no, it will save the clock as is.
Windows on the other hand, takes the time directly from the hardware clock at all times (AFAIK). If the UTC value in linux is yes then, this will screw the clock up (get it out of sync).[/QUOTE]

---

### Post by carpediem on 2005-08-13
ah sweet, thanks for that man. I'll see if I can get it to be not UTC then!

---

### Post by void_false on 2005-08-13
Helped. Thanks. :)

---

### Post by altorus on 2005-08-14
For future forum searchers:

I beleive that:
sudo update-rc.d -f ntpdate remove

should do the trick

Playing with chmods is really the arse-about-face way of doing things.

---

### Post by GoA on 2005-08-14
I have a problem that my motherboards battery is weak so the time is going too fast on windows and linux. In windows I set the update top happen every 10 minutes through registry, so how can I do the same thing in linux?

---

