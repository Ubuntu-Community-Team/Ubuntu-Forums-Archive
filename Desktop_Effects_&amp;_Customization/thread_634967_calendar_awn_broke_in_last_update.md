---
title: "calendar awn broke in last update"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by olavjunior on 2007-12-08
I used the calendar/clock applet. Then after the last update of awn, it got broke. 

When I run it in terminal I get the output:
```
File "/usr/lib/awn/applets/calendar/clockcal.py", line 45, in <module>
    import calthread
ImportError: No module named calthread

```

?

---

### Post by agaudio on 2007-12-08
I had a similar problem. A simple fix is to download the latest version:

[http://www.mediafire.com/?fzxxxtjm0e2]("http://www.mediafire.com/?fzxxxtjm0e2")

Then change the file ending from .awn to .tar and open it with your archive manager. Extract the file called calthread.py and copy it to 

/usr/lib/awn/applets/calendar/

This should solve the problem.

---

### Post by jayachandranm on 2007-12-15
Thanks for the tip, that worked for me too :-)

Jaya

---

