---
title: "Unable to save changed password in Evolution"
date: 2010-01-03
forum: Desktop Environments
---

### Post by brianmc on 2010-01-03
I'm running Ubuntu 9.10 with Evolution 2.28.1.

I'm having a problem with an IMAP account I use with gmx.co.uk.

I had reason to change the password via the website so I could verify details of the account on gmx.co.uk.

Now I wish to change the password within Evolution. I only see an option to clear all remembered passwords - not individually.

I've tried going through the preferences for the IMAP account and unchecking the "remember password" box; it appears Evolution is still trying to log into the server with the no-longer-valid password.

Is there any way of resetting the password within Evolution without clearing all the passwords for my other email accounts? I would rather not have to waste time finding where I've noted on paper the passwords for four or five other email accounts.

---

### Post by brianmc on 2010-01-03
I have been able to reset the password for sending email.

This involved, from the above, unchecking all the "remember password" boxes for the gmx IMAP account, removing it from the list of 'active' email accounts, and restarting evolution.

When reenabled, I was able to send a test message from the gmx IMAP account, was prompted for a password, and able to re-set the checkbox to remember this.

I have not been prompted for the password to access the IMAP folders; if I do so then evolution gives an error and cannot be shutdown without again killing all the processes.

---

