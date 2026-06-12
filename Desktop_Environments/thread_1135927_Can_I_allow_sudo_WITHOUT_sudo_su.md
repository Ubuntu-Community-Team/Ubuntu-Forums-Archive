---
title: "Can I allow sudo WITHOUT sudo su?"
date: 2009-04-24
forum: Desktop Environments
---

### Post by sbsheetz on 2009-04-24
I would like to grant a user the ability to sudo, but NOT let them reach a root shell (sudo su, sudo -, etc).

I've seen a little discussion online about this, but nothing I've seen seem to work correctly.   This seems like a relatively simple thing to do, except that I haven't found how.

Any ideas?

---

### Post by inobe on 2009-04-24
hi and welcome, have you considered simply creating a user account ?

the user account will not be able to use su !

in fact' you will be the admin with su, the user will have a different password and will be incapable of making su system wide changes.

rough example

system> administration> user and groups> add user.

it is your responsibility keeping your admin credentials secrete.

---

### Post by sbsheetz on 2009-04-25
I have a number of local user accounts.  My personal account already has sudo.  I want to allow another user to sudo (for mounting, updating and installing software, managing printers, etc.), but do NOT want the other user to become root.

sudo is valuable in allowing a good audit trail of administrative activities by users, but sudo su (or sudo -) can be dangerous.

I guess another way of asking my original question is: if I can't PREVENT the use of 'sudo su' or 'sudo -' by sudoers, is there a good clean way to ALLOW my user the ability to mount volumes, install or update software, and manager their printers?

Thanks for any more help!

---

### Post by _Purple_ on 2009-04-25
> **sbsheetz said:**
> I have a number of local user accounts.  My personal account already has sudo.  I want to allow another user to sudo (for mounting, updating and installing software, managing printers, etc.), but do NOT want the other user to become root.

sudo is valuable in allowing a good audit trail of administrative activities by users, but sudo su (or sudo -) can be dangerous.

I guess another way of asking my original question is: if I can't PREVENT the use of 'sudo su' or 'sudo -' by sudoers, is there a good clean way to ALLOW my user the ability to mount volumes, install or update software, and manager their printers?

Thanks for any more help!

You can give the permission to another user(other than root) to perform only certain tasks by modifying the Sudoers file. Please have a look at the following thread
[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)
Hope that will solve your problem.

---

### Post by sbsheetz on 2009-04-25
Thank you Purple!   That gives me exactly what I needed.   The user will be able to use the administrative programs they need without being able to reach a root shell!

Mucho kudos!
:lolflag:

---

