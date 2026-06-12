---
title: "planeshift errors"
date: 2005-07-15
forum: Gaming &amp; Leisure
---

### Post by twowheeler on 2005-07-15
I have installed planeshift but it dies almost immediately on execution.  Has anyone else seen this?  Here is the terminal output:

```
dan@ubuntu:~/planeshift$ ./psclient
planeshift.application.client:
  PlaneShift Crystal Blue
  This game uses Crystal Space Engine created by Jorrit and others
  0.99 r0 [Unix-x86-GCC]
LOG_ANY flag deactivated.
LOG_WEATHER flag deactivated.
LOG_SPAWN flag deactivated.
LOG_CELPERSIST flag deactivated.
LOG_PAWS flag deactivated.
LOG_GROUP flag deactivated.
LOG_CHEAT flag deactivated.
LOG_LINMOVE flag deactivated.
LOG_SPELLS flag deactivated.
LOG_NEWCHAR flag deactivated.
LOG_SUPERCLIENT flag deactivated.
LOG_EXCHANGES flag deactivated.
LOG_ADMIN flag deactivated.
LOG_STARTUP flag deactivated.
LOG_CHARACTER flag deactivated.
LOG_CONNECTIONS flag deactivated.
LOG_CHAT flag deactivated.
LOG_NET flag deactivated.
LOG_LOAD flag deactivated.
LOG_NPC flag deactivated.
LOG_TRADE flag deactivated.
LOG_SOUND flag deactivated.
LOG_COMBAT flag deactivated.
LOG_SKILLXP flag deactivated.
LOG_QUESTS flag deactivated.
LOG_SCRIPT flag deactivated.
Skipping 'radiooff' because it's already loaded
Skipping 'radioon' because it's already loaded
  psEngine initialized.
Creating psnetconnection 85a1ce8!

```

The opening screen comes up, and the drumroll sound starts but after a second or two it closes and exits.  It does not seem to be a permissions problem because it still dies if I run it as root.  Suggestions, please?

---

### Post by stevenyu on 2005-07-15
I can't even get planeshift install properly, I run the installer, but can't see where the file is, look like it delete the files as soon as it finish extracting it.

---

### Post by GazaM on 2005-07-16
I have this exact problem. If I keep trying it stays open eventually, but it is very annoying. Don't worry though, the game isn't that good at the moment, you should probably wait a few releases until it's near final.

---

### Post by flugh on 2005-07-27
You need to install 'dialog' (do 'sudo apt-get install dialog'). Once you get dialog installed, the installer will run fine.

Then planeshift will crash for some other reason  ](*,)

If you check ./psclient.txt, you will see a lot of useless-to-me information. At the end is a message about no video driver present. So, I'm off to Google a bit on the planeshift site to see about specifying the video driver (I'm using nvidia myself).

---

### Post by twowheeler on 2005-07-28
I don't think psclient.txt will tell you anything.  It does not appear to be a log of the game session -- it appears to be some sort of log from when the binaries were compiled.  Note that the time stamp of many of the files in the planeshift directory is May 20 or May 22, even though I installed the thing on July 15.  So they were copied in by the installer.

---

### Post by flugh on 2006-11-20
Just for the sake of following up over a year later, I remember starting the planeshift program and it dying mysteriously. So I ran it using strace, sifted through the bagillion lines of output (grep ENOENT or file not found from the output), and found that the binary had a hardcoded /home/username in it (I don't recall the exact username, but I just happened to bump into him in #ubuntu one night, he was the one who built the package). As a quick and dirty fix, I just did a 'sudo ln -s /home/myuser /home/otheruser' and planeshift ran fine. I'm guessing it's been fixed since then, but it can't hurt right? If nothing else, an example of troubleshooting these kind of things :-)

---

### Post by K.Mandla on 2006-11-20
Nice work. I wouldn't have thought of that.

I'm going to shift this to the Gaming area, where it will be a good reference for the future.

---

