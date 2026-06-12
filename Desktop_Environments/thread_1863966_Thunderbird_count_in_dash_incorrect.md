---
title: "Thunderbird count in dash incorrect"
date: 2011-10-18
forum: Desktop Environments
---

### Post by sderrick on 2011-10-18
The count of unread emails that overlays the Thunderbird icon in the dash is almost(95%) wrong! It always shows more messages than there is. 

Its annoying. The count will show say 5, and there are NO that is ZERO messages that indicate they are unread.

I even went through and executed "mark folder read" on every folder just to be sure Thunderbird was lying. No joy.

How do I turn off this useless indicator?

Scott

---

### Post by andreselsuave on 2011-12-07
Same problem here. Restarting thunderbird fixes it for me, but it is an annoyance... :(

By the way, do you guys know any extension for not exiting thunderbird when closing? Kind of firetray, but this add-on does not longer work properly in 11.04 

Andrés

---

### Post by BC59 on 2011-12-07
There is a way to do a workaround.

Export your messages and address book.

[http://kb.mozillazine.org/Importing_and_exporting_your_mail](http://kb.mozillazine.org/Importing_and_exporting_your_mail)

Then go to ~/Home and press CTRL+H to see the hidden folders and go to ~/.thunderbird. Rename it to e.g. /.thundebird1 and start Thunderbird. Create a new account and import your messages and book.

---

### Post by andreselsuave on 2011-12-07
So what you are saying is that it's a problem of corruption of the thunderbird profile folder, aren't you? But if that's the case, if you do what you suggest it would eventually be corrupted again by the program...

---

### Post by typhoon_tip on 2011-12-07
There is also another way, upgrade to Thunderbird 8.0 from the proposed repositories, bug has been fixed.

---

### Post by andreselsuave on 2011-12-07
> **typhoon_tip said:**
> There is also another way, upgrade to Thunderbird 8.0 from the proposed repositories, bug has been fixed.

That sounds like a better solution to me.

Thank you

---

### Post by typhoon_tip on 2011-12-07
> **andreselsuave said:**
> That sounds like a better solution to me.

Thank you

Let me know if it fixes it for you, it did for me. Was quite useless before, as it shows 1 new email where indeed there were 20 in the box... or used to show 1 and there were none ! Now is perfect since the "upgrade".

---

### Post by andreselsuave on 2011-12-07
> **typhoon_tip said:**
> Let me know if it fixes it for you, it did for me. Was quite useless before, as it shows 1 new email where indeed there were 20 in the box... or used to show 1 and there were none ! Now is perfect since the "upgrade".

Ok, I will test it some more. I will post if I still got the issue.

---

### Post by andreselsuave on 2011-12-09
The issue is still there in 8.0 :(

---

### Post by typhoon_tip on 2011-12-09
> **andreselsuave said:**
> The issue is still there in 8.0 :(

Oooops, what kind of email server are you using ? IMAP/POP3 of some famous systems like GMail etc, or personal email system ?

---

### Post by andreselsuave on 2011-12-09
I have 2 accounts: 

- IMAP gmail 

- IMAP university account

---

### Post by typhoon_tip on 2011-12-09
> **andreselsuave said:**
> I have 2 accounts: 

- IMAP gmail 

- IMAP university account

How long are you using Thunderbird, with that profile, and especially do you remember how many versions you were using over those files ? For instance for me, I started with 3.x and Ubuntu Lucid, then moved on till now, 8.0, and never have to do any rebuild in order to correct "corrupt" data.

---

### Post by andreselsuave on 2011-12-09
I believe this profiles were configured with the shipping version of thunderbird in 11.10, I guess it is 8.0.

---

### Post by typhoon_tip on 2011-12-09
> **andreselsuave said:**
> I believe this profiles were configured with the shipping version of thunderbird in 11.10, I guess it is 8.0.

This means you never get back from previous installs your historic data ? Just work with online data / IMAP ?

---

### Post by andreselsuave on 2011-12-09
yeah, this accounts haven't been through an upgrade process if this is what you're asking. If I test it now in a 11.10 live usb the issue will be there. That's why I think it is a bug of thunderbird 8.0

---

### Post by typhoon_tip on 2011-12-09
> **andreselsuave said:**
> yeah, this accounts haven't been through an upgrade process if this is what you're asking. If I test it now in a 11.10 live usb the issue will be there. That's why I think it is a bug of thunderbird 8.0

Pal, TB8.0 only comes with an update, by default is the old (bugged) one, even in live CD. Make sure you have 8.0 and you have updated your system with all updates included the one in the Proposed repositories.

EDIT: in other words, without installing 11.10 and updating fully, you can never see this bug disappear.

---

### Post by andreselsuave on 2011-12-09
Oh, I didn't have the proposed sources active. I will upgrade and re-test. Thank you!

---

