---
title: "unity-greeter won't let me login"
date: 2014-11-21
forum: Desktop Environments
---

### Post by marcohnunez2 on 2014-11-21
Hi Everybody,

I'm using 14.04.1 on a Dell Latitude D630, the issue is that I had to remove and reinstall unity-greeter 'cause there was a problem logging in, after remove/install unity-greeter there's no way to log in with the user I had it appears on the log in screen (graphic mode I mean) but no matter that I type the correct password I just get: "Failed to start session" even if I'm sure the password I assing to my user is the right one...I can go to terminal mode (Ctrl-Alt-F1) change password but when I reboot the same thing happens and there's no way to login....


Would you please give a help on this issue....I don't want to format the HD once more...

Best regards,
Marco

---

### Post by kansasnoob on 2014-11-21
When you open the terminal try:

```
sudo apt-get install lightdm
```

Then:

```
sudo dpkg-reconfigure lightdm
```

Then:

```
sudo reboot
```

And see what happens.

---

### Post by marcohnunez2 on 2014-11-21
no success....the 1st: sudo apt-get install lightdm gave a list of things that no longer be needed so I had to run sudo apt-get autoremove, then dpkg-reconfigure lightdm gave no response and after reboot the same thing, no access...I'm stuck here don't know what to do....any suggestions are welcome

---

### Post by kansasnoob on 2014-11-21
Possibly this bug:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1312526](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1312526)

Are you offered any session choices? If so there would be an icon to the right of your user name (either a GNOME foot or gear) and if you click on it you should see a list of available sessions.

---

### Post by CantankRus on 2014-11-21
Are you aware removing **unity-greeter** also removes** unity**?
Log in via tty and run...
```
sudo apt-get install unity
```

Then reboot...
```
sudo reboot
```

---

### Post by deadflowr on 2014-11-22
Doesn't it also remove the ubuntu-desktop meta-package as well?

---

### Post by jhay2 on 2014-11-22
maybe try to change your greeter ? sudo apt-get install gdm .. and see what happen ..

---

### Post by CantankRus on 2014-11-22
> **deadflowr said:**
> Doesn't it also remove the ubuntu-desktop meta-package as well?
Yes it would, but didn't go the re-install ubuntu-desktop route in case there were other packages that may have been removed earlier
that the OP didn't want re-installed.
If preferred simulate installing ubuntu-desktop to see what packages are pulled in.
```
sudo apt-get install [COLOR="#FF0000"]--simulate[/COLOR] ubuntu-desktop
```

Happy with what is to be re-installed, remove the [COLOR="#FF0000"]--simulate[/COLOR] option.

---

