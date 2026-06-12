---
title: "Evolution: leave messages on server for X days"
date: 2005-01-24
forum: Desktop Environments
---

### Post by doni on 2005-01-24
hi there...

i'm using thunderbird as e-mail client, but wanted to give evolution a try, because it looked quite good. 
but there was one thing, i really work with, which i couldn't find, which makes it quite useless for me:

an option to **leave messages on server for X days** ! if i do remember right, i saw a function to "leave messages on server", but not for "x days", which is quite important if you want to check your mail from several machines, but don't want to have your messagebox exploded.

is there no such feature, or didn't i see it? thanks for help...

doni

---

### Post by crun on 2005-01-24
You have a point, the Mail Account settings only have the option "Leave messages on server" and nothing more. Searching Google comes up with
* [a post on the Novell support forums](http://forums.novell.com/group/novell.support.ximian.evolution/readerNoFrame.tpt/@thread@443@F@10@F-,D@NONE/@article@613) 
* [one on the Ximian mailing list](http://lists.ximian.com/archives/public/evolution/2002-March/017425.html) 
but neither has been responded to. My guess is it hasn't been implemented yet, but it seems strange for such an important feature.

---

### Post by dubber on 2005-01-24
Evolution probably expects you to use a filter to do this.

Go to Tools menu, choose Filters...
In the dialog choose Add button.
Give your filter a name "Delete Old".
In the "If" section, choose drop down that now reads "Sender" and choose "Date Received"
Choose " is before" for next drop down.
Choose "<click here to select a date>" drop down.
In the dialog box, in the "Compare Against" drop down, choose "a time relative to the current time"
Change the number to "5"; change the "ago" drop down to "Days"

In the "Then" section, choose "Delete" from the drop down that now reads "Move to Folder"
Click "OK"

Select a mail folder, like your Inbox and choose "Apply Filter" from the action menu.

Messages older than 5 days should be deleted. 

I haven't waited 24 hours to see if the next day's worth of messages will be deleted but I suspect they will.

I use filters to distribute emails to different folders so I can keep things a little better organized. As always with Linux, this is just the tip of the iceberg.

---

### Post by doni on 2005-01-25
@dubber....

thanks, but i think you've misunderstoud my question a bit. it's not a problem, that my local inbox explodes, but that the inbox on the server may explode....

thanks anyway....

---

### Post by xbaez on 2005-12-13
Yeah GREAT idea, suggestion, it's nice to see how other people think around the same problem.

But man, I want evolution to delete folders in my POP3 server, NOT in my local mail

**Linux is a problem**
As much as I love it, I read the other time that most excecutive office users aren't considering changing to linux because it lacks powerfull email applications.

I mean, I want to synch my palm with linux, like I do with Outlook 2003. Both thunderbird and outlook are powerfull email applications, but thunderbird isn't able to sync messages with palm (accounts, calendar, notes...).

I tried emulating Outlook with Crossover, works ok. I tried installing Palm software with it, doesn't works ok.

I will then try to use the latest version of wine, and see if I'm able to make Outlook, Internet Explorer and the Palm software work in not a perfect but in a stable way.

Ultimately, I will give a try to kmail, and if nothing works entirely, I will continue using Thunderbird, and korganizer for the appointments, contacts and such.


the MAIN PROBLEM is that I will really like to have my contacts synched with my email program.

Isn't Linux a problem? I could have all of this working great with Windows, Outlook 2003, Palm software and even stuff like AddIt that doesn't works in Linux.

Really, I'll continue using Linux I guess, but Windows is very attractive because of all these things.

One workaround then.

How can I access evolution contacts from thunderbird?

---

### Post by chrisTGc on 2006-01-10
Hi,
Same prob here.Inbox at ISP did fill and from then Emails where returned to sender and not received here.First I heard of it was from friends telling me they where unable to email me and their mails where just bounced back to them.All despite deleting unwanted and old mails from evolution inbox.

Yesterday 15 mails in my inbox but logging onto isp mail via their homepage my inbox there had 185 mails and crammed full.

Couldnt find way back to evolution accounts and didnt want to set up a new account.Reading mails here not sure if there is any point,What i would like to have is 'Retain message on server untill deleted from my inbox',but reading posts seems only options are 'Leave on or always delete from server'.

Must admit installed Mozilla Thunderbird,inbox here took all 185 mails and deleting them down to the 15 wanted checked inbox on isp which now tallies.With Thunderbird find it ESSENTIAL to set correct ie 'leave message on server untill deleted from my inbox' BEFORE first run/get mail.

Sorry but regard the Evolution options as insufficient.

That aside UBUNTU GNU/Linux is GREAT.

Best wishes Chris,

---

### Post by xbaez on 2006-01-11
If you want to use mail in Linux I recommend Kmail.

It might not be that beautiful as Evolution and Thunderbird, but it has contacts, calendar, to do list... and syncs very nicely with your palm, using KPilot.

Apart from that it allows you to use spamassassin and has other neat features.

I suggest you give it a try.

---

### Post by chrisTGc on 2007-11-05
FYI,Evolution now has an option 'leave messages on sever for X days',sorts the prob and no prob now.

---

### Post by Bernard_ivo on 2008-01-24
Well it has, but seems not to work properly! I had both checked: Leave a message on server; Delete after X days; The result is all e-mails are still in my mailbox on the server. When I unchecked Leave message on server (the other still checked) then all were gone. 

I'm running evolution 2.12.1
Under Gutsy

---

### Post by chrisTGc on 2008-01-27
[QUOTE=Bernard_ivo;4196707]Well it has, but seems not to work properly! I had both checked: Leave a message on server; Delete after X days; The result is all e-mails are still in my mailbox on the server. When I unchecked Leave message on server (the other still checked) then all were gone. 

Hi,yes so i found out to.The evolution team say that POP mail was never designed for this anyway (part saving messages on the server) and that it was designed for either all to be left on the server or all to be taken off.Ah well,Thunderbird and Sylpheed seem to handle it reasonably if not perfectly.So for me its back to gDeskCal for the calendar and Thunderbird for mail with Sylpheed on the ole P3.I admire Evo a great deal but it does get its share of bugs. 

Best Wishes all,Chris.

---

