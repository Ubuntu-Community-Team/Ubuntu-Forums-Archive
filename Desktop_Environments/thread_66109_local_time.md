---
title: "local time"
date: 2005-09-16
forum: Desktop Environments
---

### Post by myha on 2005-09-16
Hi all!

Could someone please tell me howto set my system clock to be local? Because every time I boot system it changes my system clock to +2 hours because im using GMT. 
How to disable this?

thanks,
Miha

---

### Post by goldrush on 2005-09-16
Hi
I am also a newbie, so this may not be the "correct" way

(step1 should have been correctly set when
 installed)
1. Select
System
Admin
Time & Date
Select Time Zone
Check correct zone and time shown on "calender".. 

If time on both "calender" and clock icon (top right of screen) are correct, then step 3 is not required

2. Then Select Servers
DESELECT ubuntu server and select a server local to you
(This also stops Ubuntu attemting to sync time on boot up which can cause delays if on dial up)
Select periodically sync


3. Right click on clock time display (top right of screen)

Select Preferences
Deselect UTC (if you wish to display GMT)

I may be wrong but Ubuntu does not appear to cater for changes in Daylight saving  times

---

### Post by myha on 2005-09-16
Hi!

Thanks for your answer.. I know how to do that, but I dont want to select time zone and everything... I want to have time set without GMT... Local time... I can change time so it is correct, but when I reboot it changes back...  :???:  And thats what I want to change...

---

### Post by lao_V on 2005-09-16
Have you tried running 'tzconfig' and setting your local time zone?

---

### Post by myha on 2005-09-16
[QUOTE=lao_V]Have you tried running 'tzconfig' and setting your local time zone?[/QUOTE]
:) Well thank you very much, thats just what I needed... 

Maybe u can tell me also how to change tty console keyboard layout... ?

Thank you,
Miha

---

### Post by lao_V on 2005-09-16
[QUOTE=myha]:) Well thank you very much, thats just what I needed... 

Maybe u can tell me also how to change tty console keyboard layout... ?

Thank you,
Miha[/QUOTE]

Now you're really pushing it :-)

I haven't played around with keyboard confs too much but have a look in xorg.conf under "Input Devices" -> "XKBlayout" or I'm not sure if this is the right command but try
 ```
dpkg-reconfigure xkblayout
```

---

### Post by myha on 2005-09-16
Well u are wright, I have us layout in xorg.conf....
So I guess I just have to replace us with my language....
Do you maybe also know where to find layout codes for difrent countries?

Thank you very much,
miha

---

### Post by lao_V on 2005-09-16
You should be able to set it from one of the dpkg-reconfigure options (try dpkg-reconfigure xkb), I just can't remember which one it is at the moment. 

I can't find the codes at the moment. Which language are you trying to set it to?

---

### Post by lao_V on 2005-09-16
Or  ```
dpkg-reconfigure locales
```

---

