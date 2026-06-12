---
title: "Installing Battle for Wesnoth"
date: 2007-04-23
forum: Gaming &amp; Leisure
---

### Post by Gif on 2007-04-23
Hi,

I have read about this game (Battle for Wesnoth) and it sounds great, but as a newbie I have no idea about getting and installing it. Would it be available from Synaptic?

Thanks,

---

### Post by AnRa on 2007-04-23
Applications -> Add/Remove -> search for "wes"

---

### Post by lakersforce on 2007-04-23
If you want music and all the "extras" remember to install them too. They are not included by default.

---

### Post by Perfect Storm on 2007-04-23
If you want to compile the latest: [http://gaming.gwos.org/e107_plugins/content/content.php?content.6](http://gaming.gwos.org/e107_plugins/content/content.php?content.6)

---

### Post by AnRa on 2007-04-23
> **Artificial Intelligence said:**
> If you want to compile the latest: [http://gaming.gwos.org/e107_plugins/content/content.php?content.6](http://gaming.gwos.org/e107_plugins/content/content.php?content.6)

Alternatively, you can get it [HERE]("http://www.getdeb.net/app.php?name=The%20Battle%20for%20Wesnoth"):)

---

### Post by Perfect Storm on 2007-04-23
Aye, but my methode you can try out the development release 1.3.1 ^_^

---

### Post by AnRa on 2007-04-23
> **Artificial Intelligence said:**
> Aye, but my methode you can try out the development release 1.3.1 ^_^You're right, i didn't read the link, I'm sorry. :(

---

### Post by brigit on 2007-05-23
can anyone help me, I tried installing wesnoth by the methord shown on UGA and it didn't work after the make stage, however I think its left some of it behind as when I reinstalled the older wesnoth that didn't work any more! I'm not shore how to go about cleaning this all up, as this was my first compileing effort
Please help its the school holidays and the kids are hating me for killing all of ours best game.

---

### Post by Ozor Mox on 2007-05-23
If you search for 'wesnoth' in Synaptic you can select individual components to install or not install like campaigns, music, etc. If you mark 'wesnoth-all' for installation, that will install everything.

---

### Post by brigit on 2007-05-23
sorry my post wasn't very clear ,who can be with ten children in the house?, I was trying to install a newer vertion, and the problem now is that didn't work so even enstalling through synaptic dosen't work.

---

### Post by jamesjtucker on 2007-05-24
first i would do a  'dpkg -l | grep wesnoth' to see currently installed wesnoth packages. Then do a 
 'sudo apt-get remove wesnoth' at the command line to clean out any current wesnoth installs. 

after this  'dpkg -l | grep wesnoth'  should not list any wesnoth packages. 

Then follow whatever instructions you want to get your new install compiled. 

Were you having issues compiling the software or running it? If it compiled and installed properly, running 'wesnoth' from a command prompt may tell you what is causing the game to crash/not load/etc. 

let us know if you are still having problems after that.

---

### Post by brigit on 2007-05-30
Thanks so much for your help I intalled the two stray files that some how were on the system.
However after installing the .deb files i get this error on running the wesnoth comand
Battle for Wesnoth v1.3.2
Started on Wed May 30 16:24:08 2007

started game: 3701409069
open /dev/sequencer: No such file or directory
could not initialize fonts
exiting with code 0

---

### Post by jamesjtucker on 2007-05-30
Try moving or deleting the .wesnoth directory in your home dir and starting wesnoth again from the command line..

---

### Post by TheDudeAbides on 2007-09-08
Thanks all this was very helpful!!!

Now back to my crippling gaming addiction :)

---

### Post by rcdegges on 2007-09-08
To install the "Battle for Wesnoth" (a great game), simply open a terminal and type the following:

sudo apt-get install wesnoth

when it asks you for a y/n answer, just type y to answer yes. It wil auto install it for you.

-Randall

---

### Post by mivo on 2008-01-25
Sorry for resurrecting an older thread, but is there a currently recommend way of getting the latest Wesnoth (dev) version? The link above is no longer working and the version at GetDeb is also outdated (and for Feisty). The Gutsy repo does have 1.2.8, which is the latest stable version, but I'd like 1.3.x. 64-bit is preferred.

Thanks. :)

---

### Post by Perfect Storm on 2008-01-26
[http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth](http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth)
should also work for 32-bit

---

### Post by mivo on 2008-01-26
> **Artificial Intelligence said:**
> [http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth](http://gaming.gwos.org/doku.php/guides:64bit:battle_for_wesnoth)
should also work for 32-bit

Thanks! There were two missing dependencies not listed on the page:

libboost-dev
libboost-iostreams-dev

Once I installed those from the repository, it compiled flawlessly. :) The resulting .deb file worked as well, though the installer claimed the same version had already been installed (it wasn't), but  hitting "reinstall" worked just fine.

---

### Post by Perfect Storm on 2008-01-26
ok thanks. It seems bcp isn't depending on them - which is strange as it's a meta package for the whole damn thing LOL
Going to make the changes. Nice to get feedback on the guides so I can correct them if I missed something ^_^


Just change the number when do checkinstall a number higher or something in version.

EDIT: Meh....it seems I forgot bcp in the guide.
Edit edit. Guide fixed.

---

