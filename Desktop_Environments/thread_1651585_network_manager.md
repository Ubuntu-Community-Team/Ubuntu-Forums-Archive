---
title: "network manager"
date: 2010-12-23
forum: Desktop Environments
---

### Post by shashanksingh on 2010-12-23
I just installed a very basic kde with the kde window manager.
but the network applet does not autostart, neither does it connect when started from terminal.
Im new to kde.
Plz help.

---

### Post by 3Miro on 2010-12-23
Wired or wireless?

Does it work from the LiveCD?

When you say "very basic kde" do you mean you did an alternate install to a command line and then added the basic kde package?

---

### Post by shashanksingh on 2010-12-23
well, the very basic kde means I dont know much about kde and didnt use the "kde-full" option from synaptic.
Its wired

---

### Post by shashanksingh on 2010-12-23
Its not from a live cd. I installed it from synaptic from gnome.
I think maybe I missed out some packages or something...

---

### Post by 3Miro on 2010-12-23
I think it is knetwork manager (check synaptic), but check for a network manager widget first. Right-click unlock widgets and then add widget.

---

### Post by Zorael on 2010-12-23
The behind-the-scenes networking logic was broken out of the monolithic KNetworkManager manager and implemented as a base kded module. With KNetworkManager deprecated, the new default manager is the plasmoid aptly named "network management". :3

Its package name is **[plasma-widget-networkmanagement](apt://plasma-widget-networkmanagement)**.

As a sidenote, if you look through the packages beginning with **plasma** in your package manager of choice, you can find some hidden nifties.

---

