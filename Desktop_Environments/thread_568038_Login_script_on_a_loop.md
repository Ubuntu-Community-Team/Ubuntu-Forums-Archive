---
title: "Login script on a loop"
date: 2007-10-05
forum: Desktop Environments
---

### Post by djwhiplash on 2007-10-05
Hi,

I'm still a bit of a beginner at all this but here goes!

I installed synergy (Keyboard and mouse sharing software) and edited the following files as detailed in the Synergy docs:

gdm/Init/Default
gdm/PostLogin/Default.sample    (I changed this to Default vice Default.sample)

The advice given was to edit the gdm/Sessions/Default too, however this file was not installed.  So I jumped straight in with both feet and edited Xdm/Xsession.

Now after a reboot, the login screen is on a loop.

The synergy program works but I am unable to login to the desktop or any other kind of session.  Does anyone know how to re-edit these files.

Thanks in advance.

C W

---

### Post by kebes on 2007-10-05
If I understand your problem correctly, you cannot login to the GUI session.

However, you should still be able to login to a commandline.

If you press Ctrl+Alt+F1 you should be brought to a text-only commandline. You can login with your username and password. Then go and edit the files back to the way they were before. Use "cd" to navigate to where the file is, and use "nano" to edit the file.

---

### Post by djwhiplash on 2007-10-05
Sorted!

I restarted in recovery mode and change the files to what they should have been.

I had [/usr/bin killall] on one line and [synergyc] on the next line.

I will look harder at the commands next time.

Cheers anyhow.

---

