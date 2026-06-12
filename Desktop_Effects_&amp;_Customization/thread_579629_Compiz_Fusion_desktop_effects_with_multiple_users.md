---
title: "Compiz Fusion desktop effects with multiple users"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by Martin_sensei on 2007-10-18
Hello all,

I recently got Compiz Fusion working with my ATI X1900XT card and it looks amazing!  

However when I change users and try to enable desktop efects for the second user (after changing the session to GNOME with XGL) the computer locks up!

I have tried restarting the machine and logging on as this second user (who is a desktop user by the way) and I can start a GNOME with XGL session. However When I try to enable desktop effects the computer locks up and I can't log out.

Do I need to configure XGL for this second user in a similar way to the original user?  (I used this guide[http://ubuntuforums.org/showthread.php?t=488385]("http://ubuntuforums.org/showthread.php?t=488385") to set up Compiz Fusion)

Please help! It would be nice for all users to have nice wobbly windows and of cource, the cube!

Regards,

Martin

---

### Post by Martin_sensei on 2007-10-22
Just in case anyone else comes across the same problem I can help with some of it:

The desktop effects crashing for the second user was due to me forgetting to add compiz and emerald to the session startup items.  With these in place every user can have compiz fusion effects.

However I still can't change users, logging off then logging in as a different user still locks the system completely.  

Any ideas about this remaining problem would be much appreciated!

Cheers

---

