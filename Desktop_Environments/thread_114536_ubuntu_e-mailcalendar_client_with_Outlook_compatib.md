---
title: "ubuntu e-mail/calendar client with Outlook compatibility"
date: 2006-01-08
forum: Desktop Environments
---

### Post by fermulator on 2006-01-08
Good evening!

I'll start off by saying I'm relatively new and still learning ubuntu linux, (and linux in general).  But i'm enjoying it so far and am looking forward to more learning.

I have one major concern though, and this is regarding an email/calendar client for linux and windows.

Here is _my goal_:

1.  I'm looking for a client which can do e-mail, contacts and calendar functionalities much like Microsoft's Outlook.
  a.  This client should be cross platform compatible.  In other words, I should be able to use the same data file (PST, mbox) in either Linux or Windows.  Therefore, any contacts/calendar/email actions that are performed in either OS will be recognized by the other OS.

_An example:_

1.  In **Linux.**
   a.  Open email client.  Receive email...reply email (notice the email would be saved in "sent items"...)
   b.  Add an appointment in the calendar.
   c.  Remove a contact.

2.  Boot into **Windows**
   a.  Open the same (or perhaps a different) email client.  Receive mail...
   b.  Since this client is using the same data file, it would see that the deleted contact is no longer stored, that there is a new appointment in the calendar, and it would also see the sent email in the "sent items" folder.

_Questions / My Comments:_

Does such an application(s) exist?

I've looked into Thunderbird, which SEEMS like it does everything I need except the Calendar aspect...

I've looked into Scalix, which MIGHT do the trick...but there is no download for Ubuntu!  (Only Redhat, SuSe..)

What about "CrossOver Office"?  Will this do it for me?

_Technical Notes:_

1.  ubuntu is installed on my 60GB IDE drive. (ext3)
2.  Windows is installed on my 2x160GB SATA RAID drive. (NTFS)
3.  I've configured linux using dmraid.  This allows linux to read/write my Windows partitions (I can see everything fine, and I'm good to go for that).
4.  Windows currently cannot see my ext3 partition, but I hear its simple, so that shouldn't be a problem.

Any and all comments/suggestions will be greatly appreciated.

Thanks!

** Hoping to find that client! **

PS:  Please do not reply with a question asking WHY I wish to do this.  The answer is simply because I'm not ready to completely switch over to Linux, and need a failsafe to be able to go back to Windows if needed.  This is because I run a small business and provide technical support as well.  Plus, I'm not as comfortable in Linux as I am in Windows!  So it will take time.  Finally...regardless of WHY...it should be able to be done! :-)

---

### Post by leech on 2006-01-08
Evolution :D  It works quite well, and depending on what your email server is, can do all the calendaring, appointments, etc.

Leech

---

### Post by gw90se on 2006-01-08
I don't know if you'll find anything that is that compatible with Outlook, but if you do, you'll have to keep all mail on your Ubuntu drive, since Linux won't write to the XP's NTFS. 
I know that you could set it up if tou used Thunderbird in both systems, so for the calendar, take a look at Sunbird.

---

### Post by Sef on 2006-01-09
Sunbird is still deep in beta, not ready to be used by nontechies who want a stable calendar.

---

### Post by glorry on 2006-04-03
Me quite same as you wished.

After discuss with develepor of Evolution, they said Evolution support ms exchange mailserver but must be under OWA(Outlook Web Access) and: can not support Proxy access way!!!!
so:
1, *.pst file can not be handled under Linux directly;
2, you can only use OWA(no proxy connect) under Evolution.
3, Never use NTFS while worked together with windows.

some new pls contact with me: [email]glorry@21cn.com[/email]

---

### Post by Mr Fat Bat on 2006-05-10
From what i've seen it appears that older versions of Evolution support direct connections to exchange and only the newer ones force you to use OWA.  Which is a pain becuase my works OWA is behind https!  So evolution can't get to it to authenticate me!

The day I can finally stop having to boot into XP to check my e-mail is the day I never have to use it again! =p

---

### Post by eentonig on 2006-05-11
evolution works like a charm for connecting to Exchange.

But having Linux/windows using the same local data files won't be possible I think. I just imported all my old mail into Evolution (via thunderbird on Windows).

If, for wathever reason, need to use Outlook to get my mails, I leave them in the Inbox; the next time I use Evolution, they're still there and I can archive them in any the desired folder.

---

