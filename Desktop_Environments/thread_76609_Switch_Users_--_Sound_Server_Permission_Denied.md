---
title: "Switch Users -- Sound Server Permission Denied"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Dromio on 2005-10-15
I installed Kubuntu on the family PC and was especially excited about the ability to ¨Switch Users¨ within KDE/KDM without losing the current user´s session.  It works great except, only the original user gets any sound.  All others get an error message on startup stating that permission to the sound device is denied.  

All users have the Hardware Device set to ¨autodetect¨.  Is there anything I can do to get past this?

---

### Post by t2kburl on 2005-10-15
sound is a group that needs to be checked when you add the user ... try editing the user profiles and add priviledges

---

### Post by Dromio on 2005-10-15
No, each user can play sounds fine if they are the only session on the system. The issue only arises when user1 logs in, then user2 logs in using KDMs &#168;Switch User&#168; functionality. User1 apparently has exclusive access to the sound system, so user2 gets the access denied message.

If user2 were to log in normally as the only session on the machine, they can play sounds without issue.

---

