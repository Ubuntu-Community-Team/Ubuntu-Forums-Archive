---
title: "Need a program like PC anywhere"
date: 2008-09-16
forum: Desktop Environments
---

### Post by wewhitt on 2008-09-16
Hello all,
    I need a recommendation on a program like PC anywhere so that I can access another computer and control every aspect of it. They both have Hardy Haron(Heron not sure) loaded on them (8.04) ubuntu. I'm playing with these at work - I'm digging the OS for sure.

---

### Post by az on 2008-09-16
Ubuntu has VNC (remote desktop) built in.

System > Preferences > Remote Desktop

Also, to gain complete control, you can use SSH.  SSH is a secure shell.  It's a command-line login to the remote computer.

---

### Post by wewhitt on 2008-09-16
thats cool - I see where to select them to share. Leads to my next questions ... how do I connect to it?

I hate being a newb!!

---

### Post by Peter Frank on 2008-09-16
Applications->Internet->Remote Desktop Viewer->Connect. Enter the IP address of the remote machine, provided that the network is already set up and you can access that IP.

To connect to a windows remote desktop from Ubuntu, install the package 'rdesktop' in Synaptic, and type 'rdesktop [remote machine IP]' in a terminal.

---

### Post by wewhitt on 2008-09-16
Another question. If these things are setup remotely - how can one select "allow" on the distant computer. Is there a way to have it automatically allow the remote access.

---

### Post by Peter Frank on 2008-09-16
Set up the remote Linux machine by System->Preferences->Remote Desktop, under the section Security, uncheck 'Ask you for confirmation', check instead 'Password', then no one needs to be at the remote site.

---

### Post by wewhitt on 2008-09-16
I want to say thank you very much for your assistance. I would like to see a windows tech help as quickly and as awesome as you did.

---

