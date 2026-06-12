---
title: "Login screen"
date: 2013-05-23
forum: Desktop Environments
---

### Post by stuartbh on 2013-05-23
Ubuntu users:

I recently did an upgrade to Ubuntu 13.04 and have noticed a change in how the login interface behaves. There is a background of dots that is purpleish and orange. I have about 7 or 8 users to select from, and with one particular user it turns the entire screen of dots back and darkly colorless. Any ideas what might be causing this?

Thanks!


Stuart

---

### Post by dino99 on 2013-05-24
similar thread: [http://ubuntuforums.org/showthread.php?t=1902640](http://ubuntuforums.org/showthread.php?t=1902640)

if only one user login is borked, then either set a new user to replace that one, or edit its config settings to looks like the other good users login.

---

### Post by stuartbh on 2013-05-24
What configuration settings, in what file and in what directory are you referring to in specificity that you suggest need to be changed in order to effect this issue?

It is of course no problem to backup or copy whatever configuration files you are talking about to test it. What say you?


Stuart

---

### Post by grahammechanical on 2013-05-24
The standard (default) login background image is called warty-final-ubuntu.png. You can see it in System Settings>Appearance. You can find it at usr/share/backgrounds.

If a user selects the rotating set of wallpaper backgrounds then we get warty-final-ubuntu.png as the login background image.

If a user selects a static wallpaper as a desktop background, then we get that static image as the login background.

I suggest that you investigate what this user has been doing. What background wallpaper has he/she chosen? Has he/she installed a wallpaper from the internet that is causing a conflict?

---

### Post by stuartbh on 2013-05-24
Sir,

I think you are talking about the wallpaper that is seen **_after_** a user logs in, that is _**not**_ what I am talking about. I am talking about the background that one sees when they are selecting a user from the list of users on the login page **_before they login or enter their password_**. In 13.04 it has a huge number of dots all over the screen (at least my default look does).

That is the background that is changing to "black non-color" for when only one of the 7 or 8 users that are there are selected. For all other users there is no change change to black, just this one user in particularity in _**precedence**_ to even typing in the user's password or logging in.

Thanks.


Stuart

---

### Post by zombifier25 on 2013-05-24
You are probably upgrading from a pre-12.04 release. In 12.04 and later releases, LightDM (the login screen) changes background corresponding to the selected user's background. For example, if a user has a background of blue clouds, then when selecting that user on the login screen, the background will automatically change to blue clouds.

The user that made the background became black probably has a faulty desktop background or something. You should investigate.

---

### Post by stuartbh on 2013-05-24
Sir,

The version of Ubuntu that was installed in precedence to the upgrade was in fact 12.10 (although the 12.10 installation was installed as an upgrade to 12.04 at the time of 12.10's release).

The kind of behavior that you are describing is not what is being observed at all. In fact, the user's background is entirely blue yet the background change on the lightDM login screen is merely going from the colorized "dots background" to a monochrome-ized entirely black version of the same background. However, if you believe that this is due to the user's wallpaper choice, I can certainly login to that user, change the wallpaper and see if the bahaviour of LightDM changes when logging in next.


Stuart

---

### Post by stuartbh on 2013-05-30
Forum members,

Well the issue stopped occurring recently as magically as it started. Odd for sure, though all seems to be okay in my windowing environment now. Perhaps something got updated and fixed it - who knows?


Stuart

---

