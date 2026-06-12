---
title: "24 hour digital clock?"
date: 2009-07-10
forum: Desktop Environments
---

### Post by jpmallory on 2009-07-10
kubuntu 9.04

Where is the setting to change the clock from a 12-hour to a 24-hour format?  I'm certain it's right in front of me, but I keep overlooking it.

---

### Post by gettinoriginal on 2009-07-12
Don't run kubuntu, but found this, hope it helps  :p
Right-clicking on the clock, select Time & Date Format. Under the Time & Dates tab choose "pH:MM:SS AMPM" for time format makes it 12hr, so there must be a setting for 24hr.

---

### Post by krazyd on 2009-07-13
System Settings > Regional & Language > Country/Region & Language > Time & Dates (tab) > Time Format

---

### Post by Mirge on 2009-07-19
I'm actually trying to change mine FROM 24 hour time to 12 hour time...

If I right-click the clock and go to "Adjustable clock settings".. it has it formatted as:

%H:%M:%S

I tried %pH, but it doesn't work.. just literally puts %pH

---

### Post by ecmatter on 2009-07-19
```


man date


```

---

### Post by lindsay_keir on 2010-08-03
Like Mirge, my problem is **[WAS]** trying to display a 12-hour AMPM clock.
[LIST]
[*]I used System Settings > Regional & Language > Time & Dates >
[*]Selected from the Time Format drop down list pH:MM:SS AMPM... and the time looks good in the Settings display.
[*]... and re-booted
[/LIST]

BUT the Desktop's display on the bottom-right of the whatever-its-called panel continues to display the 24-hour clock.

I then did the same thing and switched to a 24-hour clock.... and re-booted

I then did the same thing and switched to a 12-hour clock.... and re-booted

**Hey! It's now displaying the 12-hour clock!**

I don't recall this being a problem **before** Ubuntu 10.04.1 LTS

---

### Post by owlstead on 2012-10-08
Another method is simply  restarting the panel after setting the right time format in the Locale system settings. Mine crashed, which came in handy, as it automatically restarted. Adding the digital clock widget after that did the trick. This means that logging out and in should work as well. Note that the Locale does say that you need to restart applications, and the panel is simply an application in this regard.

---

### Post by overdrank on 2012-10-08
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

