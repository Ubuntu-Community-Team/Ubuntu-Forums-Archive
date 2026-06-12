---
title: "Problem logging in after hard crash."
date: 2012-03-12
forum: Desktop Environments
---

### Post by tac-shell on 2012-03-12
I'm setting up an old PC to run Zoneminder. I decided to use Xubuntu 11.10 and got everything installed successfully.

When I was setting up Zoneminder I was having trouble getting my capture card to work so I downloaded xawtv to troubleshoot. I executed the program my system locked up completely. I couldn't kill the xserver or send the term signal with ctl-alt-delete. So... I hit the power button and restarted. 

I got back to the xdm login screen with no problems but when I input my password the screen went black for a second before returning me to xdm. I can work in the other terminals just fine (ctl-alt-F1) but I need this machine to act as a video monitor so I have to have a working desktop environment.

(B.T.W. checked the kernel log and the initial crash was due to a PCI parity error from my capture card, reseated it and it's working like a charm!)

---

### Post by Toz on 2012-03-12
Hello and welcome to the forums.

Have a look at the ownership of the files in your home directory to ensure you are the owner. Specifically, the files .Xauthority and .ICEauthority are known to exhibit this problem if they are not owned by you. Simply change the ownership.

Otherwise, the file ~/.xsession-errors may yield some clues.

---

### Post by tac-shell on 2012-03-12
I checked out .xsession-errors and there was a line indicating an I/O error with .ICEauthority. I figured that it must have been corrupted when I did the hard restart, so I moved it out of the home directory and attempted to login through xdm, and it worked! 

Thanks for your help. That was such an easy fix, I just had to know where to look.

---

