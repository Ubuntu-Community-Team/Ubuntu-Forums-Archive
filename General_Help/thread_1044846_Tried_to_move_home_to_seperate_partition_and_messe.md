---
title: "Tried to move /home to seperate partition and messed everything up"
date: 2009-01-19
forum: General Help
---

### Post by HelloIDistance on 2009-01-19
Okay, I tried to search for answers, but nothing I am doing seems to help any. I am a relatively new Ubuntu user and new to Linux. I tried to move my /home folder to a separate partition I made and messed up the process and now get all sorts of errors. (It was fine after I made the partitions, I just messed up in the moving part)

When I boot I get these error messages:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

Then I get this one:

"Could not update ICEauthority file /home/distance/.ICEauthority"

Then:

"There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

Then it boots to desktop and gives me an error about not being able to create the directory /home/distance/.gnome2/share/fonts

Now it's on the desktop with nothing showing. There's no toolbars or anything just the default Ubuntu background.

When I boot into the LiveCD I see the home folder in my main Ubuntu installation (seems to be intact). There's also a home_backup folder with all my stuff in it. On the partition I was trying to move home too there's nothing besides a lost+found and I can't view it.

I know this has been asked before, but whenever I try to follow the steps in other threads they don't work.

Any ideas?

---

### Post by tad1073 on 2009-01-19
from the live cd move you home folder back to the original partition then follow the guide from [psychocat]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by HelloIDistance on 2009-01-19
I tried that. It didn't work. That's the original article I was using to try to move my /home to a separate partition. I must have messed up a word or two. I'm not sure.

I tried the commands under the "What If it Doesn't Work" section and that didn't work either. I forgot what exactly happens. I'll try it again and post what it says.

---

### Post by taurus on 2009-01-19
Looks like your login name is distance.  Boot into recovery mode and run

```
chown -R distance:distance /home/distance
chmod -R 755 /home/distance
chmod 644 /home/distance/.dmrc
shutdown -r now
```
Now, see if you can log in as distance.

---

### Post by HelloIDistance on 2009-01-19
Alright thanks alot guys that worked. Must have not tried it before, haha. One last question though. Now that everything is back to normal...how do I delete the home_backup folder? The option to delete it is greyed out in Ubuntu.

---

### Post by tad1073 on 2009-01-19
```
alt+f2 gksu nautilus
```then navigate to the folder and delete it

---

