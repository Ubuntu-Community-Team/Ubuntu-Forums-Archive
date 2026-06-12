---
title: "Some Screenlets won't load on startup"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by acwspoon on 2007-09-20
I entered all the screenlets I use into the Sessions startup programs individually but my Calendar, Weather, and sidebar screenlets don't load with the rest.

The calendar screenlet's directory is /usr/local/share/screenlets/  with the majority of the rest. 

While the weather and sidebar screenlets are in my home/username/ directory in their respective folders.


The calendar screenlet when I just try to open it from the folder it's in, it won't load.  I have to go to the System> Preferences> Screenlet manager and I can load it from there.

The weather and sidebar screenlets I just have to go to their folders and just run them from there.

I would really appreciate some help I really don't know what I'm doing wrong.

---

### Post by acwspoon on 2007-09-23
wow this is the first thread i've had that no one could help me with.   If anyone sees this, I would really appreciate the help.

---

### Post by PiniouF on 2007-09-27
Hi !

Same problem with other screenlets ! 
"Auto start" ok for :
[LIST]
[*]Sidebar
[*]DigitalClock
[*]Weather
[/LIST]

Don't work with :
[LIST]
[*]Calendar
[*]CPU_Meter
[/LIST]
For those, I have to use screenlets-manager although *Automatically start on login* is checked. :(

All are in my home directory (~/.screenlets/)

---

### Post by acwspoon on 2007-09-29
Ok so I have the screenlets in the home directory and in the filesystem.  I guess somehow I install it twice but now I can't uninstall it.... If I go to the directory by cd and sudo make uninstall it doesn't work.... I just want to start from scratch because now I will know what to do.

---

### Post by FranMichaels on 2007-10-01
Hi,

I have the same issue. I noticed this
> 
Proserpine:~$ screenletsd 
Screenletsd isn't used for starting screenlets anymore. Please use the new 'screenlets-manager' or start each Screenlet individually from now on.

I'm running screenlets 0.10 (compiled from tarball)

So maybe this is normal behavior, or something to be fixed later?

:confused:

---

### Post by travis31 on 2007-10-07
I had the same problem, the Calendar and CPU_Meter screenlets would not start at login. It turned out that their scripts did not have execute permission. I gave execute permission to CPU_MeterScreenlet.py and CalendarScreenlet.py and now they load correctly :)

---

### Post by raddevon on 2007-10-19
> **travis31 said:**
> I had the same problem, the Calendar and CPU_Meter screenlets would not start at login. It turned out that their scripts did not have execute permission. I gave execute permission to CPU_MeterScreenlet.py and CalendarScreenlet.py and now they load correctly :)
I'm having the same problem. My screenlets won't execute on startup. When I start the manager, I get an error.
```
Unable to connect or launch daemon. Some values may be displayed incorrectly.
```
I have a feeling this may be the root of the whole problem, but I can't find on any forum how to fix it. None of my screenlets load on startup. In fact, after I boot, the "Automatically run..." boxes are now unchecked. I'm not sure where to go from here.

---

### Post by Depressed Man on 2007-10-19
Yeah that seems to be the problem. You can try manually adding the screenlets to the startup session.

Just the link to the specific directory with the code inside then the python file itself. Like clock.py then some code like > something after. 

Just look at any other screenlets that are working and copy that style.

What I've noticed is that some just plain don't work with it still though. :( 

Might be a version issue?

Try this, for the terminal part in the session add. 

python /usr/local/share/screenlets/TuxaGoshi/TuxaGoshiScreenlet.py

---

### Post by travis31 on 2007-10-22
> **raddevon said:**
> I'm having the same problem. My screenlets won't execute on startup. When I start the manager, I get an error.
```
Unable to connect or launch daemon. Some values may be displayed incorrectly.
```


I have seen this error a couple of times, but it seems to go away if you just close the Screenlets Manager and start it again.

> 
I have a feeling this may be the root of the whole problem, but I can't find on any forum how to fix it. None of my screenlets load on startup. In fact, after I boot, the "Automatically run..." boxes are now unchecked. I'm not sure where to go from here.


The way I fixed it was to uncheck the "Automatically run..." box for all screenlets. Now I have a script named StartScreenlets.sh that runs on startup and starts the individual screenlets, like this:

```

python /usr/local/share/screenlets/Clock/ClockScreenlet.py
python /usr/local/share/screenlets/Calendar/CalendarScreenlet.py

```

This is also cleaner, since I have just one entry for my script in Sessions rather than one entry per screenlet.

---

### Post by DerekInGermany on 2007-10-24
Thanks travis31, that worked for me :guitar:

Derek

---

### Post by amphoterous on 2007-10-26
Ok I need a little help. My screenlets don't get loaded with my script.

I created a startup script:
```
sudo nano /etc/init.d/StartScreenlets.sh
```
My script contains
```
python /usr/local/share/screenlets/Calendar/CalendarScreenlet.py
python /home/kit/.screenlets/DigitalClock/DigitalClockScreenlet.py
python /home/kit/.screenlets/ClearWeather/ClearWeatherScreenlet.py
```

Do I need to change permissions or anything for that startup script?

(None of my screenlets are set to enabled or to automatically start in the screenlets manager)

---

### Post by travis31 on 2007-10-26
Try this - Go to Start->System->Preferences->Sessions. Click on Add, and give the path of your script where it asks for Command. Add a Name of your choice and then do a logout and login.

---

### Post by DerekInGermany on 2007-10-26
and don't forget to make the script executible (right click on the file Properies->permissions the check off Execute)

Derek

---

### Post by amphoterous on 2007-10-26
Ok heres what I did. I moved the script (StartScreenlets.sh) into my home directory. I right clicked on it and made it executable. Then I also went to Sessions and added it.

Now I have two problems, the first is that my script runs, but not all my screenlets start up. Only the first one starts up, and the second one will load if I close the first one. The third one loads if I close the second one... etc. 

I also managed to add THREE calendars somehow. If I choose quit on any of the calendars they all close. All I want is ONE calendar! How do I chose two and keep one?

Thanks for helping me.

---

### Post by amphoterous on 2007-10-27
I was able to solve both of my problems. With multiple instances of a screenlet I simply right clicked on it and did Delete. I thought that "Delete" would delete the screenlet off of my computer.

My script also was not formatted correctly. It now looks like this:
```
#!/bin/sh
python -u /usr/local/share/screenlets/Calendar/CalendarScreenlet.py &
python -u /home/kit/.screenlets/Time/TimeScreenlet.py &
python -u /home/kit/.screenlets/ClearWeather/ClearWeatherScreenlet.py &
```

---

### Post by travis31 on 2007-10-27
@amphoterous
Good that you finally got it to work. I did not notice that you were missing the "&" at the end of each line in your script.

---

### Post by daz4126 on 2007-11-15
I have tried Travis' method, but this only works consistently for the clock screenlet. I have 3 others (all not included in the default) - gmail, cpu_meter and NowCalendar. They all start sometimes, but not very often. I can start them using the screenlets manager - or by simply invoking the python file, but getting them to open on startup just isn't working. This is a shame, because screenlets is by far the nicest desklet app for Gnome.

DAZ

---

### Post by amphoterous on 2007-11-15
If you look at my steps above I outlined a solution for starting your screenlets.

---

### Post by spiff95 on 2007-11-15
You can also look here for another way to fix the daemon error:

[http://ubuntuforums.org/showthread.php?t=533145&highlight=screenlet+daemon+error]("http://ubuntuforums.org/showthread.php?t=533145&highlight=screenlet+daemon+error")

---

### Post by spiff95 on 2007-11-15
The fix in the thread I linked may work for others, but it didn't work for me (post #19). My apologies.

---

### Post by daz4126 on 2007-11-16
> **amphoterous said:**
> If you look at my steps above I outlined a solution for starting your screenlets.

Sorry, I was on page 1 and completely missed your post! It works great now (except now the gmail screenlet won't start because it has login issues....)

Thanks a lot amphoterous!

DAZ

---

### Post by Kiyo86 on 2008-02-19
I don't know if this helps, and I'm still trying to figure out what this means, but when you launch the Terminal and type in "screenlets-manager", it responds with "DAEMON FOUND!" and then it starts the Screenlets-Manager without error messages.

---

### Post by Kiyo86 on 2008-02-19
I was working on the Screenlets-manager through the terminal, so that the Daemon would be active and I could monitor what was happening as I attempted to make changes, and I found something interesting.

Here I start the Manager through the terminal:

> rkmj@beefjerkey:~$ screenlets-manager
DAEMON FOUND!

Then I click on my desired screenlet, and click "Launch" (I'll use the native "Notes" screenlet as an example:
> Notes
Launching Screenlet from: /usr/local/share/screenlets/Notes/NotesScreenlet.py
Logging output goes to: $HOME/.config/Screenlets/NotesScreenlet.log
REGISTER screenlet: NotesScreenlet

Everything seems to be working fine up until here, when I click "Automatically Start on Login" Now, I get this, which is where I think the autostart problem lies:

> Create autostarter for: /usr/local/share/screenlets/Notes/NotesScreenlet.py
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 575, in toggle_autostart
    self.create_autostarter(info.name)
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 193, in create_autostarter
    f = open(starter, 'w')
IOError: [Errno 13] Permission denied: '/home/rkmj/.config/autostart/NotesScreenlet.desktop'

 hope that this helps. I'm working on it, but I'm not getting very far. If anyone figures this out, please post!

Good Luck!

---

### Post by spiff95 on 2008-02-20
> **Kiyo86 said:**
> I was working on the Screenlets-manager through the terminal, so that the Daemon would be active and I could monitor what was happening as I attempted to make changes, and I found something interesting.

Here I start the Manager through the terminal:



Then I click on my desired screenlet, and click "Launch" (I'll use the native "Notes" screenlet as an example:


Everything seems to be working fine up until here, when I click "Automatically Start on Login" Now, I get this, which is where I think the autostart problem lies:



 hope that this helps. I'm working on it, but I'm not getting very far. If anyone figures this out, please post!

Good Luck!

I haven't tried it, but have you tried starting the screenlet manager with sudo? That may allow the autostart to work. I've got to get going to work, or I would give it a shot and let you know.

Hope this helps!:)

---

