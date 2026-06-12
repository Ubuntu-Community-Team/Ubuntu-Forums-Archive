---
title: "Music alarm clock"
date: 2006-07-31
forum: Desktop Environments
---

### Post by Oxin on 2006-07-31
I've been doing really well making an almost full conversion to Ubuntu. I found Neverball to be so much fun since I don't have my Gamecube anymore for Super Monkey Ball. Just one thing is missing though, an alarm clock for the morning. I Windows, I programmed an alarm clock to wake me up at a certain time by opening Winamp and playing music I set the night before. Until I have that, I will sadly end and begin every day with Windows. I'm totally new to programming in a linux environment so I wouldn't know how to go about making my replacement. So, is there some available alarm clock time replacement for me or do you have suggestions on starting to program it? Would a bash script be capable of reading and acting on the current time? Thanks for your help.

---

### Post by IYY on 2006-07-31
I'm sure there is a program for it, maybe even with a graphical frontend, but I didn't really bother looking and just wrote my own, because it's so simple. Basically, you should make a shell script that plays the files you want:

It can be something like

```
#!/bin/sh
play /path/to/my/music/*
```

or if you want it to play in XMMS

```
#!/bin/sh
xmms /path/to/my/music/*
```

To make a script executable, just do

```
chmod +x scriptname
```

Then all you need to do is add this script to some task scheduler. Most common is **cron**. It's very simple, and you can learn how to use it in tutorials like:

[http://linuxweblog.com/node/24](http://linuxweblog.com/node/24)
[http://www.clockwatchers.com/cron_general.html](http://www.clockwatchers.com/cron_general.html)

Works like a charm. The only problem is that now I'm sick of the Grateful Dead after them waking me up at 7 AM every morning for a year.

---

### Post by Oxin on 2006-08-01
Well, I finally got around to trying this but I don't think cron is running.
Should this work? Cuz it's really not working. It is listed under crontab -l

* * * * * beep-media-player -p

Please help.

---

### Post by Holzster on 2006-08-01
Oxim

How about: bmp-alarm
(description) A general plugin using beep-media-player as an alarm clock.

---

### Post by Oxin on 2006-08-02
thanks a lot. I always try to make it more difficult than it has to be...

---

### Post by boobytrapped on 2006-08-02
Amarok also comes with an alarm plugin.

---

### Post by Holzster on 2006-08-02
boobytrapped

Off topic but are you running KDE oe Gnome?  the reason I ask is I am on Gnome & AmaroK is flacky for me (I know it is really made for KDE). I use Rhythenbox but I do like Am. better.

You have this issue> freezing > looses Music location> etc?

---

### Post by boobytrapped on 2006-08-02
@Holzster: I use amarok on Gnome.  I haven't had any bad experience with amarok on Gnome at all.  You didn't explain what type of flakiness you are seeing.  Anyhow, this is how I've set things up

* Use the xine sound engine (Settings->Configure amarok->Engine).  Default output plugin is set to "autodetect".  (Make sure amarok-xine is installed)
* Install some of the extra kde package that are very useful if you use amarok: kdemultimedia-kio-plugins, konqueror

---

### Post by reclusivemonkey on 2006-08-02
> **Oxin said:**
> Well, I finally got around to trying this but I don't think cron is running.
Should this work? Cuz it's really not working. It is listed under crontab -l

* * * * * beep-media-player -p

Please help.

You've probably fixed this now, but for future reference, you haven't given a time in the above cron example. Say you wanted this to run at 7 am, you should have;

```

0 7 * * * /path/to/beep-media-player -p

```

---

### Post by tzulberti on 2006-08-02
For KDe there is Kalarm, for gnome there is xmms-alarm or bmp-alarm

---

### Post by beuno on 2007-02-15
> **tzulberti said:**
> For KDe there is Kalarm, for gnome there is xmms-alarm or bmp-alarm

bmp-alarm plugin did it for me, although the mandatory "fade" is really annoying.

---

### Post by mcduck on 2007-02-15
I just use 'at 07:15 play /path/to/yourfile.mp3'..

---

### Post by Endolith on 2007-10-04
Is there an easier method than command line cron?  Like Windows' graphical "Task Scheduler" thing? Or a way to integrate it with a calendar?

I want to set more complex alarms, like: "wake me up from this playlist at 7 AM, unless it's the weekend or a holiday, in which case set the alarm for __ so I don't sleep too late, and let me override this and make it earlier or later for special cases the night before, without going off twice."  :-)

For instance, you could make a special playlist for holidays to remind you that you have the day off!

I am sick of my screaming banshee of an alarm clock.  I want to be woken up by something pleasant and gentle before I trudge off to work.

---

### Post by reclusivemonkey on 2007-10-05
> **Endolith said:**
> Is there an easier method than command line cron?  Like Windows' graphical "Task Scheduler" thing? Or a way to integrate it with a calendar?

I want to set more complex alarms, like: "wake me up from this playlist at 7 AM, unless it's the weekend or a holiday, in which case set the alarm for __ so I don't sleep too late, and let me override this and make it earlier or later for special cases the night before, without going off twice."  :-)

For instance, you could make a special playlist for holidays to remind you that you have the day off!

I am sick of my screaming banshee of an alarm clock.  I want to be woken up by something pleasant and gentle before I trudge off to work.

You'd need to write a script that checked your calendar and run that from cron. Everything you describe is possible, but its *exactly* the type of thing you need the power and flexibility of the command line for. 

If you're not prepared/able to do this, I have no idea where you would be able to get an app for this but it might be worth looking on Sourceforge for. The default Task Scheduler in Windows certainly wouldn't be able to handle anything like this.

If you install remind, enter all your calendar information and create a default override text file, then a few lines in a bash script would do this for you. You could even use Zenity to add a graphical interface for adding your override entries.

---

### Post by Endolith on 2007-10-05
> **reclusivemonkey said:**
> Everything you describe is possible, but its *exactly* the type of thing you need the power and flexibility of the command line for.

I'll keep looking.  I try to avoid rubbing sticks together unless there's no other option.  ;-)  

> I have no idea where you would be able to get an app for this but it might be worth looking on Sourceforge for

I will look, but there's lots of abandonware and such out there, so it's always best to get personal recommendations of things that normal people *actually use* on a daily basis.

> If you install remind, enter all your calendar information and create a default override text file, then a few lines in a bash script would do this for you. You could even use Zenity to add a graphical interface for adding your override entries.

I'll check it out.

---

### Post by mortazavi on 2007-10-10
Nice solution to a common problem ... Thanks.

I found that the VLC media player worked more directly for me ... 
The "player" (mentioned at the head of this thread) looks for devices ... 
With the "vlc" command all I needed to give was a pointer to an mp3 file ...

---

