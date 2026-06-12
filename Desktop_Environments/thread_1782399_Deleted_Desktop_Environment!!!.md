---
title: "Deleted Desktop Environment!!!"
date: 2011-06-14
forum: Desktop Environments
---

### Post by subchief on 2011-06-14
guys, am new to ubuntu so unfortunately i installed my desktop environment from synaptic manager! so when i restarted my computer i couldn't log into the desktop environment.
How can i recover from this?
Also,how can i access my home folder from a live cd?:(

---

### Post by Copper Bezel on 2011-06-14
If you have a wired connection, I think you should be able to connect to the network without logging into the desktop. You can hit Ctrl+Alt+F1 to jump to a console, log in, and run sudo apt-get install ubuntu-desktop, which should restore any packages you removed that are necessary for the Gnome environment.

If you boot from a LiveCD, you should be able to open the file manager, select the hard drive, and navigate to /home/[your username].

---

### Post by subchief on 2011-06-14
Thanks for that...i will try that but am working from the live cd and using a modem to access the net so i will let you know how that goes when i do it
As for accessing my home folder...i get an error message saying i do not have the permission to access the folder.Is there a way to decrypt the folder so its accessible?

---

### Post by Copper Bezel on 2011-06-14
Can you use a root nautilus session, by running gksu nautilus ? (Be careful with this, of course - you could access the files, but you wouldn't want to edit anything this way.)

---

### Post by subchief on 2011-06-14
I tried that and i got a text file in that flder with this content.

"THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private"

however when i run the command it says the private folder is not mounted properly.

any other tip?

---

