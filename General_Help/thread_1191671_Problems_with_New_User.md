---
title: "Problems with New User"
date: 2009-06-19
forum: General Help
---

### Post by Martin_sensei on 2009-06-19
Hello,

I have just installed Jaunty on a clean machine, and was pleasantly surprised how easy it was:  ATI card worked, Sound worked, Wireless Network drivers worked...  I set up all my favorite desktop effects and added Japanese Language support (using SCIM), and was completely happy with my set up.

I then created a new user account for another user of the machine.  Logged in to test, and desktop effects could not be set and SCIM would not start.

I am not sure where to start looking to resolve these issues... Is there a way to clone a users settings maybe?

Cheers

Martin

---

### Post by redilyn on 2009-06-19
Did you add the new user to any groups?

You may want to add the new user to the admin group (unless you don't want them to have admin rights).

Check System -> Administration -> User & Groups

Check the properties for the new user.

---

### Post by Martin_sensei on 2009-06-26
Thanks for the reply!

I have now fixed all these issues.

The display issue seemed to be fixed by adding the user to the administrators group before logging on for the first time. (I deleted the user, created a new user in the admin group) then logged in, then set all the desktop effects I wanted, then restarted)

The keyboard issue was a lot simpler, I had to check the "Use an IME" option in the language support area once logged in as the new user.

Thanks again

Martin

---

