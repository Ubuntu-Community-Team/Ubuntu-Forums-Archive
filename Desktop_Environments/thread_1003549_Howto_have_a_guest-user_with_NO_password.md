---
title: "Howto have a guest-user with NO password?"
date: 2008-12-06
forum: Desktop Environments
---

### Post by jdackle on 2008-12-06
Hi folks!

Using Ubuntu Hardy Heron here.

What I want: To have a "*guest*" user with NO password.

Tries so far and results:

1. 
System -> Administration -> Users and Groups
User MUST have a password, no way around this through this GUI...

2.
```
sudo adduser --disabled-password guest
```
Oddily enough, password is still asked for on both GDM and text-console logins. :confused:
Ok, don't give up. Try this now you've got your guest user created:
```
sudo passwd -d guest
```
Ok, text-console logins now work perfectly (no password asked, just enter "guest" at the login prompt and you're in! ;)
Now enter "guest" at the gdm login. You're still asked for the password... Ok, just try pressing <Enter>. Nope, "Wrong password" is the answer... :(


So, in brief:
I've successfuly created an user that has no password but can still login at the text-console BUT gdm does not seem to accept such thing.

Anyone know how/where can I fix this?

TIA

---

### Post by torelli on 2008-12-06
try this:

sudo sed -i 's/#PasswordRequired=false/PasswordRequired=false/' /etc/gdm/gdm.conf

---

### Post by jdackle on 2008-12-08
That was a good hint, torelli! But unfortunately, it didn't seem to change anything. :(
The comment for that option in /etc/gdm/gdm.conf refers to another file that may override that setting but the said file does not exist on my system, so... 
On the other hand, there may be some additional tweaking that needs to be done to /et/gd/gdm.conf - I'll try and find it and post the results here.

In the meantime, if someone has another suggestion, it will be greatly appreciated. :)

---

### Post by skintythe1andonly on 2008-12-09
Im setting up the same thing at the moment. I found this thread
[http://ubuntuforums.org/showthread.php?t=513820](http://ubuntuforums.org/showthread.php?t=513820)

havnt tested it yet, though let me know how it goes

---

### Post by jdackle on 2008-12-12
Thanks, skintythe1andonly!

That did WORK! :)
Turns out the password I had for my user "guest" in /etc/shadow was none BUT NOT the _encrypted nothing_ you'll find in the howto you've provided the link to. I.e., in my /etc/shadow, I had: ```
guest::
``` instead of ```
guest:U6aMy0wojraho:
```
That worked in the text-console w/O even asking for a password (which was actually pretty cool) but not on GDM (which asked for a password and did not accept a mere <ENTER>).
Now, on both text-console and GDM, I get asked for a password, but just hiting <ENTER> proceeds to starting the guest session.


HOWEVER, I have experienced the issue reported below: > **balance07 said:**
> I have a problem with this method:

i can login fine w/ no password to my "guest" account, but can't get BACK into it after switching user to a normal account, then trying to get back to the guest account. can't unlock the guest account screen. any tips?
I will try and see if a solution to this is mentioned somewhere along that thread and if so link to it here.
If not, the author of that howto also refers and links to another similar, more coplicated, howto to setup a passwordless user. I may try that other method too and see if that solves the problem.

But as I do have a passwordless user in my system now, I will now mark this thread as SOLVED (hope I can still post replies to it later...).

---

