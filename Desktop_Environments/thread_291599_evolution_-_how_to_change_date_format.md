---
title: "evolution - how to change date format?"
date: 2006-11-02
forum: Desktop Environments
---

### Post by kxs on 2006-11-02
How to change date format in evolution? It`s set to: 15 mar 13:00 for example as I want : 2006-03-15 13:00
I don`t have a clue how to do it, can`t find change date format option anywhere inside evolution

---

### Post by dcstar on 2006-11-04
> **kxs said:**
> How to change date format in evolution? It`s set to: 15 mar 13:00 for example as I want : 2006-03-15 13:00
I don`t have a clue how to do it, can`t find change date format option anywhere inside evolution

I believe all date/time formats are taken from your system's locale settings (not 100% sure, but reasonably so).

---

### Post by kxs on 2006-11-04
and how to change system date format?

---

### Post by exmatelot853 on 2006-11-04
Try this,

Log out of your session and at the "login" screen select "options", "select language".

From the drop down window select the language you want and then select "change language".

Now login as normal, it will then ask if you want to make your language selection default or session only, select "default".

Now your system date format will be correct and so will evolution or thunderbird etc.:) 

Hope this helps.

exmatelot853

---

### Post by kxs on 2006-11-04
No, that`s not it. I`ve got date format set to "sob lis  4 12:06:42 CET 2006", so it`s polish date format as set in locale:
```
LANG=pl_PL.UTF-8
LANGUAGE=pl_PL.UTF-8
LC_CTYPE="pl_PL.UTF-8"
LC_NUMERIC="pl_PL.UTF-8"
LC_TIME="pl_PL.UTF-8"
LC_COLLATE="pl_PL.UTF-8"
LC_MONETARY="pl_PL.UTF-8"
LC_MESSAGES="pl_PL.UTF-8"
LC_PAPER="pl_PL.UTF-8"
LC_NAME="pl_PL.UTF-8"
LC_ADDRESS="pl_PL.UTF-8"
LC_TELEPHONE="pl_PL.UTF-8"
LC_MEASUREMENT="pl_PL.UTF-8"
LC_IDENTIFICATION="pl_PL.UTF-8"
LC_ALL=

```
I want to leave locales as they are except for the date format. I want to use this one: 2006-11-04 12:06:42
How and what should I change?

man, such things should be a lot easier in the 21st century

---

### Post by exmatelot853 on 2006-11-04
Ok how about this then, this will custom format your time and date display in your task bar but I'm not sure it will alter evolution (I don't use it).

Select "Applications", "System Tools", "Configuration Editor"

Select "apps", "panel", "applets", "clock_screen0", "prefs"

In the right hand panel double click "custom_format" and to get the display you want type **%F %T** in the box and click "OK"

then double click "format" and type **custom** in the box and click "OK"

this will display system date as 2006-11-04 and system time as 14:29:03 for example.

Here's a list of the variables below.


%a     locale's abbreviated weekday name (Sun..Sat)

       %A     locale's full weekday name, variable length (Sunday..Saturday)

       %b     locale's abbreviated month name (Jan..Dec)

       %B     locale's full month name, variable length (January..December)

       %c     locale's date and time (Sat Nov 04 12:02:33 EST 1989)

       %C     century  (year  divided  by  100	and  truncated	to an integer)
	      [00-99]

       %d     day of month (01..31)

       %D     date (mm/dd/yy)

       %e     day of month, blank padded ( 1..31)

       %F     same as %Y-%m-%d

       %g     the 2-digit year corresponding to the %V week number

       %G     the 4-digit year corresponding to the %V week number

       %h     same as %b

       %H     hour (00..23)

       %I     hour (01..12)

       %j     day of year (001..366)

       %k     hour ( 0..23)

       %l     hour ( 1..12)

       %m     month (01..12)

       %M     minute (00..59)

       %n     a newline

       %N     nanoseconds (000000000..999999999)

       %p     locale's upper case AM or PM indicator (blank in many locales)

       %P     locale's lower case am or pm indicator (blank in many locales)

       %r     time, 12-hour (hh:mm:ss [AP]M)

       %R     time, 24-hour (hh:mm)

       %s     seconds since `00:00:00 1970-01-01 UTC' (a GNU extension)

       %S     second (00..60); the 60 is necessary to accommodate a leap  sec-
	      ond

       %t     a horizontal tab

       %T     time, 24-hour (hh:mm:ss)

       %u     day of week (1..7);  1 represents Monday

       %U     week number of year with Sunday as first day of week (00..53)

       %V     week number of year with Monday as first day of week (01..53)

       %w     day of week (0..6);  0 represents Sunday

       %W     week number of year with Monday as first day of week (00..53)

       %x     locale's date representation (mm/dd/yy)

       %X     locale's time representation (%H:%M:%S)

       %y     last two digits of year (00..99)

       %Y     year (1970...)

       %z     RFC-822 style numeric timezone (-0500) (a nonstandard extension)

       %Z     time zone (e.g., EDT), or nothing if  no	time  zone  is	deter-
	      minable

       By  default, date pads numeric fields with zeroes.  GNU date recognizes
       the following modifiers between `%' and a numeric directive.

	      `-' (hyphen) do not pad the field `_' (underscore) pad the field
	      with spaces

Hope this helps.:-k 

exmatelot853

---

### Post by kxs on 2006-11-04
Thanks for trying to help, but that`s not it either. I`ve managed to change my system date format, that means if I run "date" command in console I get the date as I want, that is: 2006-11-04 18:03:05, but that unfortunately that doesn`t affect GNOME. It seems that it has it`s independent date format somewhere. The only question is where isi it and how to change it.

---

### Post by gdallosto on 2008-01-09
How can I use this information with Ubuntu 7.10????

I am NEW user of Linux/Ubuntu


Thanks.......... 



> **exmatelot853 said:**
> Ok how about this then, this will custom format your time and date display in your task bar but I'm not sure it will alter evolution (I don't use it).

Select "Applications", "System Tools", "Configuration Editor"

Select "apps", "panel", "applets", "clock_screen0", "prefs"

In the right hand panel double click "custom_format" and to get the display you want type **%F %T** in the box and click "OK"

then double click "format" and type **custom** in the box and click "OK"

this will display system date as 2006-11-04 and system time as 14:29:03 for example.

Here's a list of the variables below.


%a     locale's abbreviated weekday name (Sun..Sat)

       %A     locale's full weekday name, variable length (Sunday..Saturday)

       %b     locale's abbreviated month name (Jan..Dec)

       %B     locale's full month name, variable length (January..December)

       %c     locale's date and time (Sat Nov 04 12:02:33 EST 1989)

       %C     century  (year  divided  by  100	and  truncated	to an integer)
	      [00-99]

       %d     day of month (01..31)

       %D     date (mm/dd/yy)

       %e     day of month, blank padded ( 1..31)

       %F     same as %Y-%m-%d

       %g     the 2-digit year corresponding to the %V week number

       %G     the 4-digit year corresponding to the %V week number

       %h     same as %b

       %H     hour (00..23)

       %I     hour (01..12)

       %j     day of year (001..366)

       %k     hour ( 0..23)

       %l     hour ( 1..12)

       %m     month (01..12)

       %M     minute (00..59)

       %n     a newline

       %N     nanoseconds (000000000..999999999)

       %p     locale's upper case AM or PM indicator (blank in many locales)

       %P     locale's lower case am or pm indicator (blank in many locales)

       %r     time, 12-hour (hh:mm:ss [AP]M)

       %R     time, 24-hour (hh:mm)

       %s     seconds since `00:00:00 1970-01-01 UTC' (a GNU extension)

       %S     second (00..60); the 60 is necessary to accommodate a leap  sec-
	      ond

       %t     a horizontal tab

       %T     time, 24-hour (hh:mm:ss)

       %u     day of week (1..7);  1 represents Monday

       %U     week number of year with Sunday as first day of week (00..53)

       %V     week number of year with Monday as first day of week (01..53)

       %w     day of week (0..6);  0 represents Sunday

       %W     week number of year with Monday as first day of week (00..53)

       %x     locale's date representation (mm/dd/yy)

       %X     locale's time representation (%H:%M:%S)

       %y     last two digits of year (00..99)

       %Y     year (1970...)

       %z     RFC-822 style numeric timezone (-0500) (a nonstandard extension)

       %Z     time zone (e.g., EDT), or nothing if  no	time  zone  is	deter-
	      minable

       By  default, date pads numeric fields with zeroes.  GNU date recognizes
       the following modifiers between `%' and a numeric directive.

	      `-' (hyphen) do not pad the field `_' (underscore) pad the field
	      with spaces

Hope this helps.:-k 

exmatelot853

---

### Post by josef.sabl on 2008-03-11
> **kxs said:**
> Thanks for trying to help, but that`s not it either. I`ve managed to change my system date format, that means if I run "date" command in console I get the date as I want, that is: 2006-11-04 18:03:05, but that unfortunately that doesn`t affect GNOME. It seems that it has it`s independent date format somewhere. The only question is where isi it and how to change it.

Is this resolved already? It still bugs me in Gutsy. I have (and I want) US locale set, but I want dates and times displayed in European way. That is 24h format and not that confusing MM/DD/YYYY format. Is there a way to do it please?

Thanks.

---

### Post by locky28 on 2008-03-11
> **exmatelot853 said:**
> Try this,

Log out of your session and at the "login" screen select "options", "select language".

From the drop down window select the language you want and then select "change language".

Now login as normal, it will then ask if you want to make your language selection default or session only, select "default".

Now your system date format will be correct and so will evolution or thunderbird etc.:) 

Hope this helps.

exmatelot853

I think this has worked for me, I'm behind a proxy atm so I can't test it by pulling in a new email but all my old ones seem to have the correct date.

I'll get back to you.

---

### Post by locky28 on 2008-03-12
No luck, I'm playing around with different timezones instead.

---

### Post by jpka on 2008-06-18
Hello,
After years, same problem with Evolution exist, and I not find way to solve...
I experiment with locales, and almost solve this:
 ls -l, now shows 2008-06-09 16:44 but I need '09.06.2008' date, I can't find solution.
 nautilus filemanager, the same thing.
 panel's system clock, now shows '&#1057;&#1088;&#1077;&#1076;&#1072; &#1048;&#1102;&#1085;&#1100; 18' but I need '09.06.2008' date, I can't find solution.
 and finally, Evolution, never change displayed format while I change locales. Furthermore, it displayed not in a fixed format: today's mail shown without date, yesterday's - with word 'yesterday' at a place of date, and earlier - like '&#1055;&#1085;&#1076;', more than week old - like '&#1048;&#1102;&#1085; 10'. 
This looks not like any 'locale' and because of this, 'locale's can't helpful here.
I need only and only one format - like '09.06.2008' always and everywhere.
Without this, my Hardy is not very usable. :(

I do not know C/C++ language and thus can't correct source code.
Is there exists a brave guys which can do this?

PS. My native locale is ru_RU.UTF8, but all system messages, menus etc. must be (and fortunately is) in English.

Thanks a lot!

---

