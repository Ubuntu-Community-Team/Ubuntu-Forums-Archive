---
title: "desktop sound apps preventing cron job from outputing sound"
date: 2014-06-09
forum: Desktop Environments
---

### Post by Hiflux_Seven on 2014-06-09
[COLOR=#000000]A trivial application, but somthing that worked fine under 10.04 12.04 and fails under 14.04.[/COLOR]

[COLOR=#000000]sox (play) is configured via my user crontab to chime a cuckoo clock sound hourly:[/COLOR]
[COLOR=#000000]0 * * * * /usr/bin/play -q -v 0.25 /home/username/cuckoo.au[/COLOR]

[COLOR=#000000]The soundfile plays normally unless another desktop sound application is running simultaneously such as vlc or rhythmbox, in which case syslog still logs a successful execution of play but no sound output occurs. If I run play manually from a xterm, if works fine-- even with the other application(s) running. Executed from cron and it fails to produce the expected sound.[/COLOR]

[COLOR=#000000]I just upgraded from 12.04, and the exact same configuration worked fine.[/COLOR]

[COLOR=#000000]Any idea what's going on?[/COLOR]

---

### Post by kostkon on 2014-06-09
What's the output of
```
apt-cache policy libsox-fmt-pulse
```
If it isn't installed, try installing it, and it will replace the other plugin that is currently in use. According to [its package page]("http://packages.ubuntu.com/trusty/sox"), sox can use  one the following libs for I/O:
```
libsox-fmt-alsa
libsox-fmt-ao
libsox-fmt-oss
libsox-fmt-pulse
```

Hope that helps.

---

### Post by Hiflux_Seven on 2014-06-10
Great suggestion, but no joy.  Output indicated only libsox-fmt-alsa currently, so I installed libsox-fmt-pulse but still get the same results.

I can execute play from an xterm just fine with vlc streaming or playing an mp3, but cron can't seem to do the same. Syslog shows play (sox) gets executed without any errors, but no sound gets output.  Stop the desktop streaming/mp3 application and the cron job has no problem playing the file as it should.

Any other ideas?  What's different from me executing the command within the environment of an xtem that's keeping cron from successfully doing the same?

---

### Post by Hiflux_Seven on 2014-06-10
Solved the problem by exporting the DISPLAY variable before executing play within cron.  Have no idea why this is necessary, but it works.

crontab line now reads:
0 * * * *     export DISPLAY=:0 && /usr/bin/play -q -v 0.25 /home/username/cuckoo.au

With this entry, play will output the cuckoo.au sound regardless whether another desktop sound application is concurrently running.

---

### Post by Hiflux_Seven on 2014-06-10
exporting the DISPLAY variable within the crontab entry solved the problem.  No idea why, but it works.

the crontab entry now reads:
0 * * * *     export DISPLAY=:0 && /usr/bin/play -q -v 0.25 /home/usr/cuckoo.au

With the DISPLAY variable included, play (sox) outputs the cuckoo.au sound regardless of whether another sound application is executing concurrently on the desktop.

---

