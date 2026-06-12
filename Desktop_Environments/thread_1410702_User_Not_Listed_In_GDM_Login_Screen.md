---
title: "User Not Listed In GDM Login Screen"
date: 2010-02-19
forum: Desktop Environments
---

### Post by Palshife on 2010-02-19
I set up my netbook to where /home is on a separate so I could try out other distros from time to time. After giving Fedora and Linux Mint a try and not finding them to my liking, I re-installed Ubuntu 9.10. Only now, when I get to the login screen, it doesn't show my user face.

I checked my UID to make sure it's less than 1000, and that was fine. I then tried adding a new user to see if that would show up, and it did. I checked my gconf settings to make sure disable_user_list was set to FALSE, and it was. I read a suggestion to delete .gnome2 and .gnome2_private, and that didn't fix the problem, either.

Installing one of the distros changed some setting or another, and I haven't a clue what. Is there anything else I should check or delete?

---

### Post by bluefrog on 2010-02-19
your initial user has uid =< 1000?
in that case it is normal you don't see it. By design.

---

### Post by Hero of Time on 2010-02-19
Correct, in the GDM settings, it is noted that users with an ID below 1000 are not shown in the user list. So make sure it is 1000 or higher.

---

### Post by Palshife on 2010-02-19
Next time I should read the information I find more closely, huh.

Thank you, both of you. A usermod -u 1001 and everything's fixed.

---

