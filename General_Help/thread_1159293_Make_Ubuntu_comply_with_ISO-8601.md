---
title: "Make Ubuntu comply with ISO-8601"
date: 2009-05-14
forum: General Help
---

### Post by paopao on 2009-05-14
I'm running Ubuntu 8.10.

I was wondering if it would be possible to configure the date and time for all programs and displays (or as many as possible) to conform to the ISO-8601 standard, e.g. a datetime would be 2009-05-14 14:47:23.

For example, the clock on the desktop, I can change the time into 24 hour time, but I cannot adjust how the date is displayed.  And more importantly, when I use Open Office, when I use the spreadsheet application, it likes to display my dates in formats like 05/14/09 even if I type in "2009-05-14", it's very upsetting.

In Windows, I was able to go into Language and Regional Settings and configure date and time to be displayed as such and most programs would use that rule.  I'm wondering if Ubuntu has some sort of option somewhere, like a checkbox to check.

Thanks!

---

### Post by mb_webguy on 2009-05-14
Linux tends to be fairly application-specific when it comes to most things.  Gnome apps will use Gnome settings for certain things, but otherwise there aren't many global defaults.

In an OOo spreadsheet, you can change the date format for cells containing a date by selecting the cells and going to Format > Cells.  Select the Date category, then the "1999-12-31" (ISO 8601) format.  You can do something similar in OOo documents when inserting a date.  So far I haven't found a way to set a default date format in OOo.

The Gnome Clock applet is pretty limited as far as setting the date format through its preferences, but you can do it through gconf-editor.  Open gconf-editor and navigate to apps > panel > applets > clock_screen*X* > prefs.  Change the value of "format" to "custom", then set the value of "custom_format" to "%Y-%m-%d %H:%M" to display the date in ISO 8601 format.

---

### Post by njsharp on 2009-06-01
I'm a total fan of 8601 format myself, but feel that simply it should be as easy as W... for all to choose what they prefer.  As a newcomer to U (9.04) though not to L, I too was a bit sad with the difficulties of doing all this, mainly just to get my chosen formats in Thunderbird.  However, sharing some learning, and do remember this is just MY experience in 9.04; your milage may vary:

gconf and the clock applet
=================
Thanks mb-webguy for the tip.  However, my experience was a little different (perhaps due to 9.04) as I had to navigate via gconf-editor to the prefs of 
/apps/panel/applets/applet_1   not    .../clock_screenX

I then used %Y-%b-%d %H:%M:%S to get exactly what I wanted eg 2009-Jun-02 08:04:59.  Seems the applet uses the date command formats.  Nice!

LC_... environment variables
=================
There's lots of stuff on forums here and elsewhere about messing with LANG eg choosing en-DK because you want english as the language but want 8601 dates, so pretend to be in Denmark 'cos they like 8601 too!  Hmm, rather bodgy!  Then you find in calculator that the Danes like '.' to separate thousands and ',' as the decimal 'point'.  Sorry, not for me!!

I investigated messing around with the en-DK file, one of 286 in the not very obvious location /usr/share/i18n/locales (what the heck is i18n?).  This would seem to allow you to alter the settings for the LC_... family of environment variables, most interestingly in this discussion: LC_TIME

In any of those files you will find a section defining LC_TIME in a difficult-to-read U format.  here is one tiny part of LC_TIME in en_DK:

d_fmt    "<U0025><U0059><U002D><U0025><U006D><U002D><U0025><U0064>"

which is really just "%Y:%m:%d" in a format that presumably allows use of any character set, including double bytes (I'm guessing here!).

However, it seems altering a locales file on its own does nothing.  I think you then have to "compile" it with localedef and I didn't fancy that.  Instead I found that the binary versions seem to be in a few folders such as /usr/lib/locale/en_AU.utf8 and each folder contains a binary settings file for each LC_ variable.

So I saved a just-in-case copy of /usr/lib/locale/en_AU.utf8/LC_TIME and replaced it with a copy of /usr/lib/locale/en_DK.utf8/LC_TIME

Very bodgy, but it worked!  Thunderbird now offers me 8601 dates.

Good luck, and if it sends you back to partition, reinstall, you didn't get it from me.

---

### Post by gjw0 on 2010-08-11
> **njsharp said:**
> 
So I saved a just-in-case copy of /usr/lib/locale/en_AU.utf8/LC_TIME and replaced it with a copy of /usr/lib/locale/en_DK.utf8/LC_TIME

Very bodgy, but it worked!

Tried this, but it didn't work for me.I made sure to replace en_AU with en_US, which is what I'm using.

---

