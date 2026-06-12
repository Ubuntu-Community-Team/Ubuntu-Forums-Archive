---
title: "Fluxbox - howto config bottom bar"
date: 2007-09-12
forum: Desktop Environments
---

### Post by satimis on 2007-09-12
Hi folks,


Ubuntu 7.04 server amd64
Fluxbox desktop manager


About time and date

date is not displayed on the bottom bar and time displayed as 08:35 (12h) without am/pm.


Pls advise how to display date on the bottom bar and add am/pm on time displayed.  TIA


B.R.
satimis

---

### Post by kellemes on 2007-09-12
Sorry I can't help, I'm not using Fluxbox anymore..
But have you searched [the wiki]("http://fluxbox-wiki.org/index.php/Fluxbox-wiki")?

---

### Post by mojoman on 2007-09-12
What you need to do is to edit your ~./fluxbox/init file

There is a line called:
session.screen0.toolbar.tools:

This says what should be shown in the toolbar and clock is, I think, mentioned there  (I think it's this line but I removed mine as conky displays time for me). Anyway, this is not the line to edit but the following line: 

session.screen0.strftimeFormat:	%k:%M

determines how your clock should be displayed (in this case its 24 hour clock and minute).

Now, open up a terminal and type:

man date

and read up on the multitude of different ways to display time and date. Once you find something you like, you just edit the %k:%M to the code for whatever is your preference.

The configurability of Fluxbox is simply awesome....
/mojoman

---

### Post by satimis on 2007-09-12
Hi mojoman,


Tks for your advice.

> 
session.screen0.strftimeFormat:	%k:%M

Right-click "Clock" on bottom bar starts "Edit Clock Format"

```

%k:%M

```

I can edit there.  But I have no idea how to do it.  Besides I can't exit/close it.  I have to exit X to do the job.


> 
determines how your clock should be displayed (in this case its 24 hour clock and minute).

Now, open up a terminal and type:

man date

On Terminal

$ date```

Wed Sep 12 23:05:04 PDT 2007

```
date and time is correct.

> 
and read up on the multitude of different ways to display time and date. Once you find something you like, you just edit the %k:%M to the code for whatever is your preference.
Whether adding;```

%c"Wed Sep 12 23:05:04 2007"

```

If 12h, how to add "am/pm"?

TIA


B.R.
satimis

---

### Post by thatswhatshesaid on 2007-09-12
I'm not on my Flux box right now but If I'm not mistaken the ```
%k:%M
``` come from the available date command formats.  Open a terminal and type ```
date --help
``` for all the possible values and then you can change them where you see "%k:%M" in the UI.

I would guess that ```
%k:%M%p
``` would work the way you desire.

---

### Post by mojoman on 2007-09-12
I said to type "man date", not "date". The manfile shows the following options for date:

```
 %a   locale's abbreviated weekday name (e.g., Sun)
  %A   locale's full weekday name (e.g., Sunday)
  %b   locale's abbreviated month name (e.g., Jan)
  %B   locale's full month name (e.g., January)
  %c   locale's date and time (e.g., Thu Mar  3 23:05:25 2005)
  %C   century; like %Y, except omit last two digits (e.g., 21)
  %d   day of month (e.g, 01)
  %D   date; same as %m/%d/%y
  %e   day of month, space padded; same as %_d
  %F   full date; same as %Y-%m-%d
  %g   last two digits of year of ISO week number (see %G)
  %G   year of ISO week number (see %V); normally useful only with %V
  %h   same as %b
  %H   hour (00..23)
  %I   hour (01..12)
  %j   day of year (001..366)
  %k   hour ( 0..23)
  %l   hour ( 1..12)
  %m   month (01..12)
  %M   minute (00..59)
  %n   a newline
  %N   nanoseconds (000000000..999999999)
  %p   locale's equivalent of either AM or PM; blank if not known
  %P   like %p, but lower case
  %r   locale's 12-hour clock time (e.g., 11:11:04 PM)
  %R   24-hour hour and minute; same as %H:%M
  %s   seconds since 1970-01-01 00:00:00 UTC
  %S   second (00..60)
  %t   a tab
  %T   time; same as %H:%M:%S
  %u   day of week (1..7); 1 is Monday
  %U   week number of year, with Sunday as first day of week (00..53)
  %V   ISO week number, with Monday as first day of week (01..53)
  %w   day of week (0..6); 0 is Sunday
  %W   week number of year, with Monday as first day of week (00..53)
  %x   locale's date representation (e.g., 12/31/99)
  %X   locale's time representation (e.g., 23:13:48)
  %y   last two digits of year (00..99)
  %Y   year
  %z   +hhmm numeric timezone (e.g., -0400)
  %:z  +hh:mm numeric timezone (e.g., -04:00)
  %::z  +hh:mm:ss numeric time zone (e.g., -04:00:00)
  %:::z  numeric time zone with : to necessary precision (e.g., -04, +05:30)
  %Z   alphabetic time zone abbreviation (e.g., EDT)
```

See which alternative, or combination of alternatives, that you want to be displayed. When you know what you want, I'd rather just open the configuration file with an editor. 

```
mousepad ~/.fluxbox/init
```
(There are other editors if you don't like mousepad)

Go to the file that I mentioned earlier and substitute the code. For example:

```
session.screen0.strftimeFormat: %c
```
would show your locale date and time in the format weekday month date hour minute second year.

```
session.screen0.strftimeFormat: %F %R 
```
would show full date and full time.

/mojoman

---

### Post by RedSquirrel on 2007-09-12
> **satimis said:**
> Right-click "Clock" on bottom bar starts "Edit Clock Format"

```

%k:%M

```I can edit there.  But I have no idea how to do it.  Besides I can't exit/close it.  I have to exit X to do the job.

The "Edit Clock Format" is just a mini text editor. There is a cursor in there and you can press Backspace, Delete, and so on. When you are done editing just press **Enter**.



> **satimis said:**
>  Whether adding;```

%c"Wed Sep 12 23:05:04 2007"

```If 12h, how to add "am/pm"?

If you replace the original format (%k:%M) with the format code **%c**, it will display something like "Wed 12 Sep 2007 23:05:04 PDT" (depending on your locale setting).

All of the format codes are listed in the date man page, as mentioned above, e.g., 

```
%A, %B %e %l:%M %P %Z
```

---

### Post by kerry_s on 2007-09-12
Right-click "Clock" on bottom bar starts "Edit Clock Format"
put
%l:%M %a %b %d
and hit enter

---

### Post by s26c.sayan on 2007-09-12
> **kerry_s said:**
> Right-click "Clock" on bottom bar starts "Edit Clock Format"
put
%l:%M %a %b %d
and hit enter

.......and  press ESC if you don't want to preserve the changes!

---

### Post by satimis on 2007-09-12
> **thatswhatshesaid said:**
> I'm not on my Flux box right now but If I'm not mistaken the ```
%k:%M
``` come from the available date command formats.  Open a terminal and type ```
date --help
``` for all the possible values and then you can change them where you see "%k:%M" in the UI.

I would guess that ```
%k:%M%p
``` would work the way you desire.
Tks for your advice.

%k:%M %a %e %b %Y
works for me displaying "23:50 Wed 12 Sep 2007"

[Enter] closes the box


How to add "am/pm" for 12h?


B.R.
satimis

---

### Post by RedSquirrel on 2007-09-12
%p => AM/PM
%P => am/pm

---

### Post by satimis on 2007-09-13
> **RedSquirrel said:**
> %p => AM/PM
%P => am/pm
I got it.  Tks.


satimis

---

### Post by satimis on 2007-09-13
> **thatswhatshesaid said:**
> I'm not on my Flux box right now but If I'm not mistaken the ```
%k:%M
``` come from the available date command formats.  Open a terminal and type ```
date --help
``` for all the possible values and then you can change them where you see "%k:%M" in the UI.

I would guess that ```
%k:%M%p
``` would work the way you desire.
Noted with tks.


B.R.
satimis

---

### Post by satimis on 2007-09-13
> **mojoman said:**
> I said to type "man date", not "date". The manfile shows the following options for date:

```
 %a   locale's abbreviated weekday name (e.g., Sun)
  %A   locale's full weekday name (e.g., Sunday)
  %b   locale's abbreviated month name (e.g., Jan)
  %B   locale's full month name (e.g., January)
  %c   locale's date and time (e.g., Thu Mar  3 23:05:25 2005)
  %C   century; like %Y, except omit last two digits (e.g., 21)
  %d   day of month (e.g, 01)
  %D   date; same as %m/%d/%y
  %e   day of month, space padded; same as %_d
  %F   full date; same as %Y-%m-%d
  %g   last two digits of year of ISO week number (see %G)
  %G   year of ISO week number (see %V); normally useful only with %V
  %h   same as %b
  %H   hour (00..23)
  %I   hour (01..12)
  %j   day of year (001..366)
  %k   hour ( 0..23)
  %l   hour ( 1..12)
  %m   month (01..12)
  %M   minute (00..59)
  %n   a newline
  %N   nanoseconds (000000000..999999999)
  %p   locale's equivalent of either AM or PM; blank if not known
  %P   like %p, but lower case
  %r   locale's 12-hour clock time (e.g., 11:11:04 PM)
  %R   24-hour hour and minute; same as %H:%M
  %s   seconds since 1970-01-01 00:00:00 UTC
  %S   second (00..60)
  %t   a tab
  %T   time; same as %H:%M:%S
  %u   day of week (1..7); 1 is Monday
  %U   week number of year, with Sunday as first day of week (00..53)
  %V   ISO week number, with Monday as first day of week (01..53)
  %w   day of week (0..6); 0 is Sunday
  %W   week number of year, with Monday as first day of week (00..53)
  %x   locale's date representation (e.g., 12/31/99)
  %X   locale's time representation (e.g., 23:13:48)
  %y   last two digits of year (00..99)
  %Y   year
  %z   +hhmm numeric timezone (e.g., -0400)
  %:z  +hh:mm numeric timezone (e.g., -04:00)
  %::z  +hh:mm:ss numeric time zone (e.g., -04:00:00)
  %:::z  numeric time zone with : to necessary precision (e.g., -04, +05:30)
  %Z   alphabetic time zone abbreviation (e.g., EDT)
```

See which alternative, or combination of alternatives, that you want to be displayed. When you know what you want, I'd rather just open the configuration file with an editor. 

```
mousepad ~/.fluxbox/init
```
(There are other editors if you don't like mousepad)

Go to the file that I mentioned earlier and substitute the code. For example:

```
session.screen0.strftimeFormat: %c
```
would show your locale date and time in the format weekday month date hour minute second year.

```
session.screen0.strftimeFormat: %F %R 
```
would show full date and full time.

/mojoman

Noted with tks


B.R.
satimis

---

