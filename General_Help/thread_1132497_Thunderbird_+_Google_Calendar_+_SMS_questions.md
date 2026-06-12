---
title: "Thunderbird + Google Calendar + SMS questions"
date: 2009-04-21
forum: General Help
---

### Post by Ck.asdf on 2009-04-21
Hello, just recently I discovered the ability to:
*use Google Calendar inside of Thunderbird (TB) with Google provider & Lightning
*send text messages to GVENT to add calendar events
*set up Google Calendar to text me 2 hours before an event


[green = solved, yellow/orange = kind-of w/ workaround, red = not yet solved]

However, I have some questions that hopefully have some solutions.
[color=green]*The default notification in Google Calendar is set to send an SMS message to me 2 hours before the event.  However, when I create an event with a reminder in TB, it only makes the reminder a pop-up notification for the time I set within TB.  Is there a way that the notification is always set as SMS?[/color]
[b][color=orange]*When I am disconnected from the Internet, I don't have access to the calendar events in TB.  While I realize it's pulling the calendar from the Internet, can't it create a cached local copy?[/color]
[color=red]*When I send a text message to GVENT it correctly sets the default reminder as a 2 hour before-hand SMS message.  One question, though: can I change that option within a message? Like, "Meeting at John's on Thursday at 7pm reminder 2 days"[/color][/b]
That last bit, "reminder 2 days" would remind me on Tuesday at 7PM - can I do something like that?


By the way, version numbers:
Ubuntu Studio 8.10 (fully updated)
Mozilla Thunderbird 2.0.0.21 ( 20090318 )
Lightning 0.9
Provider for Google Calendar 0.5.1


Thanks!

---

### Post by RudolfMDLT on 2009-04-22
Hi there,

Well, I can only answer one of your questions:

> Is there a way that the notification is always set as SMS?

This is a bit of a hack so post back if you're not sure what you are doing.

Download the *provider_for_google_calendar* from the mozilla addon's website. If you already have it, fine. Notice the extension is *.xpi, but in truth it's a zip file. Now rightclick on the file, point to Open With and click on Archive Manager.

Open the folder "js". Open the file called "calGoogleUtils.js" with any text editor(rightclick -> Open With -> Text Editor).

Press CTRL+F and find "alert". Do this 3 times and where ever you find "alert", replace it with "sms". Save the file, and archive manager should automatically update it.

Now in Thunderbird, uninstall the *provider_for_google_calendar*, restart thunderbird and install it again using the *.xpi file you just edited. 

When you set a reminder now in Thunderbird it will be an sms on Google Calendar.

Cheers,

Rudolf

ps: original solution from this guy: [http://www.nasirabed.eu/2008/10/24/thunderbird-lightning-and-google-calendar-with-sms-reminders/](http://www.nasirabed.eu/2008/10/24/thunderbird-lightning-and-google-calendar-with-sms-reminders/)

---

### Post by Ck.asdf on 2009-04-22
SWEETNESS!  You're great, it works, thanks! :)

Okay, so now - anyone for any of the other issues? :P

By the way, I like your avatar.  Took me a moment, but I got it. ;)

---

### Post by chrisinspace on 2009-04-22
> **Ck.asdf said:**
> 
*When I am disconnected from the Internet, I don't have access to the calendar events in TB.  While I realize it's pulling the calendar from the Internet, can't it create a cached local copy?

If you right-click a calendar in the 'Calendar' pane and choose 'Properties', there is a check box where you can set a calendar to 'Cache'.  It is experimental, however.

---

### Post by Ck.asdf on 2009-04-22
Okay, that works.
Sad thing is, while I'm offline, I can't make new events (which would ideally get synced to Google once I'm back online).  I suppose that's part of its "experimental" nature.
**One workaround for this problem**, is to save the event as you want it in the "Home" calendar, and when you're back online, edit the event and just change the calendar it's saved to to "Gcal" (whatever your Google Calendar's name is).  The event will disappear from the calendar for a moment, and come back as a Gcal event.


Another question: since I'm only using Thunderbird for the calendar function, is there a way to make it automatically open into the calendar function when I open it?  Currently it opens to mail.

---

### Post by RudolfMDLT on 2009-04-25
> **Ck.asdf said:**
> SWEETNESS!  You're great, it works, thanks! :)

Okay, so now - anyone for any of the other issues? :P

By the way, I like your avatar.  Took me a moment, but I got it. ;)
:D glad stuff is working for you!

---

### Post by Ck.asdf on 2009-04-25
I've updated my first post to show the "status" of each question via color.

Does anyone know where I can get on a mailing list or something similar to let me know the progress of Lightning (I imagine that's the plugin involved with the experimental cache stuff), so I can know when the cache is fully-functional?

---

### Post by slcpunk on 2009-11-20
> **Ck.asdf said:**
> I've updated my first post to show the "status" of each question via color.

Does anyone know where I can get on a mailing list or something similar to let me know the progress of Lightning (I imagine that's the plugin involved with the experimental cache stuff), so I can know when the cache is fully-functional?

Just want to confirm this- can you edit the reminder or alert in TB for an event that you were invited to ( ie: you didn't create it) and have it save?

I can not, and that makes this the whole TB / lightnight /google calendar thing less than useful.

I am using the extension from "lightning-extension" installed via apt get, not the plain jane lightining extension from mozilla.

---

