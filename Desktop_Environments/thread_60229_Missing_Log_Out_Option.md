---
title: "Missing Log Out Option"
date: 2005-08-26
forum: Desktop Environments
---

### Post by the.tsr on 2005-08-26
I've looked around on the forums to see if anyone else has had this problem but to no avail.. I copied over my home folder from my desktop computer to my notebook and now under "Log Out" underneath "System" the dialog box that gives you the options to shut down, restart, etc. have mysteriously disappeared. Also when I created another user the option was still on that menu. Any suggestions on how to get this feature back?

 ](*,)

---

### Post by autocrosser on 2005-08-27
I've created a user with the same name/user id before--gave the user the same log-in---then copied my old info into the "new" user directory--don't seem to have any problems this way--

Don't know why you account did this--might try like above & see if it works for you---

---

### Post by twelvegates on 2005-08-27
As a workaround you can add the *Log out* applet to the pannel.
Right-click pannel -> Add to Pannel...

---

### Post by the.tsr on 2005-08-27
[QUOTE=twelvegates]As a work around you can add the *Log out* applet to the pannel.
Right-click pannel -> Add to Pannel...[/QUOTE]

Tried this, still no option to shutdown or restart, just immediately takes me to the GDM login screen.

---

### Post by DancingSun on 2005-08-30
Is it your laptop or the desktop that's having this problem?

Assuming it's your laptop, is your desktop also running Ubuntu?

I'm guessing that you might have overwritten some hidden files on the laptop which caused some settings to be lost.  But that only makes sense if your Desktop is running another OS where it didn't have the logout screen configured, thus when copying the home folder over, it overwrote some configuration files.  Or maybe some mismatched configuration file messed up the GNOME session and somehow caused the logout dialog to disappear.

But I'm just making a wild guess here, so I could be completely wrong....

Have you tried creating and logging in as another user?  Is the logout dialog still missing?

---

### Post by the.tsr on 2005-09-01
[QUOTE=DancingSun]Is it your laptop or the desktop that's having this problem?

Assuming it's your laptop, is your desktop also running Ubuntu?

I'm guessing that you might have overwritten some hidden files on the laptop which caused some settings to be lost.  But that only makes sense if your Desktop is running another OS where it didn't have the logout screen configured, thus when copying the home folder over, it overwrote some configuration files.  Or maybe some mismatched configuration file messed up the GNOME session and somehow caused the logout dialog to disappear.

But I'm just making a wild guess here, so I could be completely wrong....

Have you tried creating and logging in as another user?  Is the logout dialog still missing?[/QUOTE]

Desktop is also running Ubuntu and still has logout dialog. Other users on my laptop still have the logout dialog, 

So let's say I deleted some hidden files, is there some way of knowing which one/ones I deleted and what they should be restored to?

---

### Post by DancingSun on 2005-09-01
[QUOTE=the.tsr]Desktop is also running Ubuntu and still has logout dialog. Other users on my laptop still have the logout dialog, 

So let's say I deleted some hidden files, is there some way of knowing which one/ones I deleted and what they should be restored to?[/QUOTE]
OK, good, so at least the other users still have the logout dialog, that means it's just a localized problem for your user account.

As for which hidden files....well, that's a bit harder, I tried searching for "the" file that specifies the menu systems, but couldn't find it.

Hey! Just got another idea.  Open up System --> Preferences --> Sessions from the menu.  You should see a "Ask on logout" check box.  Make sure it's checked.  See if that works.

---

### Post by the.tsr on 2005-09-02
[QUOTE=DancingSun]OK, good, so at least the other users still have the logout dialog, that means it's just a localized problem for your user account.

As for which hidden files....well, that's a bit harder, I tried searching for "the" file that specifies the menu systems, but couldn't find it.

Hey! Just got another idea.  Open up System --> Preferences --> Sessions from the menu.  You should see a "Ask on logout" check box.  Make sure it's checked.  See if that works.[/QUOTE]

-Purrs and huggles- We have success! You have ended my torment, thanks so much!

---

### Post by DancingSun on 2005-09-02
[QUOTE=the.tsr]-Purrs and huggles- We have success! You have ended my torment, thanks so much![/QUOTE]
Heheh, glad that I can help. :D

---

