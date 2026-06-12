---
title: "Sudo error - Missing root password?"
date: 2005-12-23
forum: General Help
---

### Post by murkin on 2005-12-23
I installed a clean installation of Ubuntu.
User: ***administrator***, Password: ***password***.

I decided that I wanted the user to be admin. It's not possible to edit the username so, I created a new one named admin. I then logged in as admin and deleted administrator. Now I can't run anything that requires root permissions!

The password for both administrator and admin are the same. I'm not sure how to fix this. I hope you're able to follow.
Thanks for the help!

(by the way, this is within a vmware image).

---

### Post by aysiu on 2005-12-23
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by murkin on 2005-12-24
hi aysiu,
Thanks for the link. I still don't understand what I'm supposed to do though.

"The first user created is part of the admin group, which can use sudo. Any users created after that are not by default. It is recommended that all users of Ubuntu use sudo, as it provides clear benefits to security."

I deleted the first user though. When I created the 2nd user, I made sure it had the same permissions as the 1st. 

Whenever I go back in to run the "users and groups" app via gui, nothing happens. No indication of what is going on and no request for root password. The program does not open; all I see is the "working" action of the mouse pointer.

Trying to start an app within terminal seems to do the same thing. i.e. sudo gedit does nothing, though gedit, of course, does open the program.

I just tried going to system tools --> run as a different user and ran users-admin. First came an error message stating "choose password for default keyring. The application 'gksu' wants to store a password, but there is no default keyring. To create one, you need to choose the password you wish to use for it". I entered the same password as before..."password".

I was then asked for the password to run users-admin, but it does not work.  "Failed to run gksudo users-admin: wrong password." Same error if I only run "users-admin" (no gksudo).

...

I just logged out and back in again. Clicked the users-admin gui app. Again, nothing happened. Then I tried running it again via "run as a different user". A new error message popped up. "The application 'gksu' wants access to the default keyring, but it is locked." I entered "password". Then the normal window popped up asking for the root password. Still a no go...! 

Any ideas?

---

### Post by murkin on 2005-12-24
Alright...I'm up and running. I found the solution at the links below and modified it a bit to suit my specific situation: [http://www.ubuntuforums.org/showthread.php?t=93150](http://www.ubuntuforums.org/showthread.php?t=93150)
[http://www.ubuntuforums.org/showthread.php?t=105973](http://www.ubuntuforums.org/showthread.php?t=105973)

Solution:
- boot in recovery mode (this boots ubuntu and logs you in as root.
- locate and if necessary add in etc/sudoers "%admin ALL=(ALL) ALL" (replace %admin with whatever group you need to have sudoers rights)
- locate and add in etc/group "admin:x:106:admin, joe, bob, jane" (or whatever other users you want to be membes of the group)

the edits would have to be made in visudo or nano since you'd be working from terminal.

as an alternative, you can simply type "startx" once ubuntu boots in recovery mode. this would start the gui and you'd be able to browse to the files in nautilus, double-click, and make the necessary edits.

after making sure i was in both files, i ran the users-admin tool again. oddly enough, when i went into my user properties, i had no permissions except for maybe one. i am 100% sure that i had checked off of the boxes when first creating the user account.

anyway, all is better now. thanks!

---

