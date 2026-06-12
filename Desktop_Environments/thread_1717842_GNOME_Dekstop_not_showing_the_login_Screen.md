---
title: "GNOME Dekstop not showing the login Screen"
date: 2011-03-30
forum: Desktop Environments
---

### Post by romy.mathew on 2011-03-30
I tried to open the Open the Laptop I found the I could not find my Login Screen, I can watch my mouse scrolling around and when hit power key show me restart, herbinernate .etc, 

I tried to log in into console by pressing ALT+CNL+F4, and when typed startx it showed me following error
 
[COLOR="red"]"
Fatal Server error:
Server is already active for display 0
           If this server is no running remove /tmp/.X0-lock
           and start again

Xinit: Resource temporarly unavailable (errno 11): unable to connect to X server

Xinit : No such process (Errno 3): server error

"[/COLOR]

Please Help.....

---

### Post by ajgreeny on 2011-03-30
Have you ever seen the gnome desktop on the machine, or is this a problem after installing?  What hardware have you got running ubuntu, particularly the graphic card?

There is an xsession already running, hence the error message
```
Server is already active for display 0
```so from the Ctrl+F4 console try stopping gdm with ```
sudo service gdm stop
```then try ```
startx
``` again and report back any new error messages.

---

### Post by romy.mathew on 2011-03-30
> **ajgreeny said:**
> Have you ever seen the gnome desktop on the machine, or is this a problem after installing?  What hardware have you got running ubuntu, particularly the graphic card?

There is an xsession already running, hence the error message
```
Server is already active for display 0
```so from the Ctrl+F4 console try stopping gdm with ```
sudo service gdm stop
```then try ```
startx
``` again and report back any new error messages.
Thanks ajgreeny for the quick response, I have using the gnome dekstop without any problem, all i have done is installed a GD [Graphics Library for perl module], when i opened in morning this issue happened 

I am using below hardware for the graphics card

[COLOR="Red"]01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M][/COLOR]

When I type the command above It takes me inside the dekstop, but when i restart it I need to do the same operation again to get inside the dekstop....:(

---

