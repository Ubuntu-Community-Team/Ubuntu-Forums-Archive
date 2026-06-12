---
title: "Gutsy - no Compiz ARGB settings"
date: 2008-02-20
forum: Desktop Effects &amp; Customization
---

### Post by tshags on 2008-02-20
I have Compiz 0.6 running on Gutsy and need to add something to "Disable ARGB visuals". However, I have no ARGB settings under Window Rules in the settings manager. 

I haven't been able to find any answer to this. I also looked into how to upgrade to the bleeding edge version of Compiz but couldn't find anything on that either. Any help would be appreciated.

---

### Post by bwang on 2008-02-21
I'm having the same problem-I have to disable ARGB Visuals for lxdoom; otherwise the whole window is transparent.

---

### Post by crewe on 2008-02-21
I believe this is in your xorg.conf
```

sudo gedit /etc/X11/xorg.conf

```

and comment out the line Option "AddARGBVisuals" "True" by haveing it read
> 
#    Option    "AddARGBVisuals" "True"


then restart X (log out and then CTRL+ALT+BACKSPACE and log in again.)

---

