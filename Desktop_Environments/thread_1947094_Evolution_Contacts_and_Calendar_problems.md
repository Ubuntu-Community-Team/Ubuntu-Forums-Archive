---
title: "Evolution Contacts and Calendar problems"
date: 2012-03-26
forum: Desktop Environments
---

### Post by Jonners59 on 2012-03-26
My Evolution has problems with both calendar and Contacts.

I have my Calendar accounts set up, but it refuses to add meetings/events directly, saying the account does not exist, however if I create them in my gmail account via my web browser, they sync up and appear in Evolution.

One error message I get get is:
```
Unable to book a resource, error: No such interface `org.gnome.evolution.dataserver.Calendar' on object at path /org/gnome/evolution/dataserver/Calendar/2293/294
```
Does thsi help in any way?

Contacts is even worse.
I have accounts created, but the contents are empty.  I then try and delete the account and start again, but it refuses to allow me to.

Screenshot attached.

---

### Post by arnouf on 2012-03-26
Same issue here !
I tried a lot of stuff and always the same message calendar doesn't exist !
So if you have a way to solve this issue, let me know

---

### Post by nmyrick on 2012-04-01
Do you have Google Plus accounts?  I don't use my calendar much in evolution (I add appointments through my Droid) but I just noticed this issue, and realized that I switched to Google Plus since the last time I tried to add an appointment in Evolution.

I think this may be a compatibility issue with Google Plus and Evolution.

---

### Post by Jonners59 on 2012-04-03
> **nmyrick said:**
> Do you have Google Plus accounts? 

How do I know?

---

### Post by nmyrick on 2012-04-10
You would have had to set up a Google plus account.  It's like Googles version of Facebook.

---

### Post by Jonners59 on 2012-04-11
> **nmyrick said:**
> You would have had to set up a Google plus account.  It's like Googles version of Facebook.
Yup, I am now with you, and yes, I do....  But, this problem has been going on far longer than since I started using Google+, which is a matter of a couple of months.  This problem started in 10.04 and has not been resolved.  See previous Threads I raised a year back.

It has got better.  I can view Calendar and it does update, and eMail does not lock up, BUT I can not add events - I can but they do not want to save saying that the calendar does not exist,  so I have to "discard" the calendar entry, but it appears in my Google on-line account which then syncs with Evolution - CRAZY:confused:

Address book just simply does not work.

I have raised with Evolution directly, but they never respond or do anything.

I am not sure anyone really gives a toot as this has been such a long outstanding issue and I have had jip in terms of support or responses.  Searching the web I am not alone.

---

### Post by jernst on 2012-04-11
I have reported this bug here : [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/978728](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/978728)

Did any of you report it upstream too ?

---

### Post by Jonners59 on 2012-04-11
> **jernst said:**
> I have reported this bug here : [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/978728](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/978728)

Did any of you report it upstream too ?
Oh, yes.  I have raised more than one thread here and contributed to others that have had the same symptoms, I have raised a few bug reports and I have contacted the Evolution team via their support/website.  Nothing on any.

As I say it started in 10.04 and has not been resolved.  I have the same issue on 7 machines (new, old, 32 and 64-bit, PC, or laptop) with all Google hosted accounts.

Never had a reply.

---

### Post by jernst on 2012-04-13
I've reported the bug upstream[1] and it has been fixed the next day !

The fix will be released in the next releases of evolution-data-server ; let's hope it'll be integrated soon in current Ubuntu releases.

[1] [https://bugzilla.gnome.org/show_bug.cgi?id=673894](https://bugzilla.gnome.org/show_bug.cgi?id=673894)

---

### Post by terrykiwi83 on 2012-04-13
cheers, for spotting the bug :)

---

### Post by Jonners59 on 2012-04-13
> **jernst said:**
> I've reported the bug upstream[1] and it has been fixed the next day !

The fix will be released in the next releases of evolution-data-server ; let's hope it'll be integrated soon in current Ubuntu releases.

[1] [https://bugzilla.gnome.org/show_bug.cgi?id=673894](https://bugzilla.gnome.org/show_bug.cgi?id=673894)

Yes, I saw that.  It included some of the bug reports I had seen or contributed last year in the report.

Fingers crossed it is a fix and we get it soon.

---

### Post by Jonners59 on 2012-05-06
No, not fixed.  Either the patch has not been distributed as yet in the updates or it does not fix the problem

---

### Post by drewstew on 2012-05-08
Having terrible problems with Contacts.  Noticed it a couple of days ago when I tried to add names to an existing Contact List.  They seem to go on, but when I check they are just meaningless characters - not quite Wingdings, but you get the idea.
So thought I would try setting up a new Contacts List - just called it Random and added a couple of names, well, at random.  Again, seemed to go on, but this time, the name of the Contact List is shown but nothing underneath!  Then when I click it, it closes Evolution down completely.
Tried backing up the data, then deleting and reinstalling Evolution, with exactly the same results.  Then tried on computer number 2 running a different brand of Linux, an entirely new install of Evolution and installing the backed-up data.  Same results! Anyone else experiencing similar?

I'm tempted just to mothball Evolution and start using another email client.  Any suggestions please, excluding Thunderbird, which really isn't to my taste?

---

### Post by Jonners59 on 2012-05-09
OK, the answer to the Calendar is
[HTML]rm -r $HOME/.config/evolution/calendar[/HTML]

Then start Evolution...

The reason, I have found for the problem is that the Evolution team have moved many of the directories in the more recent builds.  I also tried this on the addressbook, but it screwed up the install, so now i have other problems to resolve, but for calendar this works.

I found it in a long search.  There are many bugs and fault reports out there about this, but this is the only fix.

---

### Post by drewstew on 2012-05-29
Anyone worked out an answer to the Contacts issue yet?
I can add new contacts individually, but the moment I try to tinker with any of my Contact Groups, it just goes weird.

Have tried also an "incremental" change, i.e. when I'm dropping a member from a group and adding another.  I start by changing the first name, save, then surname, save - but the moment I try to change the email address - meaningless characters!

---

