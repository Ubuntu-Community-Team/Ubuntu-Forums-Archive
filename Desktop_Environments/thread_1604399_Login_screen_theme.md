---
title: "Login screen theme"
date: 2010-10-24
forum: Desktop Environments
---

### Post by shashanksingh on 2010-10-24
How can I install a new theme in 10.10 login screen?? 
I tried the login-window preferences but it doesn't have all the required options such as that of installing a new theme...

---

### Post by stinkeye on 2010-10-24
> **shashanksingh said:**
> How can I install a new theme in 10.10 login screen?? 
I tried the login-window preferences but it doesn't have all the required options such as that of installing a new theme...


Open the terminal and run
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
Then logout, and you’ll see an Appearance window pop up. Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command to prevent the Appearance window from opening at the GDM screen every time.
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by Boondoklife on 2010-10-24
I LOVE YOU, could not remember for the life of me how this worked. thanks!

---

### Post by stinkeye on 2010-10-24
. :oops:

---

### Post by exploder on 2010-10-24
stinkeye, thanks for posting the commands for the gdm theme. This seems to have fixed an issue I was having with plymouth not always displaying on shut down and reboot. I switched the theme to the same theme the desktop was using and the problem appears to be solved so far. Thanks!

Edit: I spoke too soon, the plymouth problem persists. Oh well, the gdm looks cool now.

---

### Post by Ptero-4 on 2010-11-20
The problem with plymouth not appearing at shutdown is because it was compiled without gdm support.

---

### Post by kaykelkar on 2010-11-20
@ stinkeye

Thanks for the info, but i suppose that guy was referring to those old login themes which we could change. the solution that you gave is more related to desktop theme....!!

Pls let us know if we can change the login themes...

---

### Post by stinkeye on 2010-11-20
> **kaykelkar said:**
> @ stinkeye

Thanks for the info, but i suppose that guy was referring to those old login themes which we could change. the solution that you gave is more related to desktop theme....!!

Pls let us know if we can change the login themes...

That is for changing the login theme.
I don't think you can completely change the look like before.

---

### Post by michael_teter on 2011-01-12
> **stinkeye said:**
> Open the terminal and run
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
Then logout, and you’ll see an Appearance window pop up. Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command to prevent the Appearance window from opening at the GDM screen every time.
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

This didn't help me.  It merely opens the normal Preferences->Appearance tool; it doesn't seem to have anything to do with the GDM/login screen.

And for whatever reason, the 10.10 version of the Administration->Login Screen app is stripped down from what it apparently used to be (where you could control look and feel).

So, what is the 10.10 procedure for installing themes or otherwise changing the appearance of the login screen?

---

### Post by Caver Chris on 2011-02-14
Worked for me, I followed the instructions from Stinkeye as posted. I was able to change the background on the login screen to something other than the standard and that what I wanted to do. :D

I'm running Ubuntu 10.10 BTW.

---

### Post by redbikemaster on 2011-08-01
Can you change the login *window* though?

The attached photo is want I want my login screen to look like, text box, buttons and all.

---

