---
title: "Exchange + Evolution"
date: 2005-11-15
forum: Desktop Environments
---

### Post by vtec on 2005-11-15
I set up evolution to work with an exchange server. However i'm disappointed in the buggyness of the two. At least once a day the exchange component goes crazy. Exchange is not a requirement, but it so far is the only way i have found of syncing two Linux boxes with evolution and a future palm. Are other people haveing the same problems, or is it just my setup?? Is there any better why to keep the contacts, calendar, mail etc... sync between 2 systems and a palm??

---

### Post by suRoot on 2005-11-15
You're not alone.  I've been having the same problems at work.  Evolution will lock up for no apparent reason, either when I'm using it or when it's been sitting in the tray for hours.  No rhyme or reason, just very buggy & prone to crash.  Almost every time I attempted to close it, it would fail to close prompting the force quit dialog.  Composing messages would cause the new message window to just sit there as if the screen were trying to re-draw it, unresponsive, etc.

I actually said the hell with it yesterday, turned on IMAP on our Exchange box & set up Thunderbird.  I can access all my mail & public folders just fine, so that works for me.  No crashes, period.

Can't help you with the palm as I don't use one (although surely you can sync from Thunderbird or another mail app)

---

### Post by vtec on 2005-11-15
With imap is there a way to sync tasks, contacts and calendar. The palm is a second thought. I mainly want to sync up 2 PC with that info in linux with any app that can do it.

---

### Post by suRoot on 2005-11-15
Sure - at least that's the case on my box.  I see my Exchange calendar, contacts, all that stuff.  You can even configure Thunderbird to use LDAP (which is a big part of Active Directory / Exchange) to pull addresses from your global address list.  You just don't get all the bells and whistles , messaging cruft that Microsoft throws in Outlook.

Unlike POP, IMAP stores everything on the server, exactly like MAPI (Outlook), so you can easily read your mail on multiple machines using IMAP.

Just make sure IMAP is running on the Exchange server, install Thunderbird (or whatever mail client you choose - even evolution), point it at your mail server, feed it your username & pass & then subscribe to the folders you want to see (inbox, calendar, contacts, etc).

Regarding Evolution / Exchange performance, I really haven't looked at it very much, but it appears that Evolution grabs your mail using OWA (outlook web access).  If that is the case, I can kind of understand the performance lags as that may not be the most efficient way of pulling mail from a server.  I always assumed they had come up with some reverse engineered version of MAPI, but I guess not.

---

### Post by vtec on 2005-11-21
I have evolution connected via imap to the server, but it only sees the mail. Is there something speical you have to do to get it to work with the tasks, contacts, and calendar. I subscribed to the folders, can see them when i'm looking at mail but nothing shows up when i switch over to the calendar.

---

### Post by N6546R on 2005-11-21
IMAP is great if your corporate security folks allow it. Mine don't. I'm stuck with wondering whether Evolution is going to crash and lose data, or crash and not lose data, or just hang for no apparent reason.

Perry

---

### Post by vtec on 2005-11-22
I know what you mean... I walk on eggs with evolution. However i don't think its possible to handle calendars via IMAP. Does anyone know of any other calendar program that can??

---

