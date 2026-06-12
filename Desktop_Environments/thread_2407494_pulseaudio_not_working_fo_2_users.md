---
title: "pulseaudio not working fo 2 users"
date: 2018-12-05
forum: Desktop Environments
---

### Post by Skaperen on 2018-12-05
i have installed 16.04.5 onto my new laptop and then loaded most of the files from the old laptop (a few into /etc, many into /root, and nearly a couple million into /home).  the original system was installed as 16.04 and regularly upgraded (became 16.04.5) but still had kernel 4.4.0.  the new one got kernel 4.15.0 from the 16.04.5 install/live minne pinne.  i don't know if the kernel version is affecting things. but the user files were from a system with an older kernwl.

sound is not working for 2 users but is working for the others.  the top bar audio icon is faded and the pulseaudio process is absent just for these 2 users.  the files for all user cam from the old system which was running pulseaudio in --system mode.  my intention is to run this one in --system mode, too.  i have it not in --system mode, for now, to make debugging easier by bring in the mode most people use. the same breakage happens in --system mode, too.

where do i need to look to see why pulseaudio might be exiting or crashing?  i have looked all over syslog and friends, but no message suggest anything odd going on.  anyone have any ideas.

i posted in the desktop environments forum because it seems that my DE, Unity, has chosen it and launches it.

---

### Post by Autodave on 2018-12-05
Try going to *Settings -> User & Groups* and then chose one that user that doesn't have sound. Next go to *Advanced *and make sure that they have audio priveleges.

---

### Post by Skaperen on 2018-12-05
there is no *Advanced* option for any user?

---

### Post by Autodave on 2018-12-06
I am on Xubuntu, so your screen could be different from mine.  You need to navigate to your users/groups and search from there.

---

### Post by Skaperen on 2018-12-06
there is very little to do in users/groups or user accounts.  i can set use mode (standard vs. administrator), language, and password, add users, delete users (option to delete user files).  i can also view login history.

all the users were set up the same way, then their backed up files were loaded.  one of the broken users is where i browse/view youtube videos (so you can understand why i want to get sound working there),  i went ahead and created a new one and brought in only select files (my saved videos and saved URLs).  this one works.  this further supports the idea that some file is the culprit.  but i can do what i need to do now.  i will go back to that broken one and try to narrow things down.  i wish the structure of these graphical/desktop files made sense to me, but i am just a systems person.

---

### Post by Skaperen on 2018-12-06
i found the problem.  there was a file named $HOME/.config/pulse/client.conf with just the contents "autospawn = no".  removal of this file and login of that user resulted in the sound working.  this was found for exactly the 2 problem users.

i found this file in the backups for 3 users.  the 3rd user did not get files restored because it is no longer needed for its original purpose.  now i need to see if i can figure out why this file got created, or why autospawning of pulseaudio was turned off.

---

