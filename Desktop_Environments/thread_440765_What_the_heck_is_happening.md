---
title: "What the heck is happening"
date: 2007-05-11
forum: Desktop Environments
---

### Post by myoungf1 on 2007-05-11
Alright here it is
I just recently got Ubuntu up on my brothers computer and it has been working great for about a week now.  All of a sudden he is downloading games from the synaptic package manager and all of a sudden gets the following error:  GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could  not be opened for writing.  In any case, it is not possible to login.  Please contact your system admin.

I also have suddenly had problems in kde with the desktop wallpaper slideshow.  it was working a day ago and now it will not work at all.  I have checked the settings and they are set correctly but I still can not get the wallpaper slide show to work.  

Any help would be much appreciated

---

### Post by taurus on 2007-05-11
Could be downloading too much stuff and running out of disk space.  What's the output of this command from a terminal?

```
df -h
```

---

### Post by myoungf1 on 2007-05-11
Thanks for the quick reply looks like the last install was not what we wanted and we are reinstalling again.  Only showed 2.5gb for sdb1 so will be more careful this time.

---

### Post by taurus on 2007-05-11
2.5GB for / will not leave you a lot of room for anything else.  Try to make / much larger if you plan to install a bunch of additional stuff.

---

### Post by myoungf1 on 2007-05-11
I agree but i have to admit was using the alternate install cd and didn't pay enough attention to the install of the system.

---

