---
title: "How to use Evolution with multiple accounts and mailing lists?"
date: 2009-06-11
forum: General Help
---

### Post by ubnewbie2 on 2009-06-11
After a couple of corruptions of mail databases in Thunderbird (I was warned that it could do this if a mail account got too big), I am trying Evolution - mainly as it's the default in Ubuntu.  It looks quite nice.

I managed to configure my multiple email accounts in it's preferences, and have set up so rules to sort email into various folders.  For example emails to from the different mailing lists, to which I am subscribed, go into folders named after the mailing list.

The problem comes when I want to post a new message to a mailing list. When I click on new in Evolution, it always starts a message with a default email account in the 'from' field.  This means I have to remember, and manually change, the from field to whichever email account is registered with that mailing list, or else it will fail.

In Thunderbird, everything was kept in separate places, with an inbox for each account (as opposed to the single inbox for everything in Evolution).  This meant you could be working in one particular account, and when you clicked on 'write' to compose a new message, the correct account was defaulted in the 'from' field.  It's not easy to ddo, because it's not a one for one thing.  Three mailing lists might have one account registered, and another might expect emails from me to come from a different account.

Not being very experienced in Evolution, I was wondering if there was a better way to set things up.  I tried setting up a search folder for the mailing list, but even with that selected, a new message does not default to coming from the correct account.

I need a way to at least be able to tell it to compose a new message using the account that the highlighted message comes from.  Using Reply does this, but that screws up message threading if I am starting a totally new subject.  I tried right clicking on the mailing list address in a message header and using 'Send new message to...' but that also uses the default email account (I really believe it should use the same email account that received the message in the first place)

---

### Post by lisati on 2009-06-11
I have the exact same "problem" - multiple email accounts, multiple mailing lists. So far I haven't bothered looking for a solution beyond remembering to check the "from" address before clicking "send"

---

### Post by ubnewbie2 on 2009-06-11
> **lisati said:**
> I have the exact same "problem" - multiple email accounts, multiple mailing lists. So far I haven't bothered looking for a solution beyond remembering to check the "from" address before clicking "send"

It could be done automatically if they wanted, because the source of each message is recorded in the header in X-evolution-source: pop://<emailaddr@wherever.net>.   The 'Send new message to...' option could pick that up.

Alternatively, how about an inbox and folders for each account?   Then the default 'from' field can be determined by which account is selected (same as Thunderbird).

---

### Post by ubnewbie2 on 2009-06-13
I have found another email client that handles multiple accounts properly.  It's Sylpheed.  It lets you have multiple mailboxes, one for each account, and also manually specify the inbox, sent folder, etc etc, individually for each account.  Most importantly, you can select the default sending account for each mailbox individually.

---

