---
title: "Lotus Notes 8.5"
date: 2009-01-07
forum: General Help
---

### Post by wohenben on 2009-01-07
Managed to get the beta running on Hardy (both Domino 8.5 and Notes 8.5 client).

Main puzzle so far is that some dialogs don't seem to take any notice of font settings, so that some text overlaps the end of buttons or simply gets cut short.

Anyone else out there running this?

---

### Post by BeamingFuture on 2009-01-29
I'm running Lotus notes 8.5 on Ubuntu 8.10 64-bit. I have some smaller issues, but not the one mentioned. Have you installed "ttf-xfree86-nonfree"? this will make Lotus Notes look even better than on Windows, and it will problably help you with this issue.

/Anders

---

### Post by daanemanz on 2009-01-30
The problem is... I can't get it done. I have a fresh intrepid 64 bit install, installed ubuntu-restricted-extras after that for Java and used getlibs for the missing libraries.

So far, I have only seen the splash screen and a prompt to fill in my password.

Before I had it installed and it kinda worked, but as soon as I clicked the 'Mail' icon, one of the cores of my dualcore went 100% and Lotus Notes was unresponsive.

Anyone have some tricks for this?

---

### Post by Narkolas on 2009-03-02
I keep getting this message when i try to start the server:

/opt/ibm/lotus/bin/server

Please edit your shell's DISPLAY environment variable to reflect an unlocked terminal that you would like to launch the Domino Setup Program on.



Im running 8.04.02 console only.

Any ideas?


Solution: For some reason i had to add -listen <port> to that command.

/opt/ibm/lotus/bin/server -listen 8585

---

