---
title: "Date format in Pangolin changeable?"
date: 2012-05-05
forum: Desktop Environments
---

### Post by reedk on 2012-05-05
I can't find where to change the date format in Pangolin. I'd like to do this system-wide, but it's most noticeable in apps like Thunderbird. Instead of the date I'm comfortable with - 12/31/2011, I get a format more like 11-12-31. I see it the same way in "Time & Date Settings." I see the logic, but I don't like it.

Is there a way to change this presentation? Preferably system-wide.

---

### Post by grahammechanical on 2012-05-05
In my Time and Date settings I see 05/05/12. Even when I change the location from London to somewhere in the USA the time changes but the date format says the same - 05/05/12. If I move in the other direction, the day will change but not the format - 06/05/12

Regards.

---

### Post by reedk on 2012-05-05
That helps a lot. Thanks. I noticed that after install that my Location was set to Toronto, which likely uses a different format. Based on your comment, it sounds like the format gets defined once during setup regardless of later Location changes. Once I find that, I can change it system-wide. I'll poke around settings, gconf, and the Internet for that and post any fixes or observations. Thanks again.

---

### Post by reedk on 2012-05-05
Fixed. Like I saw, it's not that Linux is perfect, it's that the problems you have are fixable.

For everyone else, this appears to be related to picking a bad locale during install.

I found that date format is controlled by the environment variable LC_TIME.Issuing the command *locale*, I see:

```
LANG=en_CA.UTF-8
LANGUAGE=en_CA:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8

```

So my language is set to Canadian English!

To fix it, I edited /etc/default/locale to change both instances of "CA" with "US". I then regenerated the locales, for the sake of completeness, with *sudo locale-gen*. I then rebooted and the date was set to my familiar format. One note, the system did ask to correct the locale format on a couple directories, and I allowed it to do so. I noticed no impact from that.

Sources:
[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
[https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

---

### Post by grahammechanical on 2012-05-06
I am glad you found a fix. I also thougnt of another solution but I have been doling other things for most of the day.

In System Settings the Language Support utility has a Region Formats tab where you can set various kinds of English regional formats which in turn affects the display of numbers, dates and currency amounts. And it can be applied system wide.

So, that would be the "official" way of doing it in Precise Pangolin.

Regards.

---

### Post by rewyllys on 2012-05-07
> **grahammechanical said:**
> I am glad you found a fix. I also thougnt of another solution but I have been doling other things for most of the day.

In System Settings the Language Support utility has a Region Formats tab where you can set various kinds of English regional formats which in turn affects the display of numbers, dates and currency amounts. And it can be applied system wide.

So, that would be the "official" way of doing it in Precise Pangolin.

Regards.
Thanks, Graham. I've changed my settings in System Settings.  This works in most places, but Thunderbird continues to ignore my settings.  

Can you or anyone suggest how to get Thunderbird to show times using the 24-hour clock?

Thanks in advance for any help.

---

### Post by fbicknel on 2012-06-20
Here's what I did.  It is admittedly draconian, but I want everything on my system to use 24-hour time and to use Monday as day 1 of the week.

So I modified en_US rather than my LC_ locale settings.  Here's how:
```

bick-ubtu3:/usr/share/i18n/locales$ diff en_US.orig en_US
85c85
< first_weekday 1
---
> first_weekday 2
106,107c106,108
< %     "%a %d %b %Y %r %Z"
< d_t_fmt "<U0025><U0061><U0020><U0025><U0064><U0020><U0025><U0062><U0020><U0025><U0059><U0020><U0025><U0072><U0020><U0025><U005A>"
---
> %     "%a %d %b %Y %r %Z" 12-hour + am/pm notation
> %     "%a %d %b %Y %T %Z" 24-hour notation
> d_t_fmt "<U0025><U0061><U0020><U0025><U0064><U0020><U0025><U0062><U0020><U0025><U0059><U0020><U0025><U0054><U0020><U0025><U005A>"
114,115c115,117
< %     "%r"
< t_fmt   "<U0025><U0072>"
---
> %     "%r" - 12 hour am/pm notation
> %     "%T" - 24 hour notation
> t_fmt   "<U0025><U0054>"

```The unicode makes it scary looking, but essentially there are two changes made:
 - Change the first_weekday from 1 to 2
 - For d_t_fmt and for t_fmt, change the %r format parameter to %T

%r represents a 12-hour AM/PM format, %T is a 24-hour time format.

The <U0072> (r) is changed to <U0054> (T) to effect this change.

After that, I just ran:
    sudo localedef -f UTF-8 -i en_US en_US.UTF-8

and restarted Thunderbird.  

I'm probably going to find this file overwritten one day with the original.  I expect some routine update will do this "for" me.  So I made a copy of the modified file, as well.  If that happens often, I'll probably relent and do it the "right" way.  My plan:

  - create a new custom locale setting (eu_US) that matches the mods above
  - compile that as above
  - set my locale environment variables to eu_US

(almost there... just two beans to go!)

---

