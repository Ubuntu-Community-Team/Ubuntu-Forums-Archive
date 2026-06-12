---
title: "GDM loop at login"
date: 2010-10-19
forum: Desktop Environments
---

### Post by HappyJaZZ on 2010-10-19
Hey folks!

**_Problem:_**

I have a kinda strange problem... Just installed 10.10 a few days ago, got my FORTRAN compilers setup and everything running smooth.

However, at one session i hit the "Suspend" button instead of the "Restart", and the computer went to a black screen, blinking cursor and nothing happened. I suspect it's because I don't have a swap drive, but I had to hit the powerswitch.

When I rebooted into Ubuntu again I was greeted with a login screen (it's called GDM, right?) even though I have activated automatic login. Everytime I enter my password and username the screen blink, and return to the GDM login screen.

**_Attempted solutions:_**

Hitting Alt+CTRL+F# gives me a console, but I cant seem to do anything useful there (i.e. does not recognize sudo), but booting into recovery mode gave me access to a root terminal.

_First Attempt_

I have tried to remove and reinstall GDM as suggested in this post [http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9245994&postcount=10](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9245994&postcount=10)

   apt-get remove GDM
   apt-get install GDM
   apt-get install gnome-session

but with no succes.

_Second Attempt_

Tried to use "purge" instead of "remove" (not quite sure what the difference is, though)

   stop gdm
   apt-get purge gdm
   apt-get install gdm

again no change.

_Third Attempt_

According to [http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9252459&postcount=11](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9252459&postcount=11) I could install WDM instead.

   stop gdm
   apt-get purge gdm
   apt-get install wdm

This gave me semi succes. I got a new login program (WDM) and it actually allowed me to login. 

However, I have modified my bashrc file and used some other settings (I have to ssh a firewall in order to get internet), and it seems like WDM does not load any of my settings, so if possible I would very much just et GDM working instead

_So what now..._

Well this is as far as I've gotten. Any suggestions?

**Thanks in advance!**

---

### Post by HappyJaZZ on 2010-10-21
Nothing...?

---

### Post by HappyJaZZ on 2010-10-22
I found the problem!

I edited my /etc/environment file, since I thought it would be able to source the environment for my intel fortran compiler. However, it seemed like that didn't work, and instead made the xserver crash (or something like that).

Restoring /etc/environment to its previous state solved everything!

---

