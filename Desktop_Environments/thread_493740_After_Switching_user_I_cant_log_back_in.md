---
title: "After Switching user I cant log back in"
date: 2007-07-06
forum: Desktop Environments
---

### Post by waggygee on 2007-07-06
I clicked switch user so I can log into my little brothers user (and it logged in perfectly) but when I tried to log into my user again (after logging out of my little brothers account) I got a black screen (the cursor was present and did respond)...

---

### Post by lisati on 2007-07-06
I hadn't actually noticed until now, but I was getting this too on my laptop. What seemed to work for me went something like this:
[LIST=1]
[*]From System->Administration->Login Window, select "Restart X-Server with every login"
[*]Restart
[*]From System->Administration->Login Window, click on the "local" tab
[*]For "Theme", choose "selected only"
[*]Choose your preferred login screen
[*]Go for it!
[/LIST]
I'm not sure why (or which part) this worked. Hope it helps!

---

### Post by evny on 2007-07-06
That's interesting.  I just tried adding a new user and when I went to "Switch User" I just got a black screen.  The same happened when I tried to log out and log in as the new user.  I'll have to try the "restart X" option.

---

