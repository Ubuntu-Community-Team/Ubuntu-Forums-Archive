---
title: "Need help resetting user password"
date: 2011-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ntonline on 2011-01-15
I need help resetting my user password, not the initial login password.  When I start Ubuntu 10.10, I have the system configured to start up without a password.  I am able to use the system as long as I don't let the computer go into standby.  When the system enters standby, I am prompted to enter my user password, but I don't know what it is.  I thought I removed the password, but leaving the cell blank doesn't authenticate.  I then have to reboot to get back into the system.  Very frustrating.  

I run into the same issue with a failed password authentication when attempting to add additional applications through the Ubuntu Software Center.  I am the only user on the system.  I need help resetting this user password.

System Details:
Dell Dimension 3000
Ubuntu 10.10 32-bit

I have already logged in to root shell and reset the user password using password command, but that did not reset the user password for the particular issues mentioned above.  If I need to I'm open to deleting the only user account I have to create a new one.

---

### Post by gbrainin on 2011-01-15
You can try resetting the password in recovery mode, as shown here: [http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

However, your setup seems strange.  The default Ubuntu setup has the root password disabled, and the first user has root privileges accessible by using sudo.  In other words, normally on a one-user system like yours, there is only one password, not separate login, user, and root passwords like you're describing.  If you've modified your system from the default setup, then you may need to do something different to fix the problems you're experiencing.

---

### Post by ntonline on 2011-01-16
I've reinstalled Ubuntu and now have no issues with seperate passwords.  I don't know how that happened, but it did.  I could not figure out a fix so I just re-installed.

---

### Post by gbrainin on 2011-01-16
Well, good to hear that it's working now!

---

