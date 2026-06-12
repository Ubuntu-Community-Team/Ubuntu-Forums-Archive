---
title: "Can't login via graphical login manager"
date: 2016-06-21
forum: Desktop Environments
---

### Post by Christian_Kloiml on 2016-06-21
Hi!

My problem is that i cant login into my graphical system, however i can via each of the consoles. Somehow it seems to me that the validation of the password is broken? If I type sudo startx at the command prompt the graphical system starts and I am logged in as root user, but on the graphical terminal i am not able to login. Everytime I want to login into the system, it is black for a short time, and then the login screen appears again without any error message. I also searched the Xorg log files but wasnt able to find any error messages. Maybe it works, if I turn off the login screen and the timeout for the login screen after some time of inactivity but I didnt try this yet and it should definitely not be the first option for me.

Does anyone know how I can "debug" this issue or did anyone have a similar issue like this?

If you need more information, please write me, i will provide you the information.

Thanks and kind regards,
Chris.

---

### Post by steeldriver on 2016-06-21
Hello and welcome to the forums

There may be other underlying issues, but running' sudo startx' itself is what often causes this

Running startx with sudo is a well known no-no - it results in root  owning the .Xauthority file in the user's home directory. When you try  to log in to a graphical session as your ordinary user, you can't write  to that file if root owns it - and so the session fails.

From one of the consoles, check with

```

ls -l ~/.Xauthority

```

It's also worth checking the ownership of the .ICEauthority file if it exists, of the home directory itself

```

ls -l ~/.ICEauthority

ls -ld ~/

```

Fixing is usually just a matter of resetting the appropriate ownerships.

---

