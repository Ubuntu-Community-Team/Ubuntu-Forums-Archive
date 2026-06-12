---
title: "Edubuntu Classroom add on cd"
date: 2007-06-26
forum: Education &amp; Science
---

### Post by adMOMistrator on 2007-06-26
Can someone explain, how do I install the programs i the add on cd, like tuxpaint and celestia?  

Also, I thought the add on cd had language translations, how do I get those?   

And how do I get the languages into gcompris.  I installed gcompris on m XP, and it picked up all that I have installed, will it do that on linux?

And can I get the kde stuff working without a connection to the internet?  Its like I have no kde anything on my Feisty server install.  

Oh--what do I do to get mol-ras (or whatever the molecular generator is called) working, it asked for some database or file to be setup?

Thanks!

---

### Post by LaserJock on 2007-06-27
OK, number of questions there :-)

To install the apps on the addon CD you want to insert the disc once you have Edubuntu installed. It should pop up a little dialog box that asks you if you want to start the addon installer. [http://doc.ubuntu.com/edubuntu/handbook/C/ch02s03.html](http://doc.ubuntu.com/edubuntu/handbook/C/ch02s03.html) has more info and a screenshot.

I'm not positive about the best way to get the translations. One way would be to select "start package manager" when you insert the addon CD and then do a search for "language-pack" and "language-support" and install the ones for your language. It's possible that the Language Support tool  in System -> Administration would pick up on the Addon CD but I'm not sure.

I think pretty much all the gcompris languages available are on the addon CD. When you insert the Add-on CD you can select "start package manager" and then search for gcompris in the the package manager that opens up. It will have gcompris itself and then all the languages as individual packages.

Yes, the KDE apps on the Addon CD can be installed without the internet. When you first install Edubuntu Server it won't have any KDE, but the Addon CD included the needed KDE libraries for the apps on it.

rasmol uses PDB (Protein Database) files. So either give it the name of the .pdb file that you want to look at or run it from a terminal like rasmol <name of pdb file>.pdb

-LaserJock

---

### Post by prenger745 on 2008-01-30
I installed the edubuntu desktop CD on a home computer.  Can I use the server add-on CD?  Or do I need to install the server version of edubuntu first instead of the desktop  CD?

Thanks,
Dan

---

### Post by LaserJock on 2008-01-31
You can use the addon CD. It *should* work just the same as for the Server CD.

-LaserJock

---

