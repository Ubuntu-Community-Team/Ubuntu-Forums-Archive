---
title: "Rollback from Firefox 16?"
date: 2012-10-11
forum: Desktop Environments
---

### Post by JordanH on 2012-10-11
Bah. I updated my laptop today using the Update Manager and it appears that Firefox was updated to Firefox 16.

Whatever changed has fixed some minor issues I was having but has created new issues for me.  I don't have time to resolve this on my laptop today and would love to roll-back my installation to some version prior.  Any ideas on how to do so?

Alternatively, if I can resolve the problem quickly then I'll do so.
Specifically, when accessing my web mail via Lotus iNotes 8.5.2fp4, the "Send" and "Save as Draft" functions no longer work.  I believe both are part of a Java applet.  Both worked under previous versions of Firefox and both work under current versions of Google Chrome.

I am on 12.04LTS, technically an Ubuntu install, but using KDE-Plasma.
I have completely purged Firefox from my system, including ~/.mozilla directory.  I then re-installed Firefox with no add-ons or extensions that may have been interfering.

Any thoughts?

Jordan.

---

### Post by dniMretsaM on 2012-10-11
16.0.1 is already in the repos. So just install Firefox again.

---

### Post by JordanH on 2012-10-12
> **dniMretsaM said:**
> 16.0.1 is already in the repos. So just install Firefox again.
Thanks.  I did this morning, but it is still borken.

---

### Post by dniMretsaM on 2012-10-12
Ok.I missed the Java thing in the first post. Do you have IcedTea installed ([FONT=Courier New]icedtea-6-plugin[/FONT])?

---

### Post by JordanH on 2012-10-12
> **dniMretsaM said:**
> Ok.I missed the Java thing in the first post. Do you have IcedTea installed ([FONT=Courier New]icedtea-6-plugin[/FONT]?

Yes and no.
Yes, it was installed when it was running the previous version of Firefox.
Yes, it was installed when I upgraded to 16.0.1
No, it wasn't running during some of the testing (I tried disabling it with no success.)
No, it's not available when I tested in Windows Vista. This issue is reproducible on that platform as well.

IBM had an issue with the same symptoms when Firefox 15 was released and was related to signed scripts.  However, the work-around for 15 does not fix the issue for Firefox 16.  I suspect I'll have to wait for IBM to get around to fixing iNotes rather than Firefox.

I managed to snag myself a tarball for Firefox 15 which I'm hoping will work until they get their stuff together.

edit: Here is the Mozilla link [https://bugzilla.mozilla.org/show_bug.cgi?id=546848](https://bugzilla.mozilla.org/show_bug.cgi?id=546848) that is at the root of the issue.  IBM says they have a work around for their Domino 8.5.3 server for now, and hopefully a proper fix soon/later.  Nothing more can be done... either go roll back or use another browser until it's fixed.

---

### Post by litiform on 2012-10-12
my ubuntu updated to 16.01 today.

---

