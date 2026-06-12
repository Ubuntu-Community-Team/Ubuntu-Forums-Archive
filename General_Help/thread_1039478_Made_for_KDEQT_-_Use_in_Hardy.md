---
title: "Made for KDE/QT - Use in Hardy?"
date: 2009-01-14
forum: General Help
---

### Post by hawkhock on 2009-01-14
I found a cross stitch pattern creator created for KDE/QT.  Will the package run successfully in Ubuntu 8.04LST? Not sure I understand how the different distros interact.

---

### Post by Titan8990 on 2009-01-14
Kubuntu and Ubuntu are not different distros, even if they claim to be. They are the same distro running a different desktop. Most other major distros come on a DVD and present you with a choice of desktops/window managers.

You can run KDE applications in gnome but will need to download and install some KDE libraries. 

If the program is in Synaptic, then it will handle all the kde libraries for you. Just install the app that you need.

---

### Post by hawkhock on 2009-01-14
Much thanks for the prompt reply. I'll research the package and give it a shot.
Georgi

---

### Post by todak on 2009-01-14
You can install the package from the repositories ```
sudo apt-get install kxstitch
``` That way it will pull in any other files you will need to run the program. However, you must create an entry in the **Applications** menu yourself.

---

### Post by hawkhock on 2009-01-14
I just finished adding the Hardy respositories but had not checked them out.  Much thanks. Noob - learning as I go.  How to I manually add a package to the Applications menu?

Never mind - I think I found it!  I lied -- did find how to add a new application but don't know which file listed in Synaptic manager should be used to open the program. Any help?

---

### Post by todak on 2009-01-14
The command to add to the menu is usually (not always) the same as the package name you installed, in this case, ```
kxstitch
```. Glad i was of help. :)

---

### Post by hawkhock on 2009-01-14
Thanks much.  I was able to open it in terminal but will type in the code to add to the menu as well.  We'll mark this one solved.

---

### Post by hawkhock on 2009-01-14
Guess it is not solved after all.  I opened terminal and typed in "kxstitch".  Received the following messages:

georgi@georgi-desktop:~$ kxstitch
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kxstitch: WARNING: KTempFile: Error trying to create /home/georgi/.kde/tmp-georgi-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
kxstitch: WARNING: KTempFile: Error trying to create /home/georgi/.kde/tmp-georgi-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
kxstitch: WARNING: KTempFile: Error trying to create /home/georgi/.kde/tmp-georgi-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
kxstitch: WARNING: KTempFile: Error trying to create /home/georgi/.kde/tmp-georgi-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
kxstitch: WARNING: KTempFile: Error trying to create /home/georgi/.kde/tmp-georgi-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
kxstitch: WARNING: KTempFile: Error trying to create /home/georgi/.kde/tmp-georgi-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
kdeinit: Aborting. No write access to '/home/georgi/.ICEauthority'.

In another box, message is:
Could not read network connection list.
/home/georgi/.DCOPserver_georgi-desktop_0
Please check that the "DCOP server" is running.

I have a DSL router but no network connection.  Is problem also related to permissions?

---

