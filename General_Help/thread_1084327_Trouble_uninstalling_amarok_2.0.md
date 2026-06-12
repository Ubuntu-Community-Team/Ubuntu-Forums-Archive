---
title: "Trouble uninstalling amarok 2.0"
date: 2009-03-01
forum: General Help
---

### Post by ddigler on 2009-03-01
I found a post which is now eluding me that gave me a two step process on how to install Amarok-2.0.1.1 through terminal. Now i don't want it any more and am trying to remove it. 

'sudo apt-get remove amarok' returns 'package not installed nothing removed'

Yet when i 'sudo amarok' it launches the player.

What gives?

No clue how to uninstall and need help. thanks.

---

### Post by Master_Odin on 2009-03-01
Just run the following command:
sudo apt-get install amarok-kde4

It'll automatically remove amarok (and related libraries) as well as install amarok-kde4.

You'll also most likely want to add the Amarok 4 to the software sources area, so open that up (System > Administration > Software Sources) > Third Party Sources > Add and type in:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

That's all you'll need to do to get Amarok 4 up and running. :)

Of course, if you want to downgrade (since Amarok 4 is well, like KDE 4.0 :P) just run:
sudo apt-get install amarok

---

