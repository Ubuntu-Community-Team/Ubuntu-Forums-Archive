---
title: "Copying X-Server settings to another user?"
date: 2008-12-31
forum: General Help
---

### Post by DeaconBlues on 2008-12-31
Hi, I'm using kubuntu 8.10, installed via wubi. I've created two accounts on this machine.

The one under my name has become corrupt with regard to x-server. I no longer have sound and whenever I try to log in graphically it gives me "x-terminal-emulator not found; aborting" and crashes into the console.

I can then login and if I then type "startx" at this point, KDE starts up without any audio.

I think I've corrupt xservers' configuration by installing the wrong nvidia drivers, which worked for a while before a recent kernel update. I managed to remove the old nvidia drivers and installed appropriate ones, this time using EnvyNG.

Now if I log in using the second user account everything is fine: I have sound and the new nvidia driver loads fine. It is just when logging into my account, which is the one I used for much messing around with video drivers and editing xorg.conf my sound is screwed and it gives me the error I mentioned above and drops me into the console.

Would it be possible to copy over the x-server config files from the working user account into mine? Which directory would I find them in etc, etc?

I know that I could probably just delete my account and create a new one, as both accounts on the machine have root access, but I would rather learn something by my mistakes. Thanks for reading.

---

### Post by dcstar on 2008-12-31
> **DeaconBlues said:**
> 
........
Would it be possible to copy over the x-server config files from the working user account into mine? Which directory would I find them in etc, etc?

I know that I could probably just delete my account and create a new one, as both accounts on the machine have root access, but I would rather learn something by my mistakes. Thanks for reading.

All the configuration should be in hidden "." files and directories in the user home folder, you can try copying them one-by-one until you problem is fixed.

Be sure the permissions are correct for the destination!

---

### Post by abn91c on 2009-01-01
Delete your .kde4 folder in your profile,when you log in again kubuntu will rebuild it to default settings

---

