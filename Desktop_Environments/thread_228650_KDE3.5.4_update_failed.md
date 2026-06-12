---
title: "KDE3.5.4 update failed"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Pyro MX on 2006-08-03
And now I am no longer able to install or update anything because adept says that anytime I run the updater or adept itself: "Database locked - Another process is using the packaging system database (probably some other Adept application or apt-get aptitude). Please close the other application before using this one"

The problem is, I found no processes matching the ones in the message when checking in the system monitor. Now I have 142 packages waiting to be installed and I cannot do anything ](*,) ! Any solution?

---

### Post by tcollogne on 2006-08-03
Try this

    sudo dpkg --configure -a

Mine also failed. I think it is because the connection to
archive.ubuntu.com fails.

I am going try again later.

Hope this helps

---

### Post by Pyro MX on 2006-08-03
It worked A1! Some stuff got configured and konqueror failed to configure correctly, but adept unlocked and still displayed all the updates. So I got the updates installed and I think it's okay now lol!

I was checking out in the console and noticed that Synaptic gives more detailed on what's going on than adept - like the commands to do in case there's something wrong. I should try synaptic in console when there's an error with adept maybe it will be helpful if I have any other issues.

---

### Post by T700 on 2006-08-03
Thank god for the search function on the forum!  I tried to do the 3.5.4 update and it errored out in the middle of it.  Found myself also staring at the "locked" error.  Tried the simple stuff: restart session, reboot, remove lock file--nothing worked.

Then I did a search and ran ```
sudo dpkg --configure -a
``` and all is joyful again.  Thanks!

Paul

---

