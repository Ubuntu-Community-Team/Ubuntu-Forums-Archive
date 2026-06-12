---
title: "Alarm clock"
date: 2012-02-10
forum: Desktop Environments
---

### Post by chejose on 2012-02-10
I have been trying to install the alarm clock for Ubuntu, and am not having very good luck.

The software center and synaptic both have the 1.2.5 version, but I know there is a 3.2. something version out.

I tried to install it, but I'm afraid that I don't have the capacity to do it.

So could someone please help me to install the latest version of the alarm clock?

I am pretty slow, so need complete instructions.

Many thanks,

José

---

### Post by Krytarik on 2012-02-10
> **chejose said:**
> The software center and synaptic both have the 1.2.5 version, but I know there is a 3.2. something version out.
Are you aware that there are two apps with the same name, "Alarm Clock", but with differently named packages, "alarm-clock" and "alarm-clock-applet"?:

[http://packages.ubuntu.com/search?keywords=alarm+clock&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=alarm+clock&searchon=names&suite=all&section=all)

"alarm-clock" seems to be not actively developed since quite some time, and "alarm-clock-applet" is currently in version 0.3.2.

Regards.

---

### Post by chejose on 2012-02-10
Well, thanks. No I did not know there were two... and I obviously have the wrong one! So will make an attempt to install the right one.

Many thanks.

José

---

### Post by chejose on 2012-02-10
Well, synaptic says I have the alarm-clock-applet installed, but it does not show up in any menu. Now what?

José

---

### Post by Krytarik on 2012-02-10
> **chejose said:**
> Well, synaptic says I have the alarm-clock-applet installed, but it does not show up in any menu. Now what?
Incidentally, I've tested them both, and eventually decided for "alarm-clock" back then. However, if you want to stick with your choice, it should turn up in the "Accessories" sub-menu/category, or, alternatively, you can run via the Alt+F2 dialog:
```
alarm-clock-applet
```Btw., what Ubuntu version and what DE/session are you running?

---

### Post by chejose on 2012-02-11
Back to it after a fair night's rest.

There is nothing in the "accessories" file, and when I try to open alarm-clock-applet with alt F2 I get a reply that it does not exist. Synaptic says it does, but... oh well.

I got the impression from reading that alarm-clock was an old app and that the applet was "up-to-date. But with no experience I have no way to chose.

I'm running 10.4

I'll try a reinstall and see what happens. And will install alarm-clock agin to see If I can compare them.

Thanks,

José

---

### Post by chejose on 2012-02-11
I did a re-install for the alarm-clock-applet and installed alarm-clock again. No sign of the applet, but alarm-clock is up and working. So I guess the wisest would be to simply stay with that.

José

---

### Post by chejose on 2012-02-11
Actually the main reason I wanted to try alarm-clock-applet is that I cannot figure out how to stop the alarm (in alarm-clock) once it goes off! There are no instructions or help, so the only way I have found out how to do it is to close the program and then open it gain. There MUST be a better way.

I have 4 alarms set for every day, and it is a bother to have to open and close the program each time. 

José

---

### Post by Krytarik on 2012-02-11
> **chejose said:**
> I did a re-install for the alarm-clock-applet and installed alarm-clock again. No sign of the applet, but alarm-clock is up and working.
> **chejose said:**
> I'm running 10.4
In Lucid 10.04, "alarm-clock-applet" is still tied to the Gnome Panel (that's why it was called "applet" in the first place); so you obviously need to run Gnome Panel to use it, then just add it via the usual "Add to Panel" dialog.

> **chejose said:**
> Actually the main reason I wanted to try alarm-clock-applet is that I cannot figure out how to stop the alarm (in alarm-clock) once it goes off! There are no instructions or help, so the only way I have found out how to do it is to close the program and then open it gain.
Honestly, I've no idea what you're talking about. :P I use either "Passive popup" or "Dialog window" as the "Notification" method (currently then first one); so I either need to OK the dialog window, or the Notify-OSD popup disappears after the set amount of time - but yes, there is apparently a bug with the dialog window method, I'd always need to OK the dialog twice, meaning two windows pop up after another, which was the reason why I've eventually decided for the Notify-OSD method.

---

### Post by chejose on 2012-02-11
Kyrtarik

Thanks for taking the time and having the patience to get back to me on this thing. I now realize that there is a pop-up window for alarm-clock and have activated it and will see.

But I mainly answer because I did not know that Gnome Pannel was something you could run. I though it was simply the name for the desktop configuration. So that is something new to investigate. It has been some time since I have used Windows, and what I like about Linux is that almost anything can be done and there is always something new to learn.

Bit by bit

José

---

### Post by Rodney9 on 2012-02-11
Can't turn off alarm seems to be a bug - 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=635100](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=635100)


I also get the bug > Cannot play more than 1 sound at once if I try to set a new alarm.

Would there be a way of using cron or something else for multiple alarms, I need something reliable.
 

Well I found [_this_]("http://bytebaker.com/2009/08/23/roll-your-own-linux-alarm-clock/") so I will give it a whirl.

Rodney

---

### Post by Rodney9 on 2012-02-12
Well I ended up going with a script called alarm.sh

```
#!/bin/sh

ogg123 -z ~/Music/*.ogg
```

and added it to cron

```
33 04 * * * /bin/alarm.sh 
```

and this 

```
sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`
```

rtcwake wakes my laptop from sleep at 4:30am
cron plays my alarm.sh script at 4:33am
ogg123 -z shuffles my Music directory.

Rodney

---

### Post by ylk on 2012-04-12
> **Krytarik said:**
> Honestly, I've no idea what you're talking about. :razz:  I use either "Passive popup" or "Dialog window" as the "Notification"  method (currently then first one); so I either need to OK the dialog  window, or the Notify-OSD popup disappears after the set amount of time -  but yes, there is apparently a bug with the dialog window method, I'd  always need to OK the dialog twice, meaning two windows pop up after  another, which was the reason why I've eventually decided for the  Notify-OSD method.


Would be nice to "not" have to select the "Passive popup" (or  "Dialog window") checkbox for each alarm.  In other words, prefer to  have a "set it once and forget it" setting in Preferences dialog.

---

