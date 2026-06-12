---
title: "configuring provider for google calendar"
date: 2009-04-07
forum: General Help
---

### Post by thundaraptor on 2009-04-07
I need help on configuring provider for google calender to work in thunderbird/lightning  thanks

---

### Post by Irvine_himself on 2010-01-18
I have been struggling with this problem for a couple of day's and since this post has turned up fairly regularly in my Google searches, I am going to use it to document the big mistake that I, and I suspect a lot of other people, have been making.

Having recently migrated from Windows, I was fairly comfortable with Thunderbird, Lightning and pop3. Unfortunately, the TB version in the repos was a bit buggy, [the new events tab was not working,] so I tried Evolution and found that the imap thingy did not display downloaded messages. Finally, I downloaded TB3 direct from Mozilla and installed the most recent Lightening add-on. Success, real bliss!

In a fit of euphoria, I decided to sync my desktop calender with my Google calender. A quick search of the add-ons revealed the "Google Provider" add-on. If you search the posts in this forum, you will find that, like me, a lot of people have had problems with this add-on. After much tweaking, I managed to get a one way sync going from Google to my desktop. Not much use!

The next step was to try GCALDaemon. This involves an intimidating traditional installation with configuration files and all of the other things that are frightening about Linux, but I got it working........ problem, the sync is still only one way! 

At this point I was really getting ready to scream.

So making sure that GProvider and GCALDaemon were both un-installed, the next on the list was to try CalDav, it is built into TB3 and hence no add-ons or external installations were needed. Very good, I like this. 

Following the instructions for Sunbird at  [http://www.google.com/support/calendar/bin/answer.py?answer=99358#sunbird](http://www.google.com/support/calendar/bin/answer.py?answer=99358#sunbird) worked like a dream.... really easy....  no problems....     

Yeeks!   still only a one way sync.


What was going on here:

1/ "Google" calender  on-line was being picked up by my "Home" calender.

2/ "Home" calender was  picked up by the "Google" calender in TB3.

3/ "Home" calender in TB3 was  [SIZE=1][COLOR=black]_**not!**_[/COLOR][/SIZE]  picked up by the "Google" calender on-line.

Here is the mistake that I made:-  I had defined  two calendars in TB3, "Home" and "Google" they are different. While what is entered into "Home" appears in "Google" TB3 it has not been entered or saved and will not sync with "Google" on-line.

To get everything working beautifully:-    (I recommend using CalDav, it is built in to TB3 and does not involve third party apps or add-ons, but the choice is yours.) Once you have the one-way sync from "Google" on-line to "Google" TB3, export the "Home" calender from TB3 and re-import it to the "Google" calender in TB3. It sounds really stupid and is not obvious, but believe me, this will then sync nicely with "Google" on-line, from where it can be synced with a compatible cellphone, PDA, Laptop or whatever.

Finally, for neatness and to avoid confusion, right click on the "Home" calender button and either hide or delete the "Home" calender.

I hope this helps other people that are having problems with this.

Irvine

:o

---

