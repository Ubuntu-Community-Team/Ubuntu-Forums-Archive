---
title: "need a script to pull info from emails"
date: 2009-03-31
forum: General Help
---

### Post by xinix on 2009-03-31
Hi, is there any way I can set up a script to pull info from emails and add it to an Evolution calendar?  When I accept a work assignment I am sent an email from an automated system with the job details.  I'd like to pull the "who, when and where" info and add it to an Evolution calendar so that I can have it sync with my phone at the end of the day.  I'm not really the best at scripts so any help would be greatly appreciated.

Thanks

---

### Post by xinix on 2009-04-01
Just a shameless bump.

---

### Post by xinix on 2009-04-08
Hi,  I've had some success at writing this script.  I'm sure it's not the most graceful and it still needs some work, but, it's a good start.  I've had to search quite a bit for things that I'm sure are fairly simple to do.  I could use some help adding a bit of functionality that I need in the script.
So far I have the emails coming into a directory and a separate file is made for each one (getmail does this).  This script goes through the directory and gets the info I need from the email and adds this to a calendar file(.ics).  Right now I have it confined to a single test file until I can have it do everything it needs to do. Once I have it ready to use on all files that come, I'll add code for it to move the parsed email out and work through all the files in the directory until it's empty. 

Here is an example of the body of the emails I'm scanning:
```
You have been assigned a job starting on 01/23/4567.

The following are the details of the job:

*************
 Job Summary 
*************
Confirmation No.         : 1234567890
Starting on             : 01/23/4567
Place                   : Name Of Place                   
Person                  : Lastname, Firstname


**********
 Job Days 
**********
Place                                             Date     From    To     
--------------------------------------------- -------- ------- -------
Name Of Place                                 01/23/45  8:20AM  3:00PM


Please do not reply to this system generated message.
```

Heres the script:
```
#!/bin/bash

NEWEST=$(ls -lrt | awk '{ f=$NF }; END{ print f }')
TMPNAME=$(awk '/Confirmation No.         :/ {print $4}' $NEWEST)
PLACE=$(awk '/Place                   :/ {print $3,$4,$5,$6,$7}' $NEWEST)
WHO=$(awk '/Person                  :/ {print $4,$5,$3}' $NEWEST)
TITLE=$(awk '/Title                    :/ {print $3,$4,$5,$6,$7}' $NEWEST)
DATE=$(awk "/^$PLACE/ "' {print $(NF-2)}' $NEWEST)
STIME=$(awk "/^$PLACE/ "' {print $(NF-1)}' $NEWEST)
ETIME=$(awk "/^$PLACE/ "' {print $(NF)}' $NEWEST)
DTSTART=$(date --date "$DATE $STIME +5 hours" +"%Y%m%d%H%M%S")
DTEND=$(date --date "$DATE $ETIME +5 hours" +"%Y%m%d%H%M%S")
DSTAMP=$(date --date '+5 hours' +"%Y%m%d%H%M%S")


echo -e "BEGIN:VEVENT\n\
DTSTART:$DTSTART\n\
DTEND:$DTEND\n\
DSTAMP:$DSTAMP\n\
UID:$TMPNAME-Sync-Script\n\
CLASS:PRIVATE\n\
CREATED:$DSTAMP\n\
DESCRIPTION:$TITLE\n\
LAST-MODIFIED:$DSTAMP\n\
LOCATION:$PLACE\n\
SEQUENCE:0\n\
STATUS:CONFIRMED\n\
SUMMARY:$WHO\n\
TRANSP:OPAQUE\n\
BEGIN:VALARM\n\
ACTION:DISPLAY\n\
DESCRIPTION:This is an event reminder\n\
TRIGGER:-P0DT0H30M0S\n\
END:VALARM\n\
END:VEVENT" > $TMPNAME

awk '{if (/END:VCALENDAR/) system("cat '$TMPNAME'"); print}' basic.ics > $TMPNAME.ics

mv $TMPNAME.ics basic.ics
rm $TMPNAME

```This work well (mostly) and leaves me with a file that I can use with my calendar.  I say this works well because normally the email will have only one line like this:
```
Name Of Place                                 01/23/45  8:20AM  3:00PM


```But sometimes there will be more than one, e.g.:
```
Name Of Place                                 01/23/45  8:20AM  3:00PM
Name Of Place                                 01/24/56  8:20AM  3:00PM 

```
The script gets the job date, start and end time from this line and it works well when there is only one line.  

How can I have the script add an entry for each line (day)?

---

