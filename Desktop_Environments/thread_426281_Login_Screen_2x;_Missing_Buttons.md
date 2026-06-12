---
title: "Login Screen 2x; Missing Buttons"
date: 2007-04-28
forum: Desktop Environments
---

### Post by jkzubu on 2007-04-28
Following an upgrade to Fiesty, I would like to resolve the following:

My Login screen appears twice and requires me login twice (User1) before launching into the Gnome desktop.  Following the first login and <enter>  the 'black' screen hangs for a minute or two and then the login screen reappears.  After I enter my login info the second time, Ubuntu logs into my User1 account.

Second, can someone please direct me to the location of the "Logout Window" file?  I would like to look at this file for both my User1 and User2 accounts to examine the differences.  Previously, my User1 account was missing the Hibernate, Shutdown, and Restart buttons.  After following some suggestions for a fix in these forums (by making changes to: System>Admin>Login Window), pressing the: System>Quit button now results in immediate termination of the desktop and brings up the Login window.  I am able to shut down from there.  

Out of curiosity, I created my User2 account to see if both of these problems persist.  The Login problem persists and the shut down problem is normal in User2.  

Thank you.

---

### Post by jkzubu on 2007-05-01
Somebody must have an answer...!

---

### Post by shaggly on 2007-06-14
I appear to have the same problem at the moment, but I have also noticed that it seems to have occurred since I upgraded Kernels - note upgraded kernels **only**.

I'm running Dapper with kernel 2.6.15-28

From looking at my sys log, I noticed that there appears to be a common thread at the time that the delay seems to occur, in that it states "No module symbols loaded - kernel modules not enabled." and then "Symbols match kernel version 2.6.15"

I know that this message might also be due to a couple of self-compiled modules that I have loading on startup, but it's also causing a delay of 16 seconds, which seems about the right time interval between the two logins.

With a little bit of hunting around I found that although using synaptic to upgrade the kernel source works fine, it doesn't also include the linux-header packages as part of that upgrade process.

I have installed those, and hopefully that will take care of the double logging in.

If I don't post here after this, then you know that this cured the problem...

---

