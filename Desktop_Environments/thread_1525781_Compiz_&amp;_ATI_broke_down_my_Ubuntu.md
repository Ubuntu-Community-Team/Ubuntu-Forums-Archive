---
title: "Compiz &amp; ATI broke down my Ubuntu"
date: 2010-07-07
forum: Desktop Environments
---

### Post by San-Tiago on 2010-07-07
Hi, I'm new here and in Linux. I'd got Ubuntu for two days, and then I tried to check Compiz. After that operation my Ubuntu doesn't work. I've got a black "x" instead of normal arrow pointer, I can't open Menu. I've read problem may by caused by incompatibility with ATI graphic card. I've got a Toshiba notebook with ATI Mobility Radeon, and Ubuntu is installed nest to Vista. Please help me.

Best regards,
Jim

---

### Post by kemra on 2010-07-07
I know you might not be able to do this now but did you go to System>Administration>Hardware Drivers to get the latest ATI propriatry driver?

I have a differnt ATI card on my dekstop but it works fine even with Compiz.

---

### Post by San-Tiago on 2010-07-07
I think I have the latest drivers. Somewhere I've read that using this commands might be helpful:
```
nano /etc/X11/xorg.conf
``` and then change "fglvx" to "ati", but in my case there is nothing like this to change, to be honest, there is nothing. 

Like I wrote, I'm new in Linux and the last and only thing I've changed was settings of compiz. After that I'm not able to use my Ubuntu. What else it could be if not Compiz?

---

### Post by Keith_K on 2010-07-07
try right clicking on your desktop and choose change desktop background. click on the visual effects tab and set it to normal or extra

---

### Post by San-Tiago on 2010-07-07
But I can't make a right click. I haven't got normal arrow pointer, I've got a black "X".

---

### Post by Keith_K on 2010-07-07
try this .. in the command line, type 
```
killall compiz.real && metacity --replace
```

and see if that gets you back to a mouse

---

### Post by San-Tiago on 2010-07-07
Unfortunately, this command doesn't work. It answered: "not such process".
When I typed only 'metacity -- replace' it answered: 'Window manager error: unable to open X display". After typing 'compiz' - 
"launching fallback window manager
xterm xt error - can't open display
xterm DISPLAY is not set"

Thanks for answers.

Jim

---

### Post by Keith_K on 2010-07-07
it confirmed that compiz isn't running but it should start metacity except apparently xserver is having a problem. 
you might want to look at your /var/logs/Sorg.0 log and see if there is anything there that says its not starting. (I kinda doubt you will) 
then try 
```
metacity --display=:0.0 --replace
```

The correct --display= value can be determined by issuing the 'who' command and noting the values in parenthesis at line-end.

---

