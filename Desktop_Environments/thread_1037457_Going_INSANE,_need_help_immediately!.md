---
title: "Going INSANE, need help immediately!"
date: 2009-01-11
forum: Desktop Environments
---

### Post by richardcarter on 2009-01-11
I'm so frustrated!  I love linux, but I'm amazed at how the most basic actions can be highly complex and the tiniest little mistake destroys everything.  I'm in the middle of a project and on a tight deadline and I need to access my KDE GUI on Kubuntu.


I was trying to use NFS to connect my laptop to my desktop.  It worked fine, after a bunch of work.  I restarted my computer just to see if it would still work with the folder I had mounted, and of course, it did not work anymore. UG.

So then I tried installing an automounter from the Ubuntu Community help wiki thing, located HERE:  [https://help.ubuntu.com/community/SettingUpNFSHowTo#Automounter](https://help.ubuntu.com/community/SettingUpNFSHowTo#Automounter) , and now my system is damaged.  When I log in to Kubuntu, 8.10, the following message appears: 

"Could not start kstartupconfig4. Check your installation."

This ALWAYS happens.  Something goes wrong and I lose everything and have to take hours and hours to reconfigure my system and reinstall.  I can't let that happen again this time.  Could someone please help me?


So gratefully appreciative for any assistance anyone is able to offer!

EDIT:  I tried using the failsafe startup option and I get the message: "Xsession: unable to launch failsafe X session --- x-terminal-emulator not found; aborting."

---

### Post by albinootje on 2009-01-11
> **richardcarter said:**
>  When I log in to Kubuntu, 8.10, the following message appears: 

"Could not start kstartupconfig4. Check your installation."


Did you use your /home in the NFS server settings ?
Then boot into "recovery mode".
Choose "drop to root shell prompt", and undo your changes.
If you're not so familiar with the command line, and you want a quick fix, try this :
```

apt-get remove autofs
nano /etc/fstab

```
And put a # sign in front of the line with NFS, if any.

ctl-x to exit and save the file.

After that, type :
```

reboot

```

---

### Post by richardcarter on 2009-01-12
Worked perfectly!  Thank you so so so so so much!

Now I just have to figure out how to network folders between my computers without destroying them.


Thanks again!

---

