---
title: "[SOLVED] GnuCash OFX account setup crashing"
date: 2009-03-29
forum: General Help
---

### Post by cdurst on 2009-03-29
I finally solved a problem that has been blocking me from upgrading my financial system to anything newer than Gutsy.

It worked in GnuCash 2.2.1 (aqbanking-3.99.6beta built from source).

It fails on gnucash-2.2.6 (libaqbanking20-3.5.1-1).

For the last year, I've been trying to solve this problem and the workaround turned out to be so simple!

The problem:
When setting up an online banking account, I start the aqBanking wizard, I bring up the dialog to create a "New User", I fill in all the data following the description in ["Setting up OFXDirectConnect in GnuCash 2"]("http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2").

Then, I attempt to download the accounts by clicking on the "Get Accounts" button on the OFX tab of the New User dialog.

The Wizard then crashes with the following messages:
```

3:2009/03/29 13-16-10:aqbanking(14182):qbanking.cpp:  420: No Qt translation found for your language en
3:2009/03/29 13-16-11:gwen(14182):dbrw.c:  963: open(/home/user/.aqbanking/shared/qbanking/settings.conf, O_RDONLY): No such file or directory
3:2009/03/29 13-16-29:qt3_wizard(14182):qbcfgtabpageusers.cpp:  149: Selected backend: aqofxconnect
qt3-wizard: buffer.c:987: GWEN_Buffer_AppendString: Assertion `buffer' failed.

```

For many months I've tried everything I could think of.  I Googled every combination I could think of, I tried out various updates, I downloaded the source, compiled it myself, and even tried debugging it with GDB.  The assertion failure seemed to happen when it tried to access a "user" field while attempting to construct the message to send to the banking site (from what I can remember).

Today I found a workaround.

**Do not push the "Get Accounts" button while setting up a "New User".**  Instead, hit the "OK" button to finish user creation, then select that new User from the "Configuration" dialog, edit the user using the "Edit" button, switch back to the "OFX" tab you were on a moment ago, and **now** hit the "Get Accounts" button.

It looks like the "Get Accounts" button is ignoring the current entries in the "User Configuration" dialog, and only using the entries that have previously been saved out to the overall "Configuration" dialog.

Anyway, I hope this helps anyone else out there who's trying to find an answer to this problem.

---

