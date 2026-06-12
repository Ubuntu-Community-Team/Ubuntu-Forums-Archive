---
title: "Broke X trying to install XGL"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Enigmatic on 2006-08-18
I'm not sure exactly how I managed to do it. I had originally started installing XGL per a tutorial, which I then realized was written for ATI. I cancelled the installation of a few packages. Then I tried the Nvidia installation. Installed a few packages and restarted X when prompted, but X never came up. I get this error however:

xinit: Connection refused (errno 111) unable to connect to X server
xinit: no such process (errno 3):server error

I went back and uninstalled the Nvidia packages from the commandline, and uninstalled most of the ATI packages, as far as I could tell.

Should I be removing the following? compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

I'm not sure if I should touch xserver-xorg...

If anyone has any ideas I'd really appreciate it, right now I'm not sure of what to do and have no access to my PC.

---

### Post by Enigmatic on 2006-08-19
I should also add that at the same time as I installed the packages it overwrote my xorg.conf but also made a backup file. I restored the backup but there is no change.

---

### Post by Enigmatic on 2006-08-19
Looks like I got X back by reinstalling xserver-xorg and the Nvidia drivers. However, I have a number of things that don't seem right.

1 - Fonts aren't quite as smooth as they used to be. I think I had installed a Cairo font system earlier and may have to reinstall it.

2 - Biggest problem - accessing anything in the system menu (that runs as root) does not work. Gives me this error: Unable to copy user's Xauthorization file. Earlier it had told me it couldn't find gksu, but I installed that but am left with this message.

3 - Skips the login screen. Also, I had custom settings in xorg.conf for my mouse forward/backward buttons. X wouldn't boot until I commented those out and replaced them with the default mouse. I guess I'll just have to redo that?

---

