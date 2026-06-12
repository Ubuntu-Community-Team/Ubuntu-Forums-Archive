---
title: "Users wont show up in login window."
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by seldomridgej on 2007-10-14
Ok, ive chosen a login window that has a user list box beside the username/password form.  However, no users show up in the box.  Ive looks through the security tab under Administration>login window but the excludes list seems fine and so does the minimal UID.  Anyone have a solution?

---

### Post by michael37 on 2007-10-17
Do the users have normal login permissions?  Users with crippled limited permissions cannot actually run the X session and won't show up (e.g., I have a user whose shell is /bin/false, and that user rightly doesn't even show up).

---

