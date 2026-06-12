---
title: "Crontab Trouble"
date: 2009-04-22
forum: General Help
---

### Post by Tobywuk on 2009-04-22
Hello,

I am having trouble getting cron to run a command. I want to set a cron command so that transmission loads up at a set time of the day, eg 1am at night.

I ran:
```
crontab -e
```

from here I entered the line:
```
 22 * * * * /usr/bin/transmission start
```
Once the 22nd minuit comes around nothing happens and transmission does not start. Im using the 22nd minuite to test if it works, once it does I will just change it to 1 1 * * * /commandhere to start it at 1am.

Any idea's why this is not working? thanks. :)

---

### Post by codeseer on 2009-04-22
Could be that there's a space between the application path and the parameter. Might have to put it in a bash script. I'm not sure if you're supposed to put quotes or anything around it.

Edit:

I think also, when you change it, you're supposed to put it as '01 01' instead of '1 1'.

---

### Post by Tobywuk on 2009-04-22
I just tried "" quotes around the command and no luck. I'm currently testing it out on a minute ahead of time so its double characters anyway (last one was 12 * * * * "/commandhere")

---

### Post by Tobywuk on 2009-04-22
took me ages to find the answer but its now working

```
01 02 * * * DISPLAY=:0 /usr/bin/transmission
```

---

### Post by LexLuthor08 on 2009-04-28
crontab is not working for me either. 

all I wanna do is run a script in a folder every 30minutes (the script works when I run it manually).

this is the line: 

*/30 * * * * myusername /home/myusername/script


when I browse the forum I just notice that barely anyone gets crontab to work and all the "experts" say different contradicting things.

also when I run sudo crontab -e , I get a completely different file than crontab -e.

---

### Post by Tobywuk on 2009-04-28
do crontab -e

then 

```
*/30 * * * * /home/myusername/script
``` 


I dont think you need the username. when you do a crontab -e you are editing your users crontab not the global system one.

Edit: 
my mistake - if you want it every 30 mins then you will need */30 as   just 30 will do it every hour.

---

### Post by LexLuthor08 on 2009-04-28
I found a solution for me:

install the package gnome-schedule

-> adds scheduled tasks under menu, system tools. user-friendly, graphic interface.

works like a charm.

---

### Post by su-bzero on 2011-01-19
> **LexLuthor08 said:**
> I found a solution for me:

install the package gnome-schedule

-> adds scheduled tasks under menu, system tools. user-friendly, graphic interface.

works like a charm.

O, nice. Thank you. I will try it too.

By the way, only DISPLAY=:0 doesn't work for me.

Now I use in crontab something like that:
```
*/15 * * * * username export DISPLAY=':0' && xhost local:username && notify-send -i  /usr/share/icons/oxygen/32x32/status/security-medium.png "I am living!"
```

---

### Post by Cheesehead on 2011-01-19
Several problems with this one:
```
*/15 * * * * username export DISPLAY=':0' && xhost local:username && notify-send -i  /usr/share/icons/oxygen/32x32/status/security-medium.png "I am living!"
```
1) Do you really want to run it from the root crontab? It works quite well as a user-level crontab.
2) DISPLAY=':0' is improperly formatted
3) 'export' is superfluous since you're not referring to another script
4) "&& xhost local:username && " seems superfluous, since you already defined the username...which is itself superfluous - see #1.
5) use single-quotes (') instead of double-quotes (") for the text string. 

So a version that works in a user-level crontab would be:
```
*/15 * * * * DISPLAY=:0.0 notify-send -i /usr/share/icons/oxygen/32x32/status/security-medium.png 'I am living!'
```

---

### Post by su-bzero on 2011-01-20
Thank you for correnction, Cheesehead. Now for me is all clean about invoking X program over crond.

---

