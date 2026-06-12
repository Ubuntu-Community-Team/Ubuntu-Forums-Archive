---
title: "sending emails to notify of appointments"
date: 2007-04-28
forum: Desktop Environments
---

### Post by AAM on 2007-04-28
I am sick of trying to synchronize multiple calendars on multiple sites when the only thing I carry all the time is a mobile phone which can receive calls and SMS. I wish to consolidate all this angst and activity. The first step to achieving this is problematic and listed below.

I am using Evolution (for the moment) and trying to set up a method whereby an alarm associated with an appointment will trigger the sending of an email to a provided email address.

I have done a few hours of searching and emailing without any success.

I am using Evolution 2.10. There is the ability to specify alarms in appointments, but the Customize option allows a program (presumably 'mail' in this case) and then a string of parameters. And that's where it goes very very very hazy! I am unable to find documentation of acceptable parameters for there.

I'd be grateful of help in this so that I can achieve what I set out, but also do a HOWTO for what to me seems like a very basic requirement.

---

### Post by dante.regis on 2007-04-28
Hello,

You talk about "mail". Can your cellphone receive emails? My old carrier allowed me to receive mails as sms sent to [email]MYNUMBER@MYCARRIER.COM.BR[/email] (it does not allow it anymore :( ). Anyway, if you can receive this kind of email then, I believe, the program you are looking for is "sendmail". Evolution wouldn't have documentation on this program anyway. I personally never used it, but you can google for it a bit, or use "man sendmail" for more info.

Now, if you can't receive these emails, then I suggest you use Google Calendar. It has the option to send SMS alerts to specific carriers (I was impressed they allow it to some carriers here in Brazil, since we are almost always forgotten on this kind of stuff). Just go to calendar.google.com and register for an account. You don't actually have to use the google calendar. I have developed a Java program that adds appointments to the calendar just to receive SMS (I used it as my new e-mail alert). If you are interested, I can post it here.

Best,
Dante

---

### Post by AAM on 2007-04-28
thanks for the reply Dante.

Going down the email to phone route was not something that I was keen on because of cost. But I suppose that I should pursue this with my provider, although that doesn't solve the inability to email alarms from Evolution, just removes an intermediate destination!

I was aware of the Google Calendar ability to do this, I just remain wary about keeping my information on their servers even though their 'cleanness' is more reliable than my PC. I can receive SMS from a local site if I can email the SMS to them first. That's what I can't do. I am aware of sendmail, etc but the problem is still knowing what parameters to pass to get the email sent. "Mail" is the internal Evolution command for mailing (this much I could find!)

What does the java program do? sounds interesting but I'm not sure I understand what it does.


AAM

---

### Post by dante.regis on 2007-04-30
Well, the Java program is divided in two modules: one, which probably won't interest you, checks my GMail account periodically for new e-mail. When it finds a new email, it passes the info to the second module, which you might like: it's a program that, given a small phrase (100 chars, for example), automatically creates an event on my Google Calendar Account. 

Events on GCalendar have the possibility of reminders. These can be Popups, emails or SMS. So, the program chooses the SMS, and this way I receive an SMS telling me about new e-mails with 5-10 min of delay. It's interesting, though for some reason, even if the events exist on Google Calendar (I can search for them and find them), they are not shown on the daily brief, nor show the Busy flag on the calendar. It worked for me, who only wanted the SMS, but don't know if it is of use to you.

Let me know if I wasn't clear, or if you want a copy.

Best,
Dante

---

