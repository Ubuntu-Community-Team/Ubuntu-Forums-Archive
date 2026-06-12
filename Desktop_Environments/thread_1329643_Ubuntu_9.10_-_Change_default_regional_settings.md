---
title: "Ubuntu 9.10 - Change default regional settings"
date: 2009-11-17
forum: Desktop Environments
---

### Post by bascar on 2009-11-17
Is there any way to change the default regional settings (English-US) in Ubuntu 9.10? I just can't seem to find the option in Gnome...

I'd only like to change the way the date&time is displayed in Evolution and other programs, I don't want to change the UI language for Gnome or any other program.

---

### Post by hellmet on 2009-11-18
Not quite sure I understand what you want, but try
System>Admin>Language.

What's wrong with the current way date&time is displayed?

---

### Post by nolodude on 2009-11-23
Good luck trying to find it. Maybe in Gnome you can't change regional settings at all?

@hellmet: in Evolution Mail, the date & time is currently displayed as "11/11/2009 09:34:17 PM" in the message header. In message list, the same date uses 24H time format (?!?). On the other hand, the date in my desktop panel reads "Mon Nov 23, 20:45".

Now I want every date anywhere in the OS to be in dd.mm.yyyy or yyyy-mm-dd format, and always 24H for the time.

---

### Post by philprett on 2009-12-17
I have been searching for this setting for ages.

I can't believe that this is not possible.

And, the problem with the date in the current format is that it is wrong. I am located in Germany and the time format is dd.mm.yyyy and not mm.dd.yyyy.

Is there no way to change this?

---

### Post by leorolla on 2009-12-21
In KDE its is simple like that...

:(

---

### Post by GeertVc on 2010-04-05
> **philprett said:**
> I have been searching for this setting for ages.

I can't believe that this is not possible.

And, the problem with the date in the current format is that it is wrong. I am located in Germany and the time format is dd.mm.yyyy and not mm.dd.yyyy.

Is there no way to change this?

This maybe?

[LIST]
Select "System | Administration | Time and Date"[/LIST]
[LIST]Click the key (*Click to make changes*) and give your password[/LIST]
[LIST]In the *Time and Date Settings* dialogue box, select the *Time zone*.  You will see a world map with small dots.  Try to locate your region (don't shake too much... :-) )[/LIST]
[LIST]You can also change the *Configuration* from *Manual *to *Keep synchronized with Internet servers*[/LIST]
[LIST]If you select the latter one, chances are that NTP is not installed; the program will propose you to install this.  After installation of NTP, you should choose a time server (eg the one in Mainz, Germany)[/LIST]

This way, since you select your time zone, the way the date is represented, should adhere to your wishes.

Best rgds,
--Geert

---

### Post by leorolla on 2010-04-06
> **GeertVc said:**
> This maybe?

[LIST]
[*]Select "System | Administration | Time and Date"
[/LIST]

[LIST]
[*]Click the key (*Click to make changes*) and give your password
[/LIST]

[LIST]
[*]In the *Time and Date Settings* dialogue box, select the *Time zone*.  You will see a world map with small dots.  Try to locate your region (don't shake too much... :-) )
[/LIST]

[LIST]
[*]You can also change the *Configuration* from *Manual *to *Keep synchronized with Internet servers*
[/LIST]

[LIST]
[*]If you select the latter one, chances are that NTP is not installed; the program will propose you to install this.  After installation of NTP, you should choose a time server (eg the one in Mainz, Germany)
[/LIST]

This way, since you select your time zone, the way the date is represented, should adhere to your wishes.

Best rgds,
--Geert

Your physical location has nothing to do with how you display numbers, dates etc.

---

### Post by lidex on 2010-04-06
Try playing around in "System>Administration>Language Support" on the "Text" tab. Click the "Apply System-Wide" button to set.

---

### Post by leorolla on 2010-04-07
What we want is to change the output of

```

$ locale
LANG=en_US
LC_CTYPE="en_US"
LC_NUMERIC="en_US"
LC_TIME="en_US"
LC_COLLATE="en_US"
LC_MONETARY="en_US"
LC_MESSAGES="en_US"
LC_PAPER="en_US"
LC_NAME="en_US"
LC_ADDRESS="en_US"
LC_TELEPHONE="en_US"
LC_MEASUREMENT="en_US"
LC_IDENTIFICATION="en_US"
LC_ALL=
$ 

```More precisely, we want the LC_TIME variable to change value.

This is not easy with Gnome.

---

### Post by Atilana on 2010-04-07
Good luck trying to find it. Maybe in Gnome you can't change regional  settings at all?

---

### Post by lidex on 2010-04-07
> **leorolla said:**
> What we want is to change the output of

```

$ locale
LANG=en_US
LC_CTYPE="en_US"
LC_NUMERIC="en_US"
LC_TIME="en_US"
LC_COLLATE="en_US"
LC_MONETARY="en_US"
LC_MESSAGES="en_US"
LC_PAPER="en_US"
LC_NAME="en_US"
LC_ADDRESS="en_US"
LC_TELEPHONE="en_US"
LC_MEASUREMENT="en_US"
LC_IDENTIFICATION="en_US"
LC_ALL=
$ 

```More precisely, we want the LC_TIME variable to change value.

This is not easy with Gnome.

See this thread:
[http://ubuntuforums.org/showthread.php?t=1416944]("http://ubuntuforums.org/showthread.php?t=1416944")

---

### Post by kenkaku on 2010-04-08
I actually didn't find this that difficult. I followed this thread:
[http://ubuntuforums.org/showthread.php?t=193916](http://ubuntuforums.org/showthread.php?t=193916)
It worked like a charm for everything except the [expletive deleted] Clock applet. :-/

---

### Post by GeertVc on 2010-06-20
> **leorolla said:**
> Your physical location has nothing to do with how you display numbers, dates etc.
Is it... Strange it's working for me then...

---

### Post by leorolla on 2010-06-21
That is very very strange. I will try my best to reproduce that, but I don't think I can.

So, just bo be sure.
You open "Time and Date", change the "Time Zone" entry, and Nothing Else.
And just after this, your programs like evolution, openoffice etc will change the format for displaying time and date.
Really?!

If this is exactly what happens in your computer, you should even file a bug, because being in New York, London or Rome right now should never ever change the way you have configured date to be displayed.

---

