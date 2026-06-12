---
title: "All My Cron Jobs stopped!!"
date: 2007-09-10
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-09-10
Got to work this morning, and all my scheduled cron jobs failed to start?
I noticed its running jobs for root , so this suggests to me Cron is working, but cant access DISPLAY:0 for GUI apps, also when I view all the tasks in Kcron, theyre all greyed out.
I cant think what else to try, heres my cron jobs


Display=DISPLAY=:0

# Icepodder
56 8,14 * * 1,2,3,4,5   export DISPLAY=:0 && /usr/bin/icepodder

# Kill Icepodder
15 16 * * 1-4 killall python
55 15 * * 5 killall python

# Restart Gdesklets
16 16 * * 1-4 export DISPLAY=:0 && /usr/bin/gdesklets
56 15 * * 5 export DISPLAY=:0 && /usr/bin/gdesklets
# Democracy Player
55 8,14 * * 1,2,3,4,5   export DISPLAY=:0 && /usr/bin/democracyplayer

# Kill Democracy Player
55 14,15 * * 1-5 killall democracyplayer

# Radio Paradise
57 8 * * 1-5 export DISPLAY=:0 && /usr/bin/audacious [http://scfire-nyk0l-2.stream.aol.com:80/stream/1048](http://scfire-nyk0l-2.stream.aol.com:80/stream/1048)
# 55 8 * * 1-5 export DISPLAY=:0 && /usr/bin/audacious /home/steve/music/rp.m3u

# Kill Radio Paradise Stream
28 16 * * 1,2,3,4 /usr/bin/killall /usr/bin/audacious
58 15 * * 5 /usr/bin/killall /usr/bin/audacious

# Note: Lines beginning with "#\" indicates a disabled task.

---

### Post by mister_p_1998 on 2007-09-11
Ok I think Ive pinned it down to the display:0 I messed about with permissions in my home folder last week, & think I may have messed up the access to DISPLAY:0

Im getting this error:

From: root@Video-Desktop (Cron Daemon)
To: steve@Video-Desktop
Subject: Cron <steve@Video-Desktop> export DISPLAY=:0 && /usr/bin/icepodder
X-Cron-Env: <Display=DISPLAY=:0>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/steve>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=steve>

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
[<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
Beep-Media-Player couldn't be imported
Traceback (most recent call last):
  File "CastPodderGui.py", line 3623, in ?
    main()
  File "CastPodderGui.py", line 3617, in main
    myApp = iPodderGui(ipodder)
  File "CastPodderGui.py", line 685, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
SystemError: wxEntryStart failed, unable to initialize wxWidgets!  (Is DISPLAY set properly?)
/usr/bin/icepodder: line 22:  6259 Segmentation fault      python CastPodderGui.py

How do I restore access to display?
Steve

---

### Post by tvrg on 2007-09-11
are you editing crontab as root or as a user?

---

### Post by mister_p_1998 on 2007-09-11
Crontab -e as a user

---

### Post by tvrg on 2007-09-11
and why are you exporting the display before the command? it should be in your env if your gui is running...

---

### Post by mister_p_1998 on 2007-09-11
> **tvrg said:**
> and why are you exporting the display before the command? it should be in your env if your gui is running...

Its the only way I can get a GUI program running in Cron, (Or is there another way?)

Steve

---

### Post by tvrg on 2007-09-11
also, does it work if  you run xhost local:my_user beforehand?

---

### Post by mister_p_1998 on 2007-09-11
> **tvrg said:**
> also, does it work if  you run xhost local:my_user beforehand?

No, I tried that too, Ive been working on it two days now, no joy at all.
how do I set the DISPLAY variable in Env?

---

### Post by tvrg on 2007-09-11
echo $DISPLAY
should say if it's set, otherwise export DISPLAY:"xxx"

---

### Post by mister_p_1998 on 2007-09-11
> **tvrg said:**
> echo $DISPLAY
should say if it's set, otherwise export DISPLAY:"xxx"
Hmm,
tried it again and it reports:
export: `:0.0': not a valid identifier

---

### Post by tvrg on 2007-09-11
hmm, you got me there, those were my only suggestions and you can google just as well as I do :)

sorry I couldn't help

---

### Post by mister_p_1998 on 2007-09-13
Latest update,
Cron runs for all users except me. New users run fine and export to DISPLAY:0
but my user cant.
Steve

---

### Post by psusi on 2007-09-13
You REALLY should not be running gui programs from cron.  What if you aren't logged in?  What if someone else is?  The jobs will fail.  

If you insist though, your syntax is wrong.

You want a line saying DISPLAY=:0, not display=DISPLAY=0.  Or you can have the DISPLAY=:0 ( no need for export ) in the command line itself, but you don't need both.

---

### Post by tvrg on 2007-09-13
if the app desperately needs X you could try running int over xvfb [http://www.x.org/archive/X11R6.8.0/doc/Xvfb.1.html](http://www.x.org/archive/X11R6.8.0/doc/Xvfb.1.html)

but in my experience it's a pain to get going too :)

---

### Post by pmg on 2007-09-13
I wonder if you need to set the XAUTHORITY environment variable also:  **export XAUTHORITY=~/.Xauthority**

---

