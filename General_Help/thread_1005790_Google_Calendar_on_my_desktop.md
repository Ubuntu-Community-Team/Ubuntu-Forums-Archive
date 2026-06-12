---
title: "Google Calendar on my desktop???"
date: 2008-12-08
forum: General Help
---

### Post by justinjstark on 2008-12-08
I''m working on a way to get a google calendar widget on my desktop.  I have a few possibilities but none of them work properly:

1) Screenlets with the google calendar embed html as a widget.  This works fine except when I first login (before my wireless connects).  Instead of the widget appearing I get "Internet connection required for this screenlet" (or something similar) and then the screenlet doesn't load.  You would figure it would wait for an internet connection and then load, but no.

2) Google gadgets are awesome.  But the google calendar gadget has a similar problem as the screenlet.  When I first log in (before my wireless connects) and the calendar loads, it can't grab any information.  Rather than trying again, it simply fails and I have to go into options and reapply them to get it to load the calendar data.

3) Evolution-webcal lets me put appointments and things in the gnome-panel clock/calendar applet.  But I want something on my desktop that alerts me of todays appointments passively.  Anyway, it seems to have a lot of bugs.  For instance, I have an all-day appointment set as "payday" every other Friday but it shows up on the calendar every day.

Do you guys know of a better way to put a calendar on my desktop?

Or better yet, a way to make a script that will wait for an internet connection before loading screenlets??? (<-- this would be ideal)

BTW: I can't just wait for some T seconds before loading screenlets on startup because most of the wireless networks I use require manual authentication.

---

### Post by phidia on 2008-12-08
You could have a look at gOS linux since that Ubuntu based linux does have a desktop calendar. Alternatively you could search [here]("http://bash.cyberciti.biz/") for a script you can use or modify.

---

### Post by justinjstark on 2008-12-08
> **phidia said:**
> You could have a look at gOS linux since that Ubuntu based linux does have a desktop calendar. Alternatively you could search [here]("http://bash.cyberciti.biz/") for a script you can use or modify.

It looks like gOS just uses google gadgets.  So that's basically what I have.

As far as a script, I am thinking that I should make a bash script to ping google.com every 10 seconds until it succeeds.  Then load screenlets.

I managed to find the following which simply pings something and then says whether it exists.  If I can somehow make a while look until it succeeds, then I'm in business.

```

#!/bin/bash

if [ -z "$1" ]; then
echo "Usage: `basename $0` ip-addr"
exit 1;
fi

ping -c 1 -W 10 $1 &>/dev/null
if [ $? -eq 0 ]; then
echo "Ping succeeded"
# Commands here
else
echo "Ping failed"
# Commands here
fi

```

---

### Post by justinjstark on 2008-12-08
Piece of cake.  I'm just going to put this bash script in /usr/bin and add it to my sessions.

```
#!/bin/bash

ping -c 1 -W 10 google.com &>/dev/null
until [ $? -eq 0 ]; do
	sleep 10
	ping -c 1 -W 10 google.com &>/dev/null
done

/usr/share/screenlets-manager/screenlets-daemon.py
```

EDIT:
This didn't quite work since some of the networks I connect to don't allow ping.  I came up with another solution in a different thread for those interested:

[http://ubuntuforums.org/showthread.php?p=6333715#post6333715](http://ubuntuforums.org/showthread.php?p=6333715#post6333715)

---

### Post by hachel on 2009-10-24
> **justinjstark said:**
> I''m working on a way to get a google calendar widget on my desktop.  I have a few possibilities but none of them work properly:

1) Screenlets with the google calendar embed html as a widget.  This works fine except when I first login (before my wireless connects).  Instead of the widget appearing I get "Internet connection required for this screenlet" (or something similar) and then the screenlet doesn't load.  You would figure it would wait for an internet connection and then load, but no.


how did you get it to work?
when I convert the google-gadget-app to a screenlet and start it doesn't display anything at all but gives me this terminal-output instead:
```
Launching Screenlet from: /home/hachel/.screenlets/GoogleCalendar/GoogleCalendarScreenlet.py
Logging output goes to: $HOME/.config/Screenlets/GoogleCalendarScreenlet.log
REGISTER screenlet: GoogleCalendarScreenlet
True
Traceback (most recent call last):
  File "/home/hachel/.screenlets/GoogleCalendar/GoogleCalendarScreenlet.py", line 324, in <module>
    screenlets.session.create_session(GoogleCalendarScreenlet)
  File "/usr/lib/python2.6/dist-packages/screenlets/session.py", line 472, in create_session
    session.start()
  File "/usr/lib/python2.6/dist-packages/screenlets/session.py", line 254, in start
    sl.finish_loading()
  File "/usr/lib/python2.6/dist-packages/screenlets/__init__.py", line 1243, in finish_loading
    self.on_init()
  File "/home/hachel/.screenlets/GoogleCalendar/GoogleCalendarScreenlet.py", line 219, in on_init
    self.load_widget()
  File "/home/hachel/.screenlets/GoogleCalendar/GoogleCalendarScreenlet.py", line 282, in load_widget
    self.width = int(self.widget_width)+30
ValueError: invalid literal for int() with base 10: "100% cellspacing=0 cellpadding=1 border=0>';\n\t\n\t// check for a leap year, set the max # of days for february in the max_d array\n\tif (((cur_m.getFullYear() % 4) == 0)"
```

---

### Post by fragos on 2009-10-24
You can sync the Evolution Calendar with the Google Calendar and then Evolution features will work for you.

---

### Post by yknivag on 2009-10-24
[rainlender](http://www.rainlendar.net/) also supports synchronisation with Google Calendar.

---

### Post by hachel on 2009-10-25
hi, i've had rainlendar for a while but google calendar is only supported with the pro-version.
And Evolution won't display on the desktop. Also adding new dates with googles quick-add is so much more simple than the over-bloated Evolution.

Anyway, apparently it's a google-problem. ( [http://groups.google.com/group/Google-Gadgets-API/browse_thread/thread/b8ee4c94857f6810](http://groups.google.com/group/Google-Gadgets-API/browse_thread/thread/b8ee4c94857f6810) )

---

