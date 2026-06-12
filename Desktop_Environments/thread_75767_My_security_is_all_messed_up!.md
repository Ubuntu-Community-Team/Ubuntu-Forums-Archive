---
title: "My security is all messed up!"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Corrado on 2005-10-14
I just installed a new copy of 5.10 over my old Slackware (which I still love :) and started playing with it.  Well, I must have done something terrible, because now I am having a hard time doing anything.  Whenever I try to run something from the menu it seems to start and then it quits after 10-20 seconds.   Sometimes I get a security prompt asking for my password so that the program I am trying to execute can run at elevated privileges but the program itself never shows up.  It just hides in the bottom panel and then goes away.  I don't get a dialog box or anything!

i tried to view the logs to see what's up but when I try to use the "System Log" program to view a file it tells me that I don't have permission to open it.  :(  What the heck is going on!?!  I added some new users by dropping into "Safe" mode and using the addusers command, but they had the same trouble.

I can open a shell and issue commands but they don't seem to work.  If I type sudo less /var/log/messages, it asks me for my password and then just returns me to my command prompt.  No bitching/moaning at all!   :(

I really really really wanted to like/use Ubuntu, but this is killing me.

Thanx!
  Richard

---

### Post by Corrado on 2005-10-14
Ok, thanks to someone on IRC I am back up and running now.  It appears that the only the very first user that you set up has admin rights.  Each subsequent user is not automatically put in the admin group.  So, I just modified the /etc/group file and added my userid to the "admin" group and all is well.  

Just for safety though, I set up a completely new user using the GUI tools and will be removing my "old" non-working user account.

Later...
  Richard

---

