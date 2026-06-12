---
title: "Tightvnc question"
date: 2009-04-16
forum: General Help
---

### Post by runnner on 2009-04-16
I will remote access ubuntu from a windows pc, I try to use tightvnc, now there are some questions.


1. Should both the windows PC and linux server install tightvnc?

2. How do I know if the remote Linux has installed tightvnc and whether it accepts tightvnce connection from Windows pc?

3,I downloaded tightvnc-1.3.10_unixsrc.tar.gz from [http://www.tightvnc.com/](http://www.tightvnc.com/), but I don't know how to install it.

Thanks for help!

---

### Post by jrdonnaruma on 2009-04-16
Well, I'm not an expert, but I might be able to help a little.

1. You only need to install the tightVNC viewer on the Windows PC, because the linux server (If you are running ubuntu, though I do think most distros come with some form of VNC), should already have it installed.

Here is how to setup the server within GUI (Assuming you are using a GUI.. Explanation at bottom):

System->Preferences->Remote Desktop

Click the boxes next to "Allow other users to view your desktop", "Allow other users to control you desktop", and "Require the user to enter this password:" Make sure you enter a password in the box, and uncheck anything else that is checked.

2. You can set this in the preferences for remote desktop, the last section is 'notification area' the second option is 'only display an icon when there is someone connected'

3. The windows Installation is available in an executable package (.exe) since you only need to install it on the windows computer, that should be all you need. 

(Explanation) If you are going to be trying to connect to a linux server that doesn't have a GUI, use SSH instead of VNC. Secure SHell is like Remote Desktop, except it connects to the shell, instead of a graphical interface. VNC, to my Knowledge, is for Graphical Interfaces only, so it wouldnt work if you are trying to connect to a GUI-less server.

---

