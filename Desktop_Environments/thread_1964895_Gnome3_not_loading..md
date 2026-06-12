---
title: "Gnome3 not loading."
date: 2012-04-24
forum: Desktop Environments
---

### Post by dwaite on 2012-04-24
Hi all,

A few weeks ago I installed the Gnome 3 shell (just through the Ubuntu Software Center) and it was running fine. A few days ago I installed a batch of updates through the update manager and the desktop environment started to become quite unstable (the top bar would disappear for a few seconds, then return). This went on though a few resets (since I alternate between Windows and Ubuntu), and now when I log in I see nothing except my wallpaper.

I tried to do a gnome-shell --replace through the console and got the error message:

JS LOG: GNOME Shell started at Wed Apr 25 2012 09:33:48 GMT+1200 (NZST)
Window manager warning: Log level 16: The program 'gnome-shell' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadRenderRequest'.
(Details: serial 1404 error_code 179 request_code 161 minor_code 1)

I'm still fairly new to using Ubuntu so I don't have the experience to know where to start in solving this. I've done a few searches but haven't found anyone else reporting this problem. After I get this error through the console my keyboard locks up, and I need to reset the computer to do anything else.

Is there any advice or pointers anyone could offer?

Thanks.

---

### Post by RichardCain on 2012-04-24
Are you able to log out of Gnome shell and back into your previous DE?

---

### Post by dwaite on 2012-04-25
Yes, I can log in with classic gnome or Unity fine. Also, if I log into Gnome3 I can log out with Ctrl+Alt+Del (I haven't tried gnome-session-save --logout, but I assume that would work too).

---

### Post by techsupport on 2012-04-25
When I installed Gnome 3 in Ubuntu 12.04 I used the Gnome Team Developer PPA and these kinds of issues disappeared. It ran very solid after that. 

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

> **dwaite said:**
> Hi all,

A few weeks ago I installed the Gnome 3 shell (just through the Ubuntu Software Center) and it was running fine. A few days ago I installed a batch of updates through the update manager and the desktop environment started to become quite unstable (the top bar would disappear for a few seconds, then return). This went on though a few resets (since I alternate between Windows and Ubuntu), and now when I log in I see nothing except my wallpaper.

I tried to do a gnome-shell --replace through the console and got the error message:

JS LOG: GNOME Shell started at Wed Apr 25 2012 09:33:48 GMT+1200 (NZST)
Window manager warning: Log level 16: The program 'gnome-shell' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadRenderRequest'.
(Details: serial 1404 error_code 179 request_code 161 minor_code 1)

I'm still fairly new to using Ubuntu so I don't have the experience to know where to start in solving this. I've done a few searches but haven't found anyone else reporting this problem. After I get this error through the console my keyboard locks up, and I need to reset the computer to do anything else.

Is there any advice or pointers anyone could offer?

Thanks.

---

### Post by RichardCain on 2012-04-25
> **dwaite said:**
> Yes, I can log in with classic gnome or Unity fine. Also, if I log into Gnome3 I can log out with Ctrl+Alt+Del (I haven't tried gnome-session-save --logout, but I assume that would work too).

Then I would suggest logging in with Unity, purging gnome-shell with:
```
sudo apt-get purge gnome-shell
```
and then re-install with:
```
sudo apt-get install gnome-shell
```

---

### Post by dwaite on 2012-04-25
Thanks for the advice. I had tried uninstalling/reinstalling through the software center to no avail. Trying it through the console however, I get a few warnings that I'm running Natty and there are compatibility issues. It looks like when I upgraded from Natty to Oneiric there was some corruption or incomplete installation.

I've fixed that, and it seems to have made some progress. I now get the correct interface when I log in, but as soon as I try to do anything, it crashes to a black screen with only the mouse pointer displayed.

---

### Post by RichardCain on 2012-04-27
Upgrading in situ will always present an opportunity for possible corruption.

Your best bet here is to back-up your /home directory and then do a clean install of 12.04.

---

### Post by dwaite on 2012-04-27
Yea, I think that's looking like the best plan. Thanks for the help.

---

### Post by javajeff1 on 2012-04-27
I recently could not run Gnome 3 with the install of 12.04 and the newest ATI drivers 12-4.  I put ATI drivers 12-3 back on and Gnome 3 ran fine.  I am not saying this is an issue for you, but drivers can play a part in Gnome 3 working.

---

### Post by RichardCain on 2012-04-27
> **dwaite said:**
> Yea, I think that's looking like the best plan. Thanks for the help.

No problem.  Please click on "Thread Tools" near the top, then "mark as solved".

---

