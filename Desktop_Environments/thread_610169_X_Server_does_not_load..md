---
title: "X Server does not load."
date: 2007-11-11
forum: Desktop Environments
---

### Post by Enigmachine on 2007-11-11
I recently upgraded to Gutsy on my Acer laptop and everything ran beautifully for a few days. The last few times I have started my laptop up, though, it informs me that it can't load X Server - I go to the the log it recommends ["/etc/failsafeXserver: line 47: [: too many arguments"] - then it goes to the login screen in terminal mode. 
I can't recall changing anything in the last time it was loaded properly, errors occur both with stardard and generic.

---

### Post by taurus on 2007-11-11
What happens if you try to start X from a prompt?

```
startx
```
Otherwise, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Enigmachine on 2007-11-12
Prompt didn't work, reconfiguring did. Thanks.

---

### Post by umfaan on 2007-11-17
I had a similar problem - failing to start XServer on boot - actual message "/etc/gdm/failsafeXServer: line 47:[: too many arguments
Warning: Could not retrieve EDID because get-edid is not installed (1)"

Tried using **startx **- this was the key as a got a real error message showing the actual point of error in /etc/X11/xorg.conf. In my case it was a missing Section Name "Extensions".

Hope this helps others who, through my searching for a fix, I know are having similar issues. Cheers...

---

