---
title: "update-manager doesn't run from desktop button"
date: 2005-05-02
forum: Desktop Environments
---

### Post by amosshapira on 2005-05-02
Hello,

I've installed Ubuntu 5.04 on an AMD Athlon with pretty much default settings
(used the expert mode but hardly touched the options).

When I login to my user and hover the cursor over the update manager button
at the top right corner it says "There are 5 updates available".

When I press on it it brings up a "Changing user..." window asking for the password.
I type in the password and then, invariably, it comes up with a "Failed to run /usr/bin/update-manager: Child terminated with 1 status" error message.
The exit status sometimes changes to other values (2, 70) but it never
succeeds.

Any other option I try to choose (with right-mouse menu) also fails similarly -
ask for a password then fail with strange exit status.

Running update-manager used to fail but now that I execute it from a root
shell it seems to succeed.

What am I doing wrong?

Thanks,

---

### Post by neighborlee on 2005-05-02
[QUOTE=amosshapira]Hello,

I've installed Ubuntu 5.04 on an AMD Athlon with pretty much default settings
(used the expert mode but hardly touched the options).

When I login to my user and hover the cursor over the update manager button
at the top right corner it says "There are 5 updates available".

When I press on it it brings up a "Changing user..." window asking for the password.
I type in the password and then, invariably, it comes up with a "Failed to run /usr/bin/update-manager: Child terminated with 1 status" error message.
The exit status sometimes changes to other values (2, 70) but it never
succeeds.

Any other option I try to choose (with right-mouse menu) also fails similarly -
ask for a password then fail with strange exit status.

Running update-manager used to fail but now that I execute it from a root
shell it seems to succeed.

What am I doing wrong?

Thanks,[/QUOTE]
-----------
it sounds like you are using your actual root password ( which for sake of post Ill assume you made ) instead of your 'users' password..

with luck thats it ;-))

cheers
neighborlee

---

### Post by amosshapira on 2005-05-02
[QUOTE=neighborlee]-----------
it sounds like you are using your actual root password ( which for sake of post Ill assume you made ) instead of your 'users' password..

with luck thats it ;-))

cheers
neighborlee[/QUOTE]

:) I suspected this is going to be the first question but forgot to mention this -
I tried both my password and the root password (both of them are non-empty).

---

### Post by matthieufecteau on 2005-05-03
Maybe (I'm not very sure ...) your problem is with the loopback interface not starting at boot.

To look further into that direction, read the second post of this thread : [http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback](http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback)

---

### Post by amosshapira on 2005-05-04
[QUOTE=matthieufecteau]Maybe (I'm not very sure ...) your problem is with the loopback interface not starting at boot.

To look further into that direction, read the second post of this thread : [http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback]("http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback")[/QUOTE]
Thanks for the pointer, but I have a loop-back interface configured right.
Anything else I can look at?
Thanks.

---

