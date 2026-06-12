---
title: "root login, modem dectection, sound system."
date: 2006-09-05
forum: Desktop Environments
---

### Post by ashif on 2006-09-05
my System is:

Compaq DeskPro ENS P866


I am new to Linux / KUbuntu. i am facing a couple of problems.

1) firstly, i cant login as root (it says that root login disabled)
how to enable the root login ?

2)I want to run internet on kubuntu, i've installed the modem in the extension slot, kubuntu might have picked the modem(as it shows the model and manufacturer - Us Robetics), but in the kinfo it displayes the modem model and manufacturer and there in description it says : that its "only available to root" (like that...).

i cant setup any internet account in kppp, when i configure kppp, in modem tab, ther is no item, and it does not query modem as it is not installed.

3)i hear no sounds,no vedio i tried to play a VCD, mp3 file but it didnt played, the player crashed.
how to check if sound drivers are installed ?

---

### Post by tatimmer on 2006-09-05
How to set/change/enable root user password

    * Read #General Notes 

sudo passwd root


2) I suggest an external hardware modem.  See "tomsmodemtips".  See also "man pppconfig" for setting up dialup connection.

mp3 files are not supported out of the box since they are proprietary but I believe there is a library package that can be downloaded.

---

### Post by ashif on 2006-09-06
thanks,
but what if i want to use an internal modem?

and how to check if sound driver is installed and working, and playing sample sounds? (any built in sample sound and vedio?

---

