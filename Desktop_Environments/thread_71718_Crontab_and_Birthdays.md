---
title: "Crontab and Birthdays"
date: 2005-10-04
forum: Desktop Environments
---

### Post by gobfrey on 2005-10-04
Hi
I want to set up automatic emails when the birthdays of my family approach.  I'm a continent or so away from them, so I want to get a 'one month' reminder and then a 'two week reminder'.  I want to use crontab for this, but I'm extremely new to this and there are a couple of questions I have:

1)  If I set up a reminder to send me an email on (e.g.) January 1st for my Mother's birthday on February 1st, but I happen to be away from home for a few days, will the email still get sent when I turn on my computer on January 5th?

2)  My wife is Korean, and her birthday is calculated by the lunar calander:  It's a different (solar) day every year.  How can I work under these conditions?  Crontab doesn't seem to support the Lunar calander.  Is there a program which will convert the date each year and insert them into crontab (automaticaly)?

A little help from a guru would be appreciated.

Adam

Windows->Suse->Windows->Fedora->Windows->Ubuntu and Happy.

---

### Post by simon w on 2005-10-04
1)
Cron doesn't care about missed entries in crontab.  Used have to use Anacron for that.

2) Sorry, can't help here.

---

### Post by KingBahamut on 2005-10-04
1. See first post. 

2. Not without some fancy footwork.

---

### Post by gobfrey on 2005-10-04
OK, helpful in a very vague way.

1)  Do we not have anacron any more.  If this does care about missed entries why don't we have it and how can I get it back?  Failing that, I could write my own script that will look at a list of birthdays, run periodically and send emails, but I would have thought a script like that already exists.

2)  What precisely is the fancy footword one would need to do to get lunar calander entries working?  Could I write a perl script that is called from crontab that converts dates and writes a new entry back into crontab every year?  Does anyone know what the algorithm is for converting between the dates?

Linux is a powerful operating system, and I refuse to believe there isn't a relatively simple way of doing this, even if it is a case of installing a lightweight program to do it.

Somebody please give me some more specific and in-depth help.

Adam

---

### Post by Zwack on 2005-10-04
Yes, Anacron is in Hoary at least...  

Synaptic will allow you to install that.

As for your Fancy footwork, I've never tried to convert from one calendar to another, so I'll just say that if you get the conversion sorted out, you might want to consider a script run from At instead.  It can be run once to insert itself into at and then automatically insert itself every time that it runs...

Of course you may prefer just to run the script daily from anacron and have it keep track of when it has emailed you.

I hope that this helps...

Z.

---

### Post by gobfrey on 2005-10-05
I'm sorry if this is a silly question, but what's At?

Adam

---

### Post by 3david on 2005-10-24
that's an interesting idea for a reminder script, i'll write it once i have some time (hopefully soon),

What i would do is write a script (in python maybe) that would be run once a day or so using crontab, and each time the script is run it will count the days until each event in a list of events, and when the amount of days it two weeks or a month or whatever it will notify you by a pop-up or email or something.

This could be a useful script to have, i'll let you know when i write it.

---

### Post by kailden on 2008-04-09
Replying very late to this...but...I think 'remind' would be a good program to do what you want.
see: [this article]("http://www.linuxjournal.com/article/3529").  It can handle phases of the moon and other very advanced calculations.

---

