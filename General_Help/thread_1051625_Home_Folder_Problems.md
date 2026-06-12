---
title: "Home Folder Problems"
date: 2009-01-26
forum: General Help
---

### Post by untappedpilot2 on 2009-01-26
So I moved my Home Folder on one of my computers and can no longer log in. What can I do to salvage my files in my home folder or make it so I can at least log in to get at the files?

-Derek

---

### Post by pytheas22 on 2009-01-26
Please provide a little more information.  How did you move your home folder?  Did you move the entire /home directory somewhere else (where?), or did you just move your particular user's section of /home (in other words, just /home/username)?

One quick solution would be to press control-alt-F2 to get to a terminal, log in, then type:
```

sudo adduser newuser
```

Follow the instructions to create a new user named 'newuser'.  When you're done, press control-alt-F7 and you'll be brought back to the graphical login screen; try logging in there as 'newuser'.

---

### Post by untappedpilot2 on 2009-01-27
I guess I'll try adding a new user from the root prompt in safe mode. I think I moved the /home/user directory or i might have moved the entire /home directory I'm not sure. Either way I moved it to a folder in a folder off / . Basically I got a new computer and I was gonna move my docs and things over to it but I screwed up and moved everything.

---

### Post by pytheas22 on 2009-01-27
You could also just figure out where you put your /home folder and move it back into place.  That would probably work, provided no permissions have been changed on the files (if they are changed, it's not too hard to fix them).

---

### Post by untappedpilot2 on 2009-01-27
i think the add user thing would be the way to go.. if the /home directory no longer exists will it be created upon adding a new user? also im not sure where it's moved to exactly i think its in the /media directory.. I'm going to try it here in a few minutes and post back.. thanks for the help guys

---

