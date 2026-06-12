---
title: "Login screen resolution problems"
date: 2006-12-28
forum: Desktop Environments
---

### Post by MisterCow on 2006-12-28
Well, I'm having an issue with the login screen. I've never used Ubuntu before, so I thought I'd give it a shot.

My monitor appears to be detected properly, and it's been given the largest resolution it can handle as the default res - the problem is that 1280x1024, even though it's a supported res, looks horrible on the monitor.

I found the option for changing the screen resolution on the System > Preferences, but it only changes it for my user, rather than the entire system - Even with the checkbox for the computer checked.

So I searched the forum and found that the only way most people could find is to directly edit the xorg.conf, so I edited out 1280x1024 and it fixed the res on the login screen... sort of.

My main problem is that the screen is now 1024x768 like I wanted, except it's still showing the login screen at 1280x1024 and has scrolling edges to see the rest of the screen that's missing... Is there a way to fix this?

---

### Post by gatinho on 2007-01-19
> **MisterCow said:**
> ...

My main problem is that the screen is now 1024x768 like I wanted, except it's still showing the login screen at 1280x1024 and has scrolling edges to see the rest of the screen that's missing... Is there a way to fix this?

Any solution to this?  I have the same problem with my monitor. ](*,)

---

### Post by NESFreak on 2007-01-19
the settings windows your referring to is only for you as users.

pres alt-F2 and enter```
gksudo gedit /etc/X11/xorg.conf
```search for ```
Section "Screen"
``` and go to```
SubSection     "Display"
        Depth       <your default dept, probably 24>
        Modes      <remove the resolutions you think that are to high>
```

next time you boot up the login screen works correct.

NESFreak

---

### Post by Error1312 on 2007-01-19
I'm not sure if I'm talking about the exact same problem, but I could get my login resolution the same like rest of my system by moving the used resolution to the front of the 'Modes' line in xorg.conf . It should then be seen as the default resolution by ubuntu.

---

### Post by cahumphrey on 2007-02-23
NESFreak, 

Your method worked perfectly for me! I was having the same problem, my monitor was displaying a FAR TOO SMALL HIGH of resolution, and therefore defaulting to a refresh rate of 60Hz! 

Now I have the login screen running at a reasonable 1600x1200@85Hz - Just like my user's configuration :)

Next time I may try the Error1312 method though, so I can keep certain resolutions availble 'just in case'.

Thanks again guys!

---

