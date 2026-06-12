---
title: "start tilda when Gnome loads"
date: 2006-07-26
forum: Desktop Environments
---

### Post by machs_fuel42 on 2006-07-26
i'd like tilda to start with gnome automatically, if there a file that i can edit to add it to the programs that start when gnome loads up?  (after login)

thanks-

---

### Post by ape on 2006-07-26
Navigate into the System menu, then Preferences, then Sessions.  Go to the 'Startup Programs' tab.  Add your entry for tilda here. 

--ape--

---

### Post by machs_fuel42 on 2006-07-26
Perfect - thanks, found this too.. great resoure

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_run_programs_on_startup_when_login_into_GNOME](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_run_programs_on_startup_when_login_into_GNOME)

---

### Post by munkar on 2006-12-29
when i put tilda in my startup programs, it appears to run on startup (the window briefly comes up), but it then disappears. i can see it in my "current session," but when i press the key that's supposed to bring it up, nothing happens.

it shouldn't disappear anyway, since i've set it to "Display pulled down on start." every once in a while it works as it's supposed to, but i can't see any pattern. there's another post here on the exact same problem....

any ideas what could be going on? i'm trying to use it to emulate pc-com, which is the only Windows program that i *really, really* miss.

---

### Post by raul_ on 2006-12-29
put it to sleep for a while. Instead of loading tilda, create a file (gedit filename.sh)

```

sleep 20 && tilda;

```

save it and make it executable by running
```

chmod +x <file>

```

and try to load that script on startup

---

### Post by munkar on 2006-12-30
thanks, raul, but unfortunately it seems to give the same result, no matter how long i set the delay. this is my script:

```
sleep 40
export DISPLAY=:0
tilda
```

---

### Post by raul_ on 2006-12-30
Are you using beryl?

---

### Post by munkar on 2006-12-30
nope.

---

### Post by munkar on 2006-12-30
the script works, by the way, when run from the terminal. but when i load, it sleeps 40 seconds, then i briefly see the tilda terminal before it disappears. then it's impossible to bring up.

---

### Post by munkar on 2007-01-06
this problem resolved itself when i upgraded to Eft.

---

