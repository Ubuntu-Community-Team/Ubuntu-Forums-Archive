---
title: "Evolution: unlock keyring"
date: 2009-01-30
forum: General Help
---

### Post by Boycraft on 2009-01-30
Evolution mail asks "Enter password for default keyring". What is it? Passwords of user and encryption key don't stop it from asking again and again.

---

### Post by kmac on 2009-01-30
System >> Administration >> Authorizations


I think...

---

### Post by Boycraft on 2009-01-30
More details: 
The window can't be moved. It can be only closed with X or by pushing the button.
text
Enter password for default keyring to unlock.
The application 'evolution' (/usr/bin/evolution) wants to access tot the default keyring, but it is locked.
> System >> Administration >> Authorizations
Nope. It's applications - encryption keys. The status bar of it says: access to default keyring denied. Strange. I've deleted the key - it's still asking.

---

### Post by Boycraft on 2009-01-30
The password it wants is my old user password.Strange: that keyring-thing password did not change when i changed my user password.
Solved!

---

### Post by fballem on 2009-02-04
When you change your password to login to your computer, the keyfile for passwords is not changed. On my system, Evolution is the only application that has a problem.

To fix when you change your password on your computer:

[LIST=1]
[*]Select Applications > Accessories > Passwords and Encryption Keys
[*]Choose Edit > Preferences from the menu. You will get a screen similar to the attached screenshot.
[*]Highlight the entry for 'login Automatically unlocked when the user logs in'
[*]When you select this item, the Change Unlock Password button is enabled. Select the button.
[*]You will then be able to change the password - enter your old password and your new password in the appropriate spots, then select the Change button.
[*]Select OK at each screen until the application closes.
[*]At this point, you may wish to test by restarting your system, then executing a Send and Receive from Evolution.
[/LIST]

That should do it. If this solves your problem, please don't forget to mark the thread solved so that other users may benefit from this thread.

Thanks,

---

### Post by bizmeds on 2009-03-22
thanks for the mini tut however when I followed the instructions I got an access denied to change the password. Any ideas

---

### Post by fballem on 2009-03-22
Sorry, no - I'm still in the learning curve. Hopefully, someone with more expertise than me will enlighten both of us.

---

### Post by serenityit on 2009-09-02
Hmm... we're getting this issue here with both Evolution Mail and trying to change the keyring password.

My password hasn't changed, and that is what I can't understand. Its just randomly started throwing a fit after doing some updates and rebooting.

Anyone got ideas? Its been 6 months since this thread got an answer!

---

### Post by Johnny B on 2009-09-02
this thread did not require an answer because fballem posted the solution
which part do you need help with?

sorry i should have read more carefully.
if you dont have the password, delete the login key, and create a new one. make sure to name it login.

---

### Post by serenityit on 2009-09-03
> **Johnny B said:**
> this thread did not require an answer because fballem posted the solution
which part do you need help with?

sorry i should have read more carefully.
if you dont have the password, delete the login key, and create a new one. make sure to name it login.

That solved it, thanks.

---

### Post by Emoria on 2009-09-10
> **fballem said:**
> When you change your password to login to your computer, the keyfile for passwords is not changed. On my system, Evolution is the only application that has a problem.
 
To fix when you change your password on your computer:

[LIST=1]
[*]Select Applications > Accessories > Passwords and Encryption Keys
[*]Choose Edit > Preferences from the menu. You will get a screen similar to the attached screenshot.
[*]Highlight the entry for 'login Automatically unlocked when the user logs in'
[*]When you select this item, the Change Unlock Password button is enabled. Select the button.
[*]You will then be able to change the password - enter your old password and your new password in the appropriate spots, then select the Change button.
[*]Select OK at each screen until the application closes.
[*]At this point, you may wish to test by restarting your system, then executing a Send and Receive from Evolution.
[/LIST]
That should do it. If this solves your problem, please don't forget to mark the thread solved so that other users may benefit from this thread.
 
Thanks,
 
 
OK, I currently have an older seahorse or something because mine dosnt look like that. I mean it looks like it but it dose not have the keyring thing... i cant access the net to update it. What do I do?

---

### Post by SoftPops on 2009-09-18
> **Emoria said:**
> OK, I currently have an older seahorse or something because mine dosnt look like that. I mean it looks like it but it dose not have the keyring thing... i cant access the net to update it. What do I do?
 
I have been having the same problem with Evolution since changing my login password. I too do not have the same tabs on "edit, preferences". What I have found is that after going into "Passwords and Encryption Keys" I have a tab called "Passwords" which gives me one entry "Passwords: Login", if I right click this there is a "Change Password" option. In here I have changed the password using my previous login password as the old password and my current one as the new password. This has been accepted by the system quite happily. I haven't been able to check it yet as I not connected to the net, certainly looks hopeful though.
 
I have now tried opening Evolution after making the change described above and I am no longer asked for a keyring password.

---

