---
title: "IMAP Email Accounts: why is my email continually disappearing?"
date: 2013-03-18
forum: Desktop Environments
---

### Post by XEtedBear on 2013-03-18
I've now had a repeated experience of my emails disappearing - not deleted, just disappearing - since I converted from POP to IMAP. How do I stop this perverse behaviour?

On (bad) advice I converted my Evolution email client account from POP to IMAP. ALL email, in every folder, in client and host server just disappeared. I had no opportunity to even take a back-up in Evolution. My only backups were in POP mode. Having reset Evolution to POP mode and restored from backup I was able to export my emails to mbox files, loosing only about 5% of emails which were not in the newest Evolution backup.

I installed Thunderbird in IMAP mode and finally found a way to import into my TB local folders (you can't import into TB non-local folders in IMAP mode - how bizarre!). But - and this is the real problem - every time I attempt to either move or copy emails from a local folder into a non-local folder ALL emails, except the last one in the folder, disappear again. There is no sign of them in my client or in the host server.

How do I stop this damaging feature of IMAP?

---

### Post by mike acker on 2013-03-18
> **XEtedBear said:**
> I've now had a repeated experience of my emails disappearing - not deleted, just disappearing - since I converted from POP to IMAP. How do I stop this perverse behaviour?

On (bad) advice I converted my Evolution email client account from POP to IMAP. ALL email, in every folder, in client and host server just disappeared. I had no opportunity to even take a back-up in Evolution. My only backups were in POP mode. Having reset Evolution to POP mode and restored from backup I was able to export my emails to mbox files, loosing only about 5% of emails which were not in the newest Evolution backup.

I installed Thunderbird in IMAP mode and finally found a way to import into my TB local folders (you can't import into TB non-local folders in IMAP mode - how bizarre!). But - and this is the real problem - every time I attempt to either move or copy emails from a local folder into a non-local folder ALL emails, except the last one in the folder, disappear again. There is no sign of them in my client or in the host server.

How do I stop this damaging feature of IMAP?

i would expect this is a problem with your mail server rather than imap.... . imap is supposed to keep your mail on their server so that you can read it from {anywhere} -- e.g. on your desktop also on your mobil devices ...

in my experience not all e/mail services are created equal.  i use and recommend CoreComm . it works better for me and i like their privacy statement : they don't spider what you are doing . 15USD / quarter for basic service including 25 e/mail addresses and your own www domain .      can't beat it .

---

### Post by dev.null on 2013-05-07
My setup is less complicated than yours. Brand-new install of ubuntu 12.10, setup evolution w/ IMAP. My inbox has maybe 5k+ emails. It takes an hours for it to load them all. When I close it and re-open, they are all there, but as soon as it connects to the imap server and starts updating itself, all the emails disappear and get re-added over the next couple hours.

It wouldn't be that bad if the newer ones appeared first, but that's not the case.

I even have it set to download them for offline mode.

Older version of evolution didn't do this. I'm thinking I'll have to do something else for email. This upgrade is pathetic.

---

### Post by col48 on 2013-05-08
In my newly installed 12.04, I started by trying Evolution in POP mode (migrating from Thunderbird (POP) under Lucid in another partition on the same machine).

All the emails were imported successfully but once I started to move some around from one folder to another the occasional one disappeared as described in the OP.
Not always the one being moved.

This is one reason I moved back to Thunderbird (the other being problems with managing the Contacts list) before any emails disappeared from the email server.
Migrating T from Lucid to Precise took under 15 minutes including setting up the accounts, researching how to do it and doing precautionary backups.

---

### Post by BrunoLotse on 2013-05-08
I am running 12.04 LTS with Evolution IMAP+ connected to yahoo servers. Works like a charm.Cheers, Bruno

---

### Post by SeijiSensei on 2013-05-08
Have you "subscribed" to all the folders you want to reference in your mail client?  IMAP includes a concept of "subscribing" to folders.  Many servers and clients will not show unsubscribed folders even though the contents of the folder are intact.  In Thunderbird, you right-click your email address at the top of an account tree and choose Subscribe.  You'll be presented with a list of all available folders.  Just select the ones you want and subscribe to them.  I've never used Evolution so I can't help with that.

Subscription is usually not required for the inbox.

---

