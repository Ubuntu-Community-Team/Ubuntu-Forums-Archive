---
title: "Messed with Permissions, now I can't log in!"
date: 2009-03-19
forum: General Help
---

### Post by Datsun240Z on 2009-03-19
Hi guys, I really screwed up and could really use your help

Heres was happened:

Ubuntu wasn't letting me create/edit files on a couple of my external usb drives because it said I wasn't the owner. So I opened up the terminal, inputted "sudo nautilus" so i could go into dev/external (where i mounted my drive) as root with full permissions. As root, I could finally create and edit the files I needed on my external drives.

Well, I thought it was a good idea to give my own user account the same permissions as root so I wouldnt have to go into the terminal every time I wanted to alter files on my external drives. So as root, I right clicked on Home, went to Permissions, and gave my user account the ability to create/edit files. 

I'm new to linux, and apparently this was a no-no, because after that happened things started getting weird, and now I can't log in.

At the log-in screen, I type my username and pass, it says 

"Users $HOME/.dmrd file is being ignored. This prevents the default session and language from being saved.
File should be owned by user and have 644 permissions.
Users $HOME directory must be owned by user and not writable by others."

after i press OK, it goes to another prompt that says

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

and then it takes me back to the log-in screen

I have no idea how to fix this besides re-installing ubuntu and possibly losing my data. help!

---

### Post by adult swim on 2009-03-20
reboot and select recovery mode from the grub menu.  you may have to press escape to show the grub menu if it is set to hidden.  when you have booted to recovery mode, select root terminal.  once you are there enter in these commands
```
chown username:username /home/username/.dmrc

chmod 644 /home/username/.dmrc

shutdown -r now
``` in the first step youll want to change username:username to your username.  so if it is Datsun, it would be ```
chown Datsun:Datsun /home/username/.dmrc
```

---

### Post by Datsun240Z on 2009-03-20
it didnt work, it said something like "cannot find /root/~.dmrc". 

but i just realized i needed the 64-bit version of ubuntu for my system so i had to re-install anyway. works fine now, and i was able to back up my files before re-installation using the live cd. but i really appreciate your help, you're awsome

---

### Post by fieroboom on 2009-03-20
> **Datsun240Z said:**
> it didnt work, it said something like "cannot find /root/~.dmrc". 

but i just realized i needed the 64-bit version of ubuntu for my system so i had to re-install anyway. works fine now, and i was able to back up my files before re-installation using the live cd. but i really appreciate your help, you're awsome

That's adult swim's post is a typo. ~/ is shorthand for /home/USER where user is your username. When you log into recovery mode, you are true root, therefore, your $HOME is /root.
Here is the correct way to do it:
```
chown username:username /home/YOUR_USERNAME/.dmrc

chmod 644 /home/YOUR_USERNAME/.dmrc

shutdown -r now
```

Anytime you are fixing an issue, it's always better to use an absolute path. It helps prevent issues. For instance, had there been an actual .dmrc file in /root, then Datsun240Z would have just created more issues for himself. Please be careful giving advice; especially in root form.
:D
-Paul

---

