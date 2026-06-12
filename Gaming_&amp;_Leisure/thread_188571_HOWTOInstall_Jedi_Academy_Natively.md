---
title: "HOWTO:Install Jedi Academy Natively"
date: 2006-06-04
forum: Gaming &amp; Leisure
---

### Post by deathbyswiftwind on 2006-06-04
Alright this is my first howto so please bear with me. I am writing this howto on Jedi Academy. This is still a pretty popular game and can be purchased from walmart for only 10 dollars. Anyways here it is

First you need to download,install, and configure wine. I wont go into this because there are many previous threads that describe this. 

Second download the Jedi Academy loki installer. Here is a [link]("http://www.liflg.org/?what=dl&catid=7&gameid=44&filename=jedi.academy_1.01-multilanguage-2.run") to it. While it may not always work you can also download it from [http://www.liflg.org/]("http://www.liflg.org/")

Now open a terminal/Konsole and go to where you downloaded the file.
Enter the following command.

chmod a+x jedi.academy_1.01-multilanguage-2.run

After that enter the following command

./jedi.academy_1.01-multilanguage-2.run

A graphical installer will appear and guide you through the installation. Depending apon where you would like to install it you may want to add sudo in front of the last command

sudo ./jedi.academy_1.01-multilanguage-2.run

That enables it to install in the /usr/local/games directory. I prefer to install all games in my home directory so I own all and can change/edit anything I want without having to change ownership and such.

Anyways be sure that when the installer asks for cd2 you right click your cd icon and click eject. Then insert the second cd. Ive tried it by just opening the drive by just pushing the button and for some reason it makes the installer hang.

The loki guys ever have an additional mappack you can download for jedi academy. Here is the [Link]("http://www.liflg.org/?what=dl&catid=7&gameid=44&filename=jedi.academy_bonusmaps.run")
 
Once again open the terminal/konsole and enter the following command

chmod a+x jedi.academy_bonusmaps.run

./jedi.academy_bonusmaps.run 

or for the installs in usr/local/games/ use this command

sudo  ./jedi.academy_bonusmaps.run

Anyways I hope this helps someone. It works great for me everytime. Enjoy my fellow padawans and may the force be with you

---

### Post by Gnobody on 2006-06-04
[LEFT]This Loki installer uses Wine, it is not exactly native but simple to get up and running regardlessly.  Just thought I'd clear that up.
[/LEFT]

---

### Post by amunimanghi on 2006-06-22
This is great. I just have 2 small but important problems. The first is that I have no sound entirely. The second is the game doesn't show **any** servers. I have the Internet icon selected. Do you know how to fix these?

---

### Post by deathbyswiftwind on 2006-06-22
Okay for your sound it gives you the hint when you run it. Open a terminal and config your wine. You have to select emulation in the options for hardware. As far as your connection I have no idea. Would you run from terminal and see if it gives you an error. I know in SOF2 it tells me that the networking is always set to LAN so it wont let me play online. Probably something along the same lines. One thing I did notice is when I had cedega installed for wow everything worked great my ja works great but my sof not so hot

---

### Post by amunimanghi on 2006-06-22
I switched back to cedega because it would let me play online. Bummer huh. The only problem is that is sometimes doesnt detect the sound card...even if all the sound applications are dead. Thanks. I'll fiddle around with it later though.

---

### Post by Tris2006 on 2006-09-15
Well thanks to this howto I got the game installed, but I cant get it running. I get an OpenGL error.
[IMG]http://img87.imageshack.us/img87/7236/jkalh7.jpg[/IMG]

Any ideas?

EDIT: Oh yeah forgot to mention Im using a GMA900

EDIT2: Ok fixed the openGL problem by commenting out Load "dri"
       but now I get a missing ui.dll error. :|

---

