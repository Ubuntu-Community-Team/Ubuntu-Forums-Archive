---
title: "My login time just increased dramatically."
date: 2009-05-25
forum: Desktop Environments
---

### Post by Buttons840 on 2009-05-25
I'm using jaunty.  I don't know if it was something in the latest updates, but that's the best guess I have as to the cause of this problem?

My login time recently increase from a few seconds to about 40 seconds (I timed it, just over 40 seconds).  That is, I enter my username and password at the initial splash screen, then the screen changes resolutions (why isn't the initial splash screen the proper resolution?*) and the top and bottom panels appear, and the mouse.  The mouse shows the busy sign (the spinny circular thing) for about 2 or 3 seconds, then the mouse returns to normal.  Then the screen just sits for about 35 seconds with a black background, the regular mouse, and two blank panels (the default top and bottom panel).  Finally, the background and panels update very quickly, and I"m ready to go, after 40 seconds.

Any ideas what may have changed, this, or what I can do to reduce my login time back to it's usual 4 seconds?  Thanks.

* I did set the /etc/usplash.conf to the proper resolution, but this appears to make no effect on anything.

---

### Post by whoop on 2009-05-25
Look in synaptic history, have you installed any daemons lately?

---

### Post by Buttons840 on 2009-05-25
Most recent installation was k3b CD burning software.

Further back I see a suprano-daemeon but I checked in synaptic, and it is no longer installed.

Anything further back than this is not likely to be the cause.

---

### Post by whoop on 2009-05-25
Ok, remove "quiet splash" from your running kernel line in /boot/grub/menu.lst and reboot.... You won't see the splash screen and can see what it is all doing... You can figure out what is taking so long...

---

### Post by Buttons840 on 2009-05-25
I tried that, but it didn't help.  I think you might not understand.  The excessive wait comes during login, not during boot.

Fallowing your instruction removed the Ubuntu *boot screen*, but that is not where the problem is.  I am happy with the *boot time*, it's faster than it's ever been with Jaunty.

My problem is after the username and password prompt appears, I log in, and then the desktop starts to load, but takes 40 seconds as I said.  I'm used to seeing this in Windows, where the task bar and icon will start appear long before the desktop is fully loaded.  This is a similar problem, the panels show, and the mouse shows, but the desktop is not fully loaded.  There are no icons or interface.  Just the mouse and 2 blank panels.

---

### Post by Buttons840 on 2009-05-25
[http://www.youtube.com/watch?v=Az4dQxhtEKs](http://www.youtube.com/watch?v=Az4dQxhtEKs)

I added a video of the login.  Excessively slow as you will see.

---

### Post by cariboo on 2009-05-25
Could you paste the output of dmesg in your next post. Please use the [noparse]```
 
```[/noparse] tags to make it easier to read.

---

### Post by asmoore82 on 2009-05-25
> **Buttons840 said:**
> That is, I enter my username and password at the initial splash screen, then the screen changes resolutions (why isn't the initial splash screen the proper resolution?*)

This is because the resolution of the Login Screen is set automatically "on-the-fly" at every boot -
simply a must for any users that might ever change to a different monitor - otherwise they could get left in the dark

After you log in, your personal resolution preference is loaded up and set -
another way to look at it besides the possibility of changing monitors is that
at initial boot up, the system has no way to know which user will login,
so it can't preload any particular user's preferences.


For the actual slowness issue, check out "System -> Preferences -> Startup Applications"
make sure everything is kosher in there and you can turn off what you don't need.

---

