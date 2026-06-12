---
title: "GDM - date/time format"
date: 2007-06-07
forum: Desktop Environments
---

### Post by zajjar on 2007-06-07
Hello,

how can I change date/time format on GDM theme (login screen)?
Example:
from: fri 08 jun, 08:20 am
to: 2007.06.08, 08:20

Regards.

---

### Post by bashologist on 2007-06-07
I can't find any information about this but the configuration files for the gdm themes are located in "/usr/share/gdm/themes/". Changing the time format in my panel doesn't seem to change anything, and the only option in these configuration files seems to be "%c" which I think just tells the system that it's a clock and needs to be updated every second.

The configuration files usually look like this:
```
  <!-- hostname and clock -->
  <item type="rect">
    <pos x="100%" y="100%" width="box" height="42" anchor="se"/>
    <box xpadding="10" spacing="10" orientation="horizontal">
      <item type="label">
        <pos x="100%" y="50%" anchor="e"/>
        <normal font="Sans Bold 11" color="#ffffff"/>
        <text>%h //</text>
      </item>
      <item type="label" id="clock">
        <pos x="100%" y="50%" anchor="e"/>
        <normal font="Sans 11" color="#ffffff"/>
        <text>%c</text>
      </item>
    </box>
  </item>
```
I couldn't figure it out. Good luck.

---

### Post by zajjar on 2007-06-08
Thanks for your answer.

I know that exists variable "%c", but how can I format it? :(
Maybe somewhere in gconf-editor exists any key which allows to change format of this variable?

Maybe there is some Guru who can help me (us) :)?


-- 
regards,
zajjar

---

### Post by zajjar on 2007-06-09
Is there anyboby gnome/gdm theme maker :) who can resolve this problem? 

-- 
regards,
zajjar

---

### Post by RedSquirrel on 2007-06-09
The format codes are in the man page for date:

```
man date
```

---

### Post by zajjar on 2007-06-10
No, it is not a format which is used in system date command!

For example, please try to use this format:
%Y.%m.%d %H:%M:%S 

You will not see: 
2007.06.10 20:00:09

but something similar to:
.i686.:20 ::


-- 
regards,
zajjar

---

### Post by RedSquirrel on 2007-06-11
> **zajjar said:**
> No, it is not a format which is used in system date command!

I think it is. Here is the information from the date manpage:

> **%c **locales date and time (e.g., Thu Mar  3 23:05:25 2005)I thought one could change the clock format, but it appears that other formats are not accepted. I am of the opinion that the only change you can make is to specify whether the clock is in 12-hour or 24-hour time, which you can change in the GUI "GDM Setup".


EDIT:

I suppose one other change one could make is to not have the date/clock displayed (by deleting %c in the configuration file).

---

