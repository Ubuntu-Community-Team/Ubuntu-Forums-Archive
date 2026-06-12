---
title: "Birthday Reminder Method/Software Required!"
date: 2009-01-16
forum: General Help
---

### Post by Rytron on 2009-01-16
Hi,
I want a way to receive reminders of peoples birthdays. I considered using Sunbird and Google Calendar. Is there a more simple offline(preferable)/online birthday reminder tool out there? Something that would pop up on the screen every time it was someone's birthday?
Thanks.

---

### Post by jgoguen on 2009-01-16
Does it have to interact with Google Calendar?  If not, Sunbird, Thunderbird with the Lightning extension, or Evolution would all provide offline calendars.  The Evolution calendar database is used by the GNOME calendar so any event reminders (including birthdays) you set up would always display when you're logged in.  For Thunderbird/Lightning and Sunbird, you would have to have the application open to see alerts, but otherwise it's the same idea.

If you need Google Calendar, I've only been able to get it working with Thunderbird/Lightning, but it's supposedly also possible with Evolution.

---

### Post by Rytron on 2009-01-17
I will probably settle for Google Calendar as I have found that it has an email reminder setting. Perfect.

---

### Post by heindsight on 2009-01-17
Well if you want an offline method, you could use cron. Do
```
crontab -e
```

and add a line like:
```

00 9 7 10 * DISPLAY=":0.0" xmessage "heindsight's birthday"

```
which will cause a dialog to pop up with the message "heindsight's birthday" at 9:00 on the seventh of october every year... 

EDIT: of course you could use a different command. for example you could install mailx (sudo apt-get install mailx) and use
```

00 9 7 10 * mail -s birthday YourUsername <<< "Today is heindsight's birthday"

```
this will send a birthday reminder email to your local user account....

---

### Post by Rytron on 2009-01-17
> **jgoguen said:**
> Does it have to interact with Google Calendar?  If not, Sunbird, Thunderbird with the Lightning extension, or Evolution would all provide offline calendars.  The Evolution calendar database is used by the GNOME calendar so any event reminders (including birthdays) you set up would always display when you're logged in.  For Thunderbird/Lightning and Sunbird, you would have to have the application open to see alerts, but otherwise it's the same idea.

If you need Google Calendar, I've only been able to get it working with Thunderbird/Lightning, but it's supposedly also possible with Evolution.

If it is not yet possible to synchronise Google Calendar with Evolution, then a workaround would be to export a Google Calendar as a .ics file and then import this into Evolution(or vice versa).

---

### Post by Rytron on 2009-01-17
I have noticed that when importing the exported Google Calendar .ics file, select the 'On This Computer' option as shown in the attachment. I first selected Birthdays & Anniversaries and the import did not work.

---

### Post by dcstar on 2009-01-17
> **jgoguen said:**
> 
........The Evolution calendar database is used by the GNOME calendar so any event reminders (including birthdays) you set up would always display when you're logged in.
.......

The Evolution Calendar has a major problem where the birth year cannot be before 1974 (or somewhere around then), and that is coded into the program structure and will not ever be changed.

---

### Post by jgoguen on 2009-01-17
Birthdays and Anniversaries is a special calendar that displays the birthdays and anniversaries of your contacts.  To modify its contents you must modify the data for the contacts.  I don't believe you can import to it, add to it, or directly modify events for it.

---

### Post by Rytron on 2009-01-18
> **dcstar said:**
> The Evolution Calendar has a major problem where the birth year cannot be before 1974 (or somewhere around then), and that is coded into the program structure and will not ever be changed.

No birth dates remembered before 1974? Thats very strange.

---

### Post by michaelzap on 2009-01-18
> **Rytron said:**
> If it is not yet possible to synchronise Google Calendar with Evolution...

It is:
[http://www.linux.com/feature/154875](http://www.linux.com/feature/154875)

I don't use Evolution, but I sync it with my Google Calendar anyway so that my gCal events will show up in Gnome.

---

### Post by rsrijith on 2010-01-13
here is a perl script which runs on gnome panel and displays the upcoming birthdays. [http://blog.sriunplugged.com/shell-scripting/birthday-reminder-for-gnome-panel/](http://blog.sriunplugged.com/shell-scripting/birthday-reminder-for-gnome-panel/)

---

### Post by Rodney9 on 2010-01-13
> **heindsight said:**
> Well if you want an offline method, you could use cron. Do
```
crontab -e
```

and add a line like:
```

00 9 7 10 * DISPLAY=":0.0" xmessage "heindsight's birthday"

```
which will cause a dialog to pop up with the message "heindsight's birthday" at 9:00 on the seventh of october every year... 

EDIT: of course you could use a different command. for example you could install mailx (sudo apt-get install mailx) and use
```

00 9 7 10 * mail -s birthday YourUsername <<< "Today is heindsight's birthday"

```
this will send a birthday reminder email to your local user account....

When I use ```
crontab -e
``` I get the following in nano

0 * * * * ~/speak_time # JOB_ID_4
30 * * * * ~/speak_time # JOB_ID_5
@daily nice -n 19 /usr/bin/backintime --backup-job >/dev/null 2>&1

where do I place ```
00 9 7 10 * DISPLAY=":0.0" xmessage "heindsight's birthday"
```

---

### Post by Rytron on 2010-01-14
Thank you rsrijith. I appreciate it.

---

