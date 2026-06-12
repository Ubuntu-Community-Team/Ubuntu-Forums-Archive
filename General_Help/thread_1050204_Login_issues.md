---
title: "Login issues"
date: 2009-01-25
forum: General Help
---

### Post by pells09 on 2009-01-25
All of a sudden I can't login. When I enter my password it returns me to the login screen. I know for a fact that it is the right password and username. I can't get past the login screen anymore. Any help would be appreciated.

---

### Post by bapoumba on 2009-01-25
Have you been doing anything special before you were logged out? Install new packages or tweak some config files ?
Are you sure you do not have capslock on ?

In any case, here are detailed steps to reset your user password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by taurus on 2009-01-25
At the GUI login screen, press <Ctrl><Alt>F2 and see if you are able to log in with your username and password.  If you can't, then try to reset your password from the link above.  But if you can, then perhaps you are running out of space on / (/tmp to be more specific)!

```
df -h
```

---

### Post by bapoumba on 2009-01-25
taurus +1 thanks :)
(I thought there was some kind of message now when / is running full, am I wrong? Edit: has this been ever implemented? [https://blueprints.launchpad.net/ubuntu/+spec/full-filesystem-sanity-gutsy](https://blueprints.launchpad.net/ubuntu/+spec/full-filesystem-sanity-gutsy))

---

### Post by taurus on 2009-01-25
> **bapoumba said:**
> 
(I thought there was some kind of message now when / is running full, am I wrong?)

Yes, there is (has always been) when one tries to log in (to a window manager) with / at 100% but it doesn't hurt to double check since some people either don't read it or don't bother to report it.  ;)

---

### Post by bapoumba on 2009-01-25
> **taurus said:**
> Yes, there is (has always been) when one tries to log in (to a window manager) with / at 100% but it doesn't hurt to double check since some people either don't read it or don't bother to report it.  ;)
Okay thanks :)

---

### Post by pells09 on 2009-01-25
I made a new password, but I still can't login. Before this happened I was trying to add a printer with CUPS. Any help would be appreciated.

---

### Post by bapoumba on 2009-01-25
So please boot again in recovery mode and run the comand taurus suggested:
```
df -H
```
If you see that a partition is full, try to make some room.
```
sudo apt-get clean
```
will make some room on /

Try to see if you can also remove unnecessary files from your /home.

---

