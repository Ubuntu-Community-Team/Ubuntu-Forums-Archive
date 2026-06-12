---
title: "Syncronizing Google and Evolution Calendars"
date: 2009-04-21
forum: Desktop Environments
---

### Post by Cuba71 on 2009-04-21
**_Two Way Synchronization Google Calendar and Evolution 2.26.1 using WebDAV/CalDAV_**
> 
**Before you start, back up your Evolution settings to be safe.**

1.Define a Google calendar at [www.google.com](www.google.com)
2.Under settings, define your calendar as public
3.Start Evolution and go to Calendars
4.Click New > Calendar
5.Complete the Properties as follows:
6.Type: choose CalDAV
7.Name: your choice
8.URL:  caldav://www.google.com/calendar/dav/username@gmail.com/events
9.Check the box: Use SSL
10.Username:  username
11.Set the refresh time as desired
12.Click OK
13.Click Edit > Preferences > Calendar Publishing
14.Click Add
15.Under General:
16.Select Publish as:  iCal
17.Select Publishing Frequency:  Manual (via Action Menu)
18.Under Sources:
19.Click on your CalDAV calendar
20.Click on Publishing Location
21.Under Service Type select:  Secure WebDAV (HTTPS)
22.Server:   [www.google.com](www.google.com)
23.File:  /calendar/dav/username@gmail.com/events
24.Under Optional Information:
25.Port:  leave blank
26.Username:  username
27.Password:   password
28.Check the box Remember Password
29.Click OK
30.Click Close to return to Calendars-Evolution


Test it by entering a New Appointment
Click on Action > Publish Calendar Information
Go to your Google Calendar web page an hit the refresh button
The New Appointment should show within a few seconds

Note: Perhaps someone more experienced can explain how the whole thing works, I just find out by trial and error.

Antonio

---

### Post by darkstaar on 2009-04-26
Wow. It actually works.

Thank you. Been wondering how to do this.

--Leisa

---

### Post by fuerza on 2009-04-27
thanks, it works but for only the personal calendar
any suggestions on how to add the others?

---

### Post by somewhere2go on 2009-04-28
> **fuerza said:**
> thanks, it works but for only the personal calendar
any suggestions on how to add the others?

In (8. - URL) replace [email]username@gmail.com[/email] for the ID of the calendar.

Example:
caldav://www.google.com/calendar/dav/**jhg6778gg867hhuiy98hh@group.calendar.google.com**/events

---

### Post by labirn on 2009-04-30
You don't even have to set your calendar to 'public' or share any free/busy information. You can skip position (2.)

---

### Post by jay76 on 2009-04-30
Running **Evolution 2.26.1** and I seemed to have a **"Google" option** when creating a new calendar. Just fill in username etc and I was done.

Didn't have to make the calendar public either.

---

### Post by fuerza on 2009-05-02
> **somewhere2go said:**
> In (8. - URL) replace [EMAIL="username@gmail.com"]username@gmail.com[/EMAIL] for the ID of the calendar.

Example:
caldav://www.google.com/calendar/dav/**jhg6778gg867hhuiy98hh@group.calendar.google.com**/events


thanks, thanks, thanks
works great¡¡¡¡¡¡¡¡¡¡¡¡¡:guitar:

---

### Post by FokkerCharlie on 2009-05-10
Brill

That works a treat.  Only tiny gripe- Evolution asks me for a password every time I load the app, despite having the 'Remember this password' box checked.

Anyone else seeing this?

Charlie

---

### Post by rrkradio on 2009-05-12
> **jay76 said:**
> Running **Evolution 2.26.1** and I seemed to have a **"Google" option** when creating a new calendar. Just fill in username etc and I was done.

Didn't have to make the calendar public either.


Hi,
i use google calendar for work, but sync with evolution 2.26.1 isn't perfect:

1. during the sync the "alarm" is lost  (..... notify me 15 minutes before)
2. setting, in the property of calendar (google) under evolution, a time different from 30 minutes to refresh, will revert to 30 min at the next launch.

This behavior under Jaunty X64 with italian language. I confirm that is not necessary to make the calendar public.

Sorry for poor english and best regards from italy,
roby

---

### Post by senor_smile on 2009-05-13
I tried the instructions of the first post in this thread.  Now evolution will not open.  When I open evolution from the command line, I get no errors, but it never returns control or opens the program.  Is there any way to manually remove the settings I set up in evolution?

---

### Post by senor_smile on 2009-05-13
Nevermind.  I decided to give my machine a full reboot and evolution is now working.  It must have had some process running I was unable to identify.

---

### Post by senor_smile on 2009-05-14
The publishing options for evolution seem to be: 
1.daily
2.weekly
3.manual

I tried googling for changing the interval of the calendar publishing to something a bit shorter, but came up with nothing.  Anyone know if that is possible?

---

### Post by Cuba71 on 2009-05-14
I enter a new appointment in Evolution, then click Action > Publish Calendar Information and it goes to Google right away.

---

### Post by Ng Oon-Ee on 2009-05-22
> **fuerza said:**
> [QUOTE=somewhere2go]
In (8. - URL) replace [email]username@gmail.com[/email] for the ID of the calendar.

Example:
caldav://www.google.com/calendar/dav/jhg6778gg867hhuiy98hh@group.calendar.google.com/events

thanks, thanks, thanks
works great¡¡¡¡¡¡¡¡¡¡¡¡¡:guitar:[/QUOTE]

Ah, I can't get this one to work.... My primary calendar works, but the additional calendars don't. I can add another primary calendar (my girlfriend's) by using her username/password, but not by this method. Any help? Do I NEED to allow public access on her account? Would rather not, of course.

---

### Post by tdmoore on 2009-06-15
Interesting posts here.  

I too am curious as to why Evolution does some of the things with my Google calendar the way it does.  If someone can help me, I would be most appreciative.
Background.  Running 9.04 Jaunty.  Evolution 2.26.  Using this from my home desktop when working from home for access to printers, scanner etc.

We run Google Apps for our work and the email(IMAP)on Evo runs fine.  Google does a great job on the spam so the junk filter issues posted elsewhere really does not affect me.

I can create an event in both Evo and Google and they publish to each other.  However, in opening up the calendar, NUMEROUS events do not publish to Evo from Google.  It seems hit and miss for some reason.  Daily events, hourly, invites from others, private events, multiple days...some publish and some do not.

Does anyone have a fix here?  My plan would be to migrate my work notebook to Ubuntu from XP and use Evo (we use TB at work in Windows) and sync my Treo to that directly, however the calendar issue is the killer for me.  I sync the Google calendar directly to my Treo now using CompanionLink and it works great, however nothing for Linux.

Looking forward to any advice.

---

### Post by tomvanbraeckel on 2009-06-16
> **somewhere2go said:**
> In (8. - URL) replace [EMAIL="username@gmail.com"]username@gmail.com[/EMAIL] for the ID of the calendar.

Example:
caldav://www.google.com/calendar/dav/**jhg6778gg867hhuiy98hh@group.calendar.google.com**/events


That's correct, but to make sure your changes get published back to Google, you also need to replace this:

23.File:  /calendar/dav/username@gmail.com/events

Example:
23.File: /calendar/dav/**jhg6778gg867hhuiy98hh@group.calendar.google.com**/events

---

### Post by jackerhack on 2009-08-18
> **FokkerCharlie said:**
> Brill

That works a treat.  Only tiny gripe- Evolution asks me for a password every time I load the app, despite having the 'Remember this password' box checked.

Anyone else seeing this?

Charlie

I have this problem too. With five CalDAV calendars, it's five passwords every time I start Evolution!

---

### Post by Cuba71 on 2009-08-18
There are 3 places withing Evolution, where you should have the "Remember password" question checked:

Receiving Email
Sending Email
Publishing Calendar

Double check your settings

---

### Post by Rubadubdub on 2009-08-21
Thanks for this howto Cuba71, it helped me a lot. But I was having a problem with my password. Evolution kept asking for the passwords for all my calendars (5 of them). I found the solution on launchpad. 

the trick is to enter the url of the calendar in the following way (step 8 in your howto):
caldav://username@www.google.com/calendar/dav/username@gmail.com/events

And here the username is without "@gmail.com"

and fill in the username (step 10):
[email]username@gmail.com[/email]

I also did not have to do step 13-30 publishing of the new appointment when instantaneously.

Thanks again because of your howto I finally got everything the way I want \\:D/

---

### Post by Rubadubdub on 2009-08-21
By the way. I read that this "password problem" is solved in ubuntu 9.10

---

### Post by samcompton on 2009-09-09
Thank you Cuba71.  It never worked for me setting up a Google Calendar using the built in Google Calendar feature in Evolution.  Your method works great.

Thanks.

---

### Post by swdinesh on 2009-10-28
I made all the steps you suggested but I can´t retrive the calendar.
I looked at the properties of my google calendar and the caldav field became 
**caldav://gmail.com@gmail.co@gmail.c@gmail.@gmail.o@gmail.om@gmail.o@gmail.@gmail@gmai@gma@gm@g@@www.google.com/calendar/dav/swdinesh@gmail.com/events**
 instead of my settings *caldav://www.google.com/calendar/dav/swdinesh@gmail.com/events*

I´m using evolution 2.24.3 on 8.10 ubuntu 64bit version

thank you for any help 

Alex

---

### Post by reinz on 2009-11-01
Strange, after closing the Calendar publishing add or edit window, I get an error message:
[I]
Mount of davs://myusername%40gmail.com@www.google.com/calendar/dav/mycalendarID@group.calendar.google.com/events failed: HTTP error: Not Found[/I]

where myusername is my google calendar's real username and mycalendarID is my google calendar's real ID number.

I double checked all input fields and still the message is appearing. Any suggestions?

My system:
Ubuntu 9.10 Karmic Koala x86
Evolution 2.28.1

---

### Post by Cuba71 on 2009-11-01
Please, double check this instructions, it's important that you select "Secure WebDAV (HTTPS)", is the only one that works.  I havent' tried 'group calendars', I'm not sure if that's a problem or not.


```

19.Click on your CalDAV calendar
20.Click on Publishing Location
21.Under Service Type select: Secure WebDAV (HTTPS)
22.Server: www.google.com
23.File: /calendar/dav/username@gmail.com/events
24.Under Optional Information:
25.Port: leave blank
26.Username: username
27.Password: password


```

---

### Post by reinz on 2009-11-02
Thanks Cuba71 for your answear! 
But no better results when I use my google username instead of calendar ID. A litttttttle bit I'm happy with that because I have several google calendars and using the username I can sync only the google's primary calendar.
Someone else getting that kind of error message, or am I the only one?

greetings!

---

### Post by swdinesh on 2009-11-02
I made again the tutorial (substituing username with my user (without @gmail) but nothing: i obtain the same weird username i already posted :( 

any other suggestion?

Alex

---

### Post by brookie on 2009-11-02
Hi all, 
Some more info that may help. 

In Karmic I set up the gmail account then went to add a new calendar. No Google option available. So, I just restarted Evolution and went to add another Calendar and Google option was there. 

Set it up and can write to my Google Calendar from Evolution without setting up all the steps mentioned here for the Publishing stuff. 

Also Can write from my Google Calendar to Evolution. Everything is syncing both ways (adding/deleting) in Karmic and Google Calendar without setting up the Publishing steps. 

Maybe it's a new thing with Evolution 2.28.1 and Karmic. It never worked for me in Intrepid so I went to Thunderbird which I love, but Thunderbird is laggy as all get out in Karmic causing Xorg to hog CPU. 

Evolution is running fast and snappy. Maybe I'll give it a drive for a while. 

Cheers, 
Brook

---

### Post by swdinesh on 2009-11-02
thank you for thia suggestion... i think it´s time to upgrade to karmic

i test it and i´ll let you know Brook :)

thank you
Alex

---

### Post by klicki on 2009-11-12
The sync between Evo and Google Cal works for me in Evo 2.26.2 with my personal calendar only. If I am trying to import a group calendar, it fails. What I did: I added a caldav calendar with this URL:
```
caldav://www.google.com/calendar/dav/bund_6127_%48amburger+%53%56#sports@group.v.calendar.google.com/events
```After that I filled in my Google mail account user an entered pwd on request. When I am trying to use this one, it goes into an endless loop and doesn't show anything. When I am checking its properties again, the URL is cut after 60 chars.](*,)

Can someone please check this in karmic?

---

### Post by Cuba71 on 2009-11-12
I tried the group calendar with Evo 2.28.1 in Karmic with the same results.

The URL address gets truncated

---

### Post by klicki on 2009-11-13
> **Cuba71 said:**
> I tried the group calendar with Evo 2.28.1 in Karmic with the same results.

The URL address gets truncated
:smile:
Thanks for trying it. Now I know for sure, that I can delete Evolution from my plans. :cry:

---

### Post by sgosnell on 2009-12-21
I'm having the same problem a lot of people have reported.  Evolution crashes immediately upon clicking on the Calendar button.  No crash report is logged at all.  I can't access my calendar at all.  This seems to be directly related to syncing to Google calendar.  I've purged Evolution, removed the entire .evolution folder, and reinstalled, and the Google calendars still show up in Evolution in the preferences, and I can't get rid of them.  The data is stored somewhere, and it crashes Evolution every time I try to open a calendar.  Does anyone have any further information on this?  I've read bug reports on Launchpad, but they're mostly more than a year old, and I've seen no resolution.  This is getting annoying.

---

### Post by original_MikZ on 2010-03-14
G'day people,

I continue to be frustrated by this. I followed the steps Cuba71 posted in April 2009, and took note of what Rubadubdub said in August, but I'm having numerous problems, both for my personal GCal and my work GCal.

Questions:

[LIST=1]
[*]Has anybody gotten this to work *without* their login being a gmail.com login? I don't use GMail—I'm uncomfortable enough about having my appointments in the cloud without putting my mail there as well. My login is therefore my e-mail address at my own domain, similar to *google {at} originalmikz {dot} net*.

[*]Those of you for whom it works, what version of Evolution are you using, and in which version of Ubuntu?

[*]A few people have said that step 2, defining the GCal as public, is unnecessary. Is this true? My GCal has appointment data going back to the mid-1990s (I've imported all my old Palm O/S data) and I really don't want the whole world to see it.
[/LIST]
My setup: Ubuntu Intrepid, Evolution 2.24.3.

Issues I'm having:

1. The same issue swdinesh reported in October. (swdinesh is on the same platform as me except mine is just a 32 bit installation.) The issue is that URL in my CalDAV calendar properties gets munged. Thus ```
caldav://www.google.com/calendar/dav/google@originalmikz.net/events
``` becomes ```
caldav://originalmikz.net@originalmikz.ne@originalmikz.n@originalmikz.@originalmikz@originalmik@originalmi@originalm@original@origina@origin@origi@orig@ori@or@o@@www.google.com/calendar/dav/google/events
```

2. When I click to select a calendar in the calendar bar, the tick briefly (for about 100ms) appears but then disappears. A message that starts with 'Opening...' briefly (also about 100ms) flashes at the bottom of the window.

3. When I try to use the Google option instead of CalDAV, appointments I newly add appear in Evolution, but appointments that were already there do not. Not very helpful.

It's probably about time I update to Karmic—64-bit Karmic works well on my work laptop. From what klicki and Cuba71 are saying, group calendars don't work, but just having my personal calendar working would be worth it. When I get around to it, I'll let you all know how it goes.

And to the person who stole my Treo, causing me to have to pursue all this: you suck. [-(

---

### Post by sgosnell on 2010-03-14
I have no solution, unfortunately.  I'm at the point where Evolution crashes immediately whenever I click on the Calendar button.  It has done this through a version upgrade, and it's very annoying.  I simply cannot make it work, even with the default calendar.  I've deleted everything I can find, including "sudo apt-get purge evolution", and it persists.  It's a bug in Evolution somewhere, but it's not a priority, and I can't fix it.  So be careful about syncing Google calendars via CalDav.

---

### Post by darkstaar on 2010-03-14
> **sgosnell said:**
> It's a bug in Evolution somewhere...

I don't think so. Cuba71's "HowTo" works for me and has been since his initial post, through several versions of Ubuntu/Evolution, on two very different machines.

---

### Post by sgosnell on 2010-03-15
I've seen the bug reports on Launchpad.  The problem seems to have been acknowledged, but no fix yet.  The bug report is pretty old now.

---

### Post by original_MikZ on 2010-03-15
darkstaar: Is the domain for your Google account gmail.com or something else? i.e. did the URL you entered for step 8 have '@gmail.com' in it? Some other domain? Did you ever have it working under Intrepid? I'd love to know how your setup differs from mine.

sgosnell: did you try also removing Evolution data in gconf-editor? Apparently the uninstallation process doesn't bother with that, so perhaps whatever's crashing Evolution for you is in there.

---

### Post by sgosnell on 2010-03-15
Yes, I've removed all the Evolution directories I can find, manually and automatically.  This has gone on for almost a year, and it just won't work on my machine.  On a new SDHC installation it works, as long as I don't try to sync any online calendars, but once it breaks, it's seemingly broken forever.

---

### Post by darkstaar on 2010-03-15
> **original_MikZ said:**
> darkstaar: Is the domain for your Google account gmail.com or something else?

In my case, I'm using Gmail with my own domain so my URL for line 8 would look like:
```
caldav://www.google.com/calendar/dav/leisa@mydomain.com/events
```

> **original_MikZ said:**
> Did you ever have it working under Intrepid?

I would have been running Hardy back then (skipped Intrepid for various reasons) but also used it through Jaunty and Karmic without any problems.

One thing to note: Your username must contain your full e-mail address if you're using your own domain. For example, my username looks like ***[email]leisa@mydomain.com[/email]*** . Of course, the domain part of the username would not be required if you were using a plain old Gmail account.

---

### Post by youknowit on 2010-10-06
On Ubuntu 10.10, you no longer need to enable Calendar Publishing (it seems).

Create a new calendar, as explained above in steps 1-12.

Simply add an event/appointment on your Evolution calendar. When you add, it asks whether the event is on this computer or Google Calendar.  Choose Google to indicate that the newly added event is google calendar event. That's it.  The new event appears on my Android phone, automatically synchronised!

---

### Post by sgosnell on 2010-10-06
I get the same thing on 10.04 and Linux Mint Debian Edition.  The current version of Evolution works well with Google Calendar.

---

### Post by oscarmeyer51 on 2010-11-01
Never saw a response for tdmoore's post in June of 2009.

Am reposting it here with my issue as well.

tdmoore wrote:
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
June 15th, 2009 	  #15
tdmoore
Just Give Me the Beans!
 
Join Date: Oct 2007
Location: Calgary, AB Canada
Beans: 62
Ubuntu 9.10 Karmic Koala
Send a message via Skype™ to tdmoore
	
Re: Syncronizing Google and Evolution Calendars
Interesting posts here.

I too am curious as to why Evolution does some of the things with my Google calendar the way it does. If someone can help me, I would be most appreciative.
Background. Running 9.04 Jaunty. Evolution 2.26. Using this from my home desktop when working from home for access to printers, scanner etc.

We run Google Apps for our work and the email(IMAP)on Evo runs fine. Google does a great job on the spam so the junk filter issues posted elsewhere really does not affect me.

I can create an event in both Evo and Google and they publish to each other. However, in opening up the calendar, NUMEROUS events do not publish to Evo from Google. It seems hit and miss for some reason. Daily events, hourly, invites from others, private events, multiple days...some publish and some do not.

Does anyone have a fix here? My plan would be to migrate my work notebook to Ubuntu from XP and use Evo (we use TB at work in Windows) and sync my Treo to that directly, however the calendar issue is the killer for me. I sync the Google calendar directly to my Treo now using CompanionLink and it works great, however nothing for Linux.

Looking forward to any advice.
__________________
Thanks,

tdmoore 
<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

Same issue for me as for tdmoore, except Evolution worked fine for me under 9.04 & 9.10, going to 10.04 and 10.10 it syncs only one way (from Evolution to Google Calendar). Google Calendar and my phone (iPhone) sync two way with no issues, but nothing gets updated on Evolution unless I go into that on the laptop and update from there.

Have not checked LaunchPad to see if this is a bug currently being worked or considered closed.

Any thoughts from the community before any info I glean from there gets appended here?

---

