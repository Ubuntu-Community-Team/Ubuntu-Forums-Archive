---
title: "Installing RealPlayer (or not)"
date: 2009-01-02
forum: General Help
---

### Post by DogWalker on 2009-01-02
I recently downloaded RealPlayerGOLD11.bin to my laptop (running Kubuntu Feisty) and had no problems except that I neglected to install it to a sensible folder.

Now I have my brand new copy of Ubuntu Intrepid Ibex on my desktop I thought I'd do the same, but install it to /usr/bin - and all seemed to go well, together with an icon in the Applications menu.

However, when I try to use the icon I get a message "Could not launch menu item Failed to execute child process "reaplay" (Too many levels of symbolic links).

Okay, I did what I do on my laptop and went to the folder I installed to and clicked the realplay.bin file which just starts it.  Only it doesn't on my desktop.  I get a message "Could not display "/user/bin/realplay.bin" There is no application installed for this file type."

Obviously I have done something silly...
First I made the download executable with chmod u+x
Then I executed it with sudo ./RealPlayer11GOLD.bin and when prompted for the install path gave /usr/bin where it now resides. I got the expected confirmatory messages.  I checked that the files and directories on my laptop install also appear on my desktop one.

Can anyone help me please?  It seems to me that I replicated what worked on my laptop but without success...

DW

---

### Post by albinootje on 2009-01-02
> **DogWalker said:**
> 
First I made the download executable with chmod u+x
Then I executed it with sudo ./RealPlayer11GOLD.bin and when prompted for the install path gave /usr/bin where it now resides. I got the expected confirmatory messages.  I checked that the files and directories on my laptop install also appear on my desktop one.

I suggest to remove /usr/bin/realplay, and reinstall in /opt/ instead of /usr/bin/

Try to carefully remove more of your old RealPlayer installation in /usr/bin/

It's possible that RealPlayer wants /usr/bin/realplay as a symbolic link, and that gave some conflict.

---

### Post by DogWalker on 2009-01-02
Excellent - I did that and after adding it manually to the menu, it works great.  Thank you.

---

