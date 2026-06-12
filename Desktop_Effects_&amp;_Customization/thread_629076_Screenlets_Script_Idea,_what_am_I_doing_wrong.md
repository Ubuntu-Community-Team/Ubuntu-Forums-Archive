---
title: "Screenlets Script Idea, what am I doing wrong?"
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by Dambrosio on 2007-12-01
I recently installed screenlets on 7.10. I'm running compiz fusion and everything is working perfect. I was trying to get the screenlets to load maybe 25-30 seconds after everything else because I get weird black boxes around each screenlet on startup. I'm thinking this is because compiz hasn't loaded yet. I tried to write a script to stall the execution of each screenlet. I changed the permissions of the file and I placed it in my home directory. I also included my script in the sessions, but nothing happened. Any ideas?
Here is the script:
```

#! /bin/sh
sleep 25;
exc /usr/local/share/screenlets/WordOfTheDay/WordOfTheDayScreenlet.py > /dev/null;
exc /usr/local/share/screenlets/UrbanDictionary/UrbanDictionaryScreenlet.py > /dev/null;
exc /usr/local/share/screenlets/Notes/NotesScreenlet.py > /dev/null;
exc /usr/local/share/screenlets/Facebook/FacebookScreenlet.py > /dev/null;
exc /usr/local/share/screenlets/DiskSpace/DiskSpaceScreenlet.py > /dev/null;
exc /usr/local/share/screenlets/CPUMeter/CPUMeterScreenlet.py > /dev/null;
exc /usr/local/share/screenlets/Clock/ClockScreenlet.py > /dev/null;
exc /usr/local/share/screenlets/ClearWeather/ClearWeatherScreenlet.py > /dev/null;
exc /usr/local/share/screenlets/Calendar/CalendarScreenlet.py > /dev/null;

```
Thanks,
Dan

---

### Post by SveinT on 2007-12-02
It's "exec" not "exc" :)

Besides, you'd need to use python to launch these apps. And you have to place a '&' at the end in order to let all lines run.

So here's en example line:

exec python /usr/local/share/screenlets/CPUMeter/CPUMeterScreenlet.py > /dev/null &

I hope that works

---

### Post by Dambrosio on 2007-12-02
Thanks a lot! I haven't really written a script by myself.

---

