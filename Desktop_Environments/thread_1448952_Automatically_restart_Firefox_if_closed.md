---
title: "Automatically restart Firefox if closed"
date: 2010-04-07
forum: Desktop Environments
---

### Post by chipperuga on 2010-04-07
For a kiosk scenario, I run this script to close & restart Firefox when the screensaver is activated (the monitor also goes to sleep). 

I want to run a loop that, if Firefox is closed, it will automatically re-open. Is there a way to use dbus-monitor to accomplish this?

> #!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver', member='ActiveChanged'\"";

open (IN, "$cmd |");

while (<IN>) 
{
 if (m/^\s+boolean true/) 
   {[INDENT]        system("pkill -9 firefox");
       system("/usr/bin/firefox &");
       system("xset dpms force off");
[/INDENT]} 
 elsif (m/^\s+boolean false/) 
    {[INDENT]       #when not idle
      #system("/usr/bin/firefox &");
[/INDENT]}
}

---

### Post by TheSqueak on 2010-04-07
```
#!/bin/bash

while true
do
if [ ! `pgrep firefox-bin` ] ; then
/usr/bin/firefox
fi
sleep 5
done
```

Something like that could work

---

### Post by chipperuga on 2010-04-07
TheSqueak,

Works perfect--thanks! How resource intensive will this script be? The kiosks we have are old, but run Ubuntu like a champ. I don't want to bog them down by constantly grep'ing for Firefox.

I'd like the script to do: If Firefox closes, restart Firefox.

...as opposed to "check if Firefox is running. If it's not, open Firefox."

Think it's possible? Hope I explained it right.

Chip

---

### Post by TheSqueak on 2010-04-07
```
time pgrep firefox-bin
28376

real    0m0.009s
user    0m0.000s
sys     0m0.008s
```

It doesn't take much CPU time to check, so it shouldn't be that resource intensive.

Somebody with more programming knowledge than me might be able to tell you if there's a way of catching firefox closing rather than checking that it's running, but I don't know how myself, sorry.

---

### Post by basejumper9 on 2010-07-14
Some minor changes I made as its faster to check a file:
```

#!/bin/bash

while true
do
if [ ! -h /home/username/.mozilla/firefox/689o3rsb.default/lock ]; then 
        DISPLAY=:0 firefox 
fi
sleep 5
done

```
You will have to substitute in your own username and profile.

Firefox creates a symbolic link to 127.0.0.1:[pid] and deletes this on clean shutdowns. I haven't checked against crashing and such so the grep option might be more flexible.

---

