---
title: "Synaptic/UpdateManager Problems after Expert install."
date: 2005-10-15
forum: Desktop Environments
---

### Post by slackern on 2005-10-15
Im writing this since i saw alot of other similar which had the same problems but there i didn't find something that fixes this problem.

I'll start of with saying that this problem i had in 5.04 also as well as when i tried 5.10 now.

The problem only happens when selecting "expert" at the start of the installation and then selecting to enable "Shadow-Passwords" after that i proceed to set a root password and then a user password for my user.

All goes well and the system boots up and i'm greeted with that there are updates available for my system, i click the icon ... waiting ... well nothing happens, i go to System - Administrator - Synaptic Package Manager, hmm nothing not working there either.

I open up a console doing "sudo synaptic" enter the root password and it pops up, same with the update manager.

I start to wonder how this come to be, it never happens during a normal install when _not_ selecting "Expert".

I started looking at what groups I am in as a regular user but i'm not sure what groups i should be in as default, maybe someone with an install that wasn't installed with "Expert" can list the groups related to your account.

---

### Post by Underhill on 2005-10-15
Do this:

# sudo visudo

And add the following:

{your_username} ALL=(ALL) ALL

---

