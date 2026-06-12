---
title: "disable Seperate x screen"
date: 2012-08-24
forum: Desktop Environments
---

### Post by neuman1812 on 2012-08-24
Running 12.04 64 bit.

I was playing around with adding a second screen and I tried the "seperate x server" option.   All the gave me was a duplicat of my current screen on the same one.  As you can see from the image, I get "screens" on the same.

 Now I cannont turn it off.

The "Disable" option for in configuration is greyed out.

<snip>

---

### Post by papibe on 2012-08-24
Hi neuman1812.

Open the 'Nvidia X Server Settings' as super user:
```
gksudo nvidia-settings
```
Then set the screens as you want. After that press 'Save X configuration file'

Finally, restart your machine.

Regards.

---

### Post by neuman1812 on 2012-08-24
> **papibe said:**
> Hi neuman1812.

Open the 'Nvidia X Server Settings' as super user:
```
gksudo nvidia-settings
```
Then set the screens as you want. After that press 'Save X configuration file'

Finally, restart your machine.

Regards.


did not work.   Options are still greyed out.

---

### Post by wyliecoyoteuk on 2012-08-24
There are 3 options for each screen, seperate Xserver, Twinview, and disabled.
The disabled option only disables the selected screen.
You need to enable the second display by selecting it in the "Model" drop down list. 
Then set the display option to "twinview", save and reboot, then you should be able to enable the second screen.

If the monitor selected is your main display, you cannot disable it.

---

### Post by neuman1812 on 2012-08-24
What Im trying to do I get the second "nautilus" from appearing on my main screen.. at this point I dont eve want a second screen.  


as you can see from my image.. For ever window that this opened..there is an Identical window opened again...On the same screen.

---

### Post by neuman1812 on 2012-08-24
> **wyliecoyoteuk said:**
> There are 3 options for each screen, seperate Xserver, Twinview, and disabled.
The disabled option only disables the selected screen.
You need to enable the second display by selecting it in the "Model" drop down list. 
Then set the display option to "twinview", save and reboot, then you should be able to enable the second screen.

If the monitor selected is your main display, you cannot disable it.


just tried to follow this and now I have 3 "nautilus" sessions running.


Im sooooo confused.

---

### Post by wyliecoyoteuk on 2012-08-25
So how many physical displays do you actually have?
Sounds like you have set up 2 screens on one display somehow.

Post the contents of your /etc/X11/xorg.conf file here, and we can probably advise you on what to change.

---

### Post by neuman1812 on 2012-08-25
> **wyliecoyoteuk said:**
> So how many physical displays do you actually have?
Sounds like you have set up 2 screens on one display somehow.

Post the contents of your /etc/X11/xorg.conf file here, and we can probably advise you on what to change.

here's and Updated picture.
[http://imgur.com/bIMCU](http://imgur.com/bIMCU)

I dont have an xorg.conf  but I do have an xorg.conf.bak

I have determined that it is profile specific.  Another user profile does not have this issue.

---

### Post by neuman1812 on 2012-08-25
I found a way around it.   Not a fix. but a solution.

I created another profile, and Just moved my documents over.

---

