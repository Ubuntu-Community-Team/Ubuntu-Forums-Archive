---
title: "Network Settings Won't Stay Fixed"
date: 2005-12-04
forum: Desktop Environments
---

### Post by rshol on 2005-12-04
New to Kubuntu (but not to Linux), running 5.10 updated with KDE 3.5 packages and from the Universe and Multiverse on a Dell Latitude laptop with an Orinoco Classic Gold wireless card.  I use static IP addresses and 128 bit WEP.

Questions:

1)  IP address of my internet gateway is not rembered from one boot to the next whether or not I put it in throught the Network Settings section of System Settings or manually put it in /etc/network/interfaces.  I have to shut down the card, put in the gateway and then start it again.  Is there a fix for this?

2)  Where is the correct place to enter the wireless networking information.  There is a place to configure it in the main networking section and also under the connections tab there is a wireless networking section.  No matter which section I enter it in, it is not saved.  Or rather its appears to be saved but I have to activate in connections==>wireless networking.   What's up here, what am I doing wrong.

3) Unrelated to networking, where can I get debs for Firefox 1.5.

Thanks.

---

### Post by rshol on 2005-12-05
Bump and a couple more questions.

1)  The settings for the gateway are staying stable with a wired connection, we'll see what they do this evening with a wireless connection.  Don't know why that should now work, I didn't change anything.

2)  ndisgtk.  I installed it with apt-get which also installed some dependencies.  But it won't run.  I get the error message:

Failed to load GTK bindings. Please check your Gnome installation.

Bummer.  Thanks for any help.

---

### Post by rshol on 2005-12-05
Gave up on debs for Firefox 1.5, the backports guys apparently haven't finished their work yet.  Installed from Mozilla.  Works fine.

---

