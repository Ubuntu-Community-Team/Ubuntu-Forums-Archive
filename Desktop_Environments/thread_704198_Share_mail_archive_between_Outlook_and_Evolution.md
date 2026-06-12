---
title: "Share mail archive between Outlook and Evolution"
date: 2008-02-22
forum: Desktop Environments
---

### Post by cckarman on 2008-02-22
I am using my laptop as a Dual boot (XP for working at the office, Ubuntu GG for working at home). In Linux I use Evolution, which gives me access to the office exchange server (using OWA). Under XP, however, I maintain my outlook archive, which I would like to use under Linux as well. As that is not possible using the .pst files, I am looking for an alternative.

I understood that a local IMAP server might be the solution here. The question is: how can I do that, without setting up an external server (i.e., on a second computer). Is there an IMAP server that runs under both Linux and XP, or , can two servers use the same resources?

Any suggestions?

Chris

---

### Post by cckarman on 2008-02-23
No suggestions at all?

---

### Post by KCormier on 2008-02-23
I can't think of a way that'd be possible.  If you want to run an imap server it has to stay available on a separate machine or else your mail is going to start bouncing :-\.  You wouldn't need a heavy machine to run an imap server...  Not sure exactly how you'd implement all of that though (not familiar with outlook and such).

---

### Post by mtbsoft on 2008-02-27
Just a thought, setup the mail/MAPI server in a VMWare virtual machine as this can run under both Linux and Windows.  Whichever environment you are in, run up the single, common instance of the VM and point the appropriate mail client at it.

Bit left field but could work.

---

### Post by The WB on 2008-02-28
I looked into this issue when I networked two XP computers at home.  The long and the short of it - between the two computers - NO way.  Outlook is a Personal program, unlike Lotus Notes that is used on a network all the time.  

Trying to share any PST info from Outlook will cause you nothing but headache and heartache - as others have put it - Don't Do It!  You will have to export and import between the two to make it work.  Good luck.

---

### Post by cckarman on 2008-03-01
Thanks for your help. I now using a MAPI mail server on the (virtual) server for one of my website. Moved my major archives to it and using it both in Outlook and Evolution. Works great, problem solved!

Chris

---

