---
title: "Writing terminal command to be executed at start up"
date: 2010-03-09
forum: Desktop Environments
---

### Post by Nozzel on 2010-03-09
Hello guys,

I have Ubuntu 9.10 and have a question for you.
Due to my Internet Service Provider complications, I need to change my Mac Address, I installed Macchanger program, so no problem there. But each time I turn off and turn on my computer, I need to repeat this steps, over and over again.

Opening up terminal (added it to Start up applications)
su
password
macchanger -r eth0 -m 00:*:*:*:*:*

Can I somehow write a script, for this to execute each time automatically, while Ubuntu loads? And what script it would be?

Any help would be greatly appreciated.

All the best,
Nozzel

---

### Post by Barriehie on 2010-03-10
You've got at least 2 choices for doing this:

1) You can make a crontab entry with the &reboot entry
2) Actually have a script in /etc/init.d  Only issue here might be if your OS checks for the script to be LSBINIT compliant.

Have to be root to save, make executable, and create symlinks.

In the terminal:  (Applications > Accessories > Terminal)
**gksu gedit /etc/init.d/changemymac**  # You'll prompted for password

Now copy/paste the below into gedit and save the file.  Save = Ctrl S / Close = Ctrl W / Quit = Ctrl Q
```

#!/bin/bash
macchanger -r eth0 -m 00:*:*:*:*:*
exit 0
```Save that in **/etc/init.d** as **changemymac **; should've already been done via gedit.  Make it executable via the terminal with **chmod +x /etc/init.d/changemymac**

Now you have to create the links the system needs:
```

sudo update-rc.d changemymac defaults
```That should do it.  To disable it see the manpage for **update-rc.d**,  you can't just delete the file!

Have to reboot for it work!

HTH

---

