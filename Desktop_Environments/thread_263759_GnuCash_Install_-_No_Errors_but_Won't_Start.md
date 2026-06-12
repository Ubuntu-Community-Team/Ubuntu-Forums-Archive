---
title: "GnuCash Install - No Errors but Won't Start"
date: 2006-09-23
forum: Desktop Environments
---

### Post by GoJimbo on 2006-09-23
Tried installing GnuCash with apt-get and automatix and did not receive any errors.  But in either case when I tried to run it from my Applications menu it does not run.  It doesn't start and then fail, nothing happening at all.

Any ideas?

---

### Post by jd65pl on 2006-09-23
Try opening it from terminal. Does this work? I'm not sure what the exact command for this program is but try
```

sudo gnucash  
```

Does this launch the program/do you get an error message?


J

---

### Post by GoJimbo on 2006-09-23
Got it started.

First tried Alt-F2 and entering gnucash, that didn't work.

Second, cd'd to /usr/bin and issued sudo ./gnucash and it fired up.


Would still like to get the application to launch from my app menu but at least I know it works.

Thanks!

---

### Post by jd65pl on 2006-09-23
As you have found running it by...
```

sudo /usr/bin/gnucash
```

May I suggest adding a launcher with the command set to

```
gksudo /usr/bin/gnucash
```

J

---

