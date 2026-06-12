---
title: "no GNOME shutdown option"
date: 2007-12-21
forum: Desktop Environments
---

### Post by maxclimber1w on 2007-12-21
Hello everyone. I am running Ubuntu 7.10 which I installed over Kubuntu. When I click on the shutdown button, the dialog only has options to shut down, hibernate, log out, switch user, and lock screen. There is no shut down or restart options.

I saw a fix to this in a thread, but it was for 6.10 and did not work for me. I have been logging out and then shutting down from the KDE login screen, but thats just a hastle. Help!

---

### Post by Nano Geek on 2007-12-21
Do you use KDM or GDM?

---

### Post by maxclimber1w on 2007-12-22
Oops sorry, this is running Gnome desktop not KDE. So GDM.

---

### Post by maxclimber1w on 2007-12-23
Can anyone help? This is a very annoying problem, and it seems like it should be so easy to fix somehow.

---

### Post by niethslim on 2007-12-23
How does your login screen look like, is it the blue Kubuntu login or the brown Ubuntu login?
I'm guessing that you have the Kubuntu one, and if so then as far as I understand you are running KDM.
I don't really know how to fix this, I have the same problem myself.

niethslim

---

### Post by maxclimber1w on 2007-12-23
I do boot into the KDE Login screen, but Gnome is set as my preference. Frustrating, isn't it?

---

### Post by purplenite on 2007-12-23
Try System > Administration > Login Window > Local and check "Show Actions Menu." Apparently turning the actions menu off on the login screen also affects the shutdown menu options.

---

### Post by Animal Mother on 2007-12-24
sudo init 6 to restart
sudo init 0 to shutdown

Could use those from the run window, <alt F2> in a pinch:KS

---

### Post by staticvoid on 2007-12-24
hit f10 in your gdm

---

### Post by staticvoid on 2007-12-24
that sorta rhymed.


cool

---

### Post by shirshasin on 2007-12-24
from a terminal window run the following command
shutdown -h now

---

### Post by maxclimber1w on 2007-12-26
i know of other ways to shut down, but I want this simple, GUI 2-click version to work. Any more ideas?

---

### Post by maxclimber1w on 2008-04-29
bump.

---

