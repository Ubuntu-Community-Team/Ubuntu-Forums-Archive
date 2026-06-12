---
title: "Running import thru cron"
date: 2009-02-27
forum: General Help
---

### Post by mastermindg on 2009-02-27
I was having some difficulty running screenshots thru cron and I've searched google and nothing had helped, so I figured I'd share my wisdom with the bunch.

I've created a shell script that takes a screenshot of a window every minute. I'm running this cron locally under my own user. I am able to run this script manually without a problem.

```
ken:~$ crontab -u ken -l
* * * * * /home/ken/capture >> /home/ken/test.log 2>&1
* * * * * /home/ken/analyze
```

test.log was throwing this error:
```
import: unable to open X server `0:0'.
```

The key here was adding the exports $DISPLAY and $HOME:
```

DISPLAY=:0
export DISPLAY
HOME=/home/ken
export HOME
import -window "XP FXDD" -crop 16X28+1191+127 pic.jpg
```

Once the exports were added to my script everything starting working fine. I ended up removing pcspkr (sudo modprobe -r pcspkr) because import beeps every time it takes a screenshot.

---

### Post by jaon on 2011-09-14
Well it's been well over 2 years since you posted your tip but it just helped me figure out a problem I was having.  Once I exported HOME as well as DISPLAY it worked perfectly.

Thank you from Perth, Australia!
Jason

---

