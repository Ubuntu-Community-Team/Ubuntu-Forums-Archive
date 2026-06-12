---
title: "gnome won't start (suddenly)"
date: 2005-06-02
forum: Desktop Environments
---

### Post by jrincon87 on 2005-06-02
It just started as a Hal error at the time gnome loaded, and it left me only the mouse cursor, and an empty space. I had to reboot and when the Hal loaded fine, then the desktop continued loading. When I went to ask, I found that somebody else had that problem and the people just said that it was almost impossible to solve. I had no time to reinstall Ubuntu until now. But, Gnome kept working fine, the Hal problem seemed to be disappeared, so I made a few updates that the update manager told me they were avalaible. They were, Synaptic, X-chat, libgcc, among other packages. After that I've been unable to sign into Gnome. The following error appears (translation from spanish):
"Your session has been active for less than 10 seconds. If you haven't logout by yourself, this could mean that there's some error in the installation or that you have no free space on the hard disk. Try to log in with some of the fail-safe sessions to see if you can solve this problem".
I click on "Details" and it shows the following:
**(gnome-session:7350): WARNING**: Unable to read ICE authority file: /home/jrincon87/.ICEauthority
From BeOS I checked all this things out, and yes I have more than 1.5GB of free space in the ReiserFS partition and the ICE authority file exists in the right path. I try to log in with a fail-safe session and the same error appears. The only way I can log in is with the recovery mode, but this obviously shows no desktop at all.
Any idea other than reinstall?

---

### Post by bored2k on 2005-06-02
Press alt+ctrl+f1 to go to a bash prompt, login and type:
sudo rm -rf /home/jrincon87/.ICEauthority

Then retry.

- This usually happens when you install applications like K3B.

---

### Post by KLineD on 2005-06-02
That happened to me a couple of times back in the warty times, I checked the permissions on the ICEauthority file and it was owned by root so I changed to be owned by myself and that was it.

EDIT: to change file ownership: 
sudo chown yourusername:yourusername filename

---

### Post by steve101101 on 2007-03-05
this worked for me thanks.

---

