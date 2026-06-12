---
title: "Can't Log In"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Rumpty on 2006-09-01
Eeeeaaaaaaaaagh! I can't log in!!

I've just done a clean install of kubuntu 6.06.1, AMD64 alternate disc, and the whole process went pretty well, meaning that it worked. Some small annoyance at not being able to change the monitor resolution - the fonts are SO small on my 17" monitor at the default res. Why the default is 1280 by 1024 beats me.

But now, after telling the computer to restart, I can't log in. The log-in screen comes up, accepts my user name and password, I press enter, (or select an option from the menu, and I've tried them all) the machine dithers around for a couple of seconds, and then brings up the log-in screen again! And so on. Talk about maddening.

I've done a number of linux installs over the years, so I'm not absolutely raw at the process, but you never know how it's going to go really. My wife sits at the other computer in the room, using Windows, smiles, and wonders why I persevere with this unfriendly techie oriented OS. So do I sometimes, like now.

Does anyone know how to get out of this log in problem please?

---

### Post by ayoli on 2006-09-01
about the default resolution, try reconfigure X with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
for login prob, i dont know much about kde, maybe a previous setting you done is bad, then you can try to remove your ~/.kde dir.
hope that can help you.
regards.

---

### Post by Rumpty on 2006-09-02
Thanks Ayoli. I've taken the easy way out, and reinstalled.

---

