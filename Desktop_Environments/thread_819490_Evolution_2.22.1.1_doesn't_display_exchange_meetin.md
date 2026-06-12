---
title: "Evolution 2.22.1.1 doesn't display exchange meeting invites anymore"
date: 2008-06-05
forum: Desktop Environments
---

### Post by patis on 2008-06-05
Hello,

Previous to the latest round of hardy updates evolution was happy dealing with meeting invites coming from our exchange server in the office. They usually showed up with a form where I would just click a button to accept/deny the invitation.

But I have that no more. Meeting invites are shown now in plain text with a URL link at the bottom that doesn't work for me. Something like this:

```
When: Thursday, June 05, 2008 3:30 PM-4:00 PM (GMT-06:00) Central Time (US & Canada). 
Where: Main office, Bridge: 325-5333, passcode 726# External 697-754-7562

*~*~*~*~*~*~*~*~*~*
Microsoft Outlook Web Access: http://ZCAXM0/Exchange/PATIS/Inbox/Finalize%20slide%2016%20-%20atics.EML?cmd=open

```

How can I get the old behavior restored (without having to downgrade evolution)? Anyone else experiencing this?

Thanks.

---

### Post by grahams on 2008-06-10
I reported this as a bug in evolution a few weeks ago. Surprising that 8.04 LTS (Long term support?) pick this up without a critical fix. 

Anyone heard of QA?

The fix is to go back to the previous evolution release.

---

### Post by cro on 2008-06-10
> **grahams said:**
> The fix is to go back to the previous evolution release.

Downgrading was a major headache, and for those who are having problems, try this:

REMOVE evolution first, all bar the required 'evolution-data-server-common'. You may have to remove some other packages because of required (but not actually required) dependencies.

Then DOWNGRADE evolution-data-server-common to 2.22.1-0ubuntu2

Once this has been done, Force Version 2.22.1 for evolution, evolution-common, evolution-data-server and evolution-exchange. 

This will restore the ability for Evolution to properly deal with "urn:content-classes:calendarmessage" type messages, and properly display the Accept, Tentative, Decline and Open Calendar buttons.

Until this issue is resolved, Evolution cannot be used as a Microsoft Exchange or Microsoft Outlook replacement in any organisation that relies on Exchange for calendaring.

One last thing, because this process forces an earlier version than the currently-available (Hardy Updates), these packages will persistently be marked for upgrade, so make sure to disable automatic upgrades until this bug is fixed - just make sure to untick all these components whenever you run upgrade manager.

---

### Post by Spyplane on 2008-06-11
This is so frustrating, and one of my complaints of all the recent updates.   How are we losing features by doing updates?   Time to start downgrading.

---

### Post by Spyplane on 2008-06-11
I fixed the problem:

Go to: Edit-> Preferences-> Mail Preferences-> HTML Messages Tab-> Plain Text Mode Section

Then change setting "HTML Mode" to "Prefer PLAIN"

This will fix your problem.

---

### Post by patis on 2008-06-12
Indeed, enabling this option shows the form at the bottom of the message. The text-only version still shows up at the top. It is still a bug though which I hope will be fixed soon.

Thank you for the hint.

---

### Post by djcrash1981 on 2008-06-12
I'm having this trouble to and it's so annoying.

The bypass worked for me but someone knows when this is going to be solve??? Or how can I fill a report???

Thanks

---

### Post by mailmrg on 2008-06-18
this blog seems to have identified the plugin that screwing things up
[http://geek.co.il/wp/2008/06/11/evolution-problems-with-ms-outlook-invitations](http://geek.co.il/wp/2008/06/11/evolution-problems-with-ms-outlook-invitations)

---

