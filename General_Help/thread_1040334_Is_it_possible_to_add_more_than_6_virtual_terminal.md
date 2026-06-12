---
title: "Is it possible to add more than 6 virtual terminals??"
date: 2009-01-15
forum: General Help
---

### Post by codename_nixon on 2009-01-15
hi, i was wondering if it was possible to have more than 6 virtual terminal??
may be 11 and all binded to cntrl+alt+fx


where x = to a function key

leaving only f12 to switch back to X???

i edited /etc/inittab and successfully added tty7 but further was of no use

=============================================================

i also wanted set a local variable as environment so its available at every logon in shel ,when i do a echo $VARNAME

eg > EXAMPLE=hi

>echo $EXAMPLE

now i want this to be permanent

how to do this??

---

### Post by doug-M on 2009-01-15
You might want to look at gnu screen if you want multiple terminals. It might be useful for what you are doing or it might not.

I used to use it all the time for the ability to detach a terminal.
Detach session at work, go home and login then reattach the terminal session.

[http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)
[http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)
[http://www.redhatmagazine.com/2007/09/27/a-guide-to-gnu-screen/](http://www.redhatmagazine.com/2007/09/27/a-guide-to-gnu-screen/)

---

### Post by heindsight on 2009-01-15
> **codename_nixon said:**
> hi, i was wondering if it was possible to have more than 6 virtual terminal??
may be 11 and all binded to cntrl+alt+fx


where x = to a function key

leaving only f12 to switch back to X???

i edited /etc/inittab and successfully added tty7 but further was of no use


It can be done, but it may take some work to get it right. At the very least, you'll need to add more tty? files to /etc/event.d (have a look at the ones that are already there).

You'll probably also want to edit /etc/default/console-setup and change the ACTIVE_CONSOLES line. 

Finally, you'll notice that normally, with only 6 virtual consoles and an X session running, some log output gets sent to tty8, you'll probably want to change or disable that (i'm not sure exactly how - i thought it was controlled through /etc/syslog.conf but it would appear that's not the case). 

It seems that /etc/init.d/usplash works on the assumption that tty8 is unused. It seems likely that some other things might also expect the higher tty's to be unused (If you put your first X session on tty12, you might not be able to start a second X session, for example).

I'm just curions, do you really need that many virtual consoles? I've never found myself needing more than 4 and I think the effort of configuring more is probably not worth it...

> 
i also wanted set a local variable as environment so its available at every logon in shel ,when i do a echo $VARNAME

eg > EXAMPLE=hi

>echo $EXAMPLE

now i want this to be permanent

how to do this??

You can put the variable definition in /etc/profile

---

### Post by codename_nixon on 2009-01-15
thx for the reply guys ..............

i just wanted to see if it was possible  , 6 is more than enough for me 2

---

