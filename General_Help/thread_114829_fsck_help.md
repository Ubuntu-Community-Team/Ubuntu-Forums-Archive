---
title: "fsck help"
date: 2006-01-09
forum: General Help
---

### Post by MrLobster on 2006-01-09
Each time I boot up it says there is a probem with my disc that I need to fix manually. Something like I have large files but lack a LARGE_FILE flag use fsck to fix or Ctrl-D to continue.

If I hit Ctrl-D my OS boots up fine but every time I boot up now it goes through a long (5-10 min) disc scan and gives me that same error. Anyone know how to fix it?

---

### Post by dcstar on 2006-01-09
[QUOTE=MrLobster]Each time I boot up it says there is a probem with my disc that I need to fix manually. Something like I have large files but lack a LARGE_FILE flag use fsck to fix or Ctrl-D to continue.

If I hit Ctrl-D my OS boots up fine but every time I boot up now it goes through a long (5-10 min) disc scan and gives me that same error. Anyone know how to fix it?[/QUOTE]
Either edit /etc/default/rcS to say:

FSCKFIX=yes

So fsck will run itself with the "Fix" flag set and automatically fix any problems it encounters.

Or, enter your root password at the "Ctrl-D" question and type:

fsck -y

to do the same thing manually.

---

### Post by MrLobster on 2006-01-09
Thank you.  I edited the files as you wrote and it fixed it.

---

### Post by iraklirost on 2006-01-14
I had same problem so wrote command: fsck -y 

but now my OS has other problmes:

Failed to start X server (your grafical Interface)
fatal server error(cannot open log file /var/log/Xorg.0.log )

---

### Post by dcstar on 2006-01-14
[QUOTE=iraklirost]I had same problem so wrote command: fsck -y

but now my OS has other problmes:

Failed to start X server (your grafical Interface)
fatal server error(cannot open log file /var/log/Xorg.0.log )[/QUOTE]

Try: sudo dpkg-reconfigure xserver-xorg to recreate your X configuration.

---

