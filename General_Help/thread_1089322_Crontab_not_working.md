---
title: "Crontab not working?"
date: 2009-03-07
forum: General Help
---

### Post by n3gative12 on 2009-03-07
I am trying to set up a crontab to change my desktop wallpaper every 10 minutes. The crontab is set up like this:
```
@reboot /bin/chwp.sh 
*/10 * * * * /bin/chwp.sh
```
where /bin/chwp.sh is a file that changes the wallpaper
The wallpaper changes right on startup, but the part to change it every 10 minutes doesn't work at all. Can anybody help me out with this?

---

### Post by cmnorton on 2009-03-07
Your crontab line is broken. I believe -- at least on Red Hat -- you cannot have even a line continuation character followed by the rest of the line. My command lines looked so badly, I wrote a shell script to execute containing a nicely formatted line with line continuation characters.

Also, I've never seen the @ character used. What is it?

Finally, check your logs, syslog and messages (/var/log).

---

### Post by |Porsche on 2009-03-07
> **n3gative12 said:**
> I am trying to set up a crontab to change my desktop wallpaper overy 10 minutes. The crontab is set up like this:
```
@reboot /bin/chwp.sh 
*/10 * * * * /bin/chwp.sh
```
where /bin/chwp.sh is a file that changes the wallpaper
The wallpaper changes right on startup, but the part to change it every 10 minutes doesn't work at all. Can anybody help me out with this?

The first * is for minutes. Your line should look like
```
10 * * * * /bin/chwp.sh
```
Notice that you have a "/" before the 10, and the 10 is in the hours field.

More info can be found [here.]("http://www.adminschoice.com/docs/crontab.htm")

---

### Post by n3gative12 on 2009-03-07
> **|Porsche said:**
> The first * is for minutes. Your line should look like
```
10 * * * * /bin/chwp.sh
```
Notice that you have a "/" before the 10, and the 10 is in the hours field.

More info can be found [here.]("http://www.adminschoice.com/docs/crontab.htm")

I thought the */10 in the minutes spot meant it would run every 10 minutes... Either way, I also tried it with 10,20,30,40,50 in the minutes spot and that didn't work.
> **cmnorton said:**
> Your crontab line is broken. I believe -- at least on Red Hat -- you cannot have even a line continuation character followed by the rest of the line. My command lines looked so badly, I wrote a shell script to execute containing a nicely formatted line with line continuation characters.

Also, I've never seen the @ character used. What is it?

Finally, check your logs, syslog and messages (/var/log).
I have to have a space between all the times/command don't I? without the spaces it comes up with errors and won't save.
I'm pretty sure @ works the same as the at command.

---

