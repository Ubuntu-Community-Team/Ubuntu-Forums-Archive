---
title: "Canon printer"
date: 2007-08-16
forum: Desktop Environments
---

### Post by kcid2829 on 2007-08-16
I really like the Ubuntu Linux 7.04 look and feel.  After weeks fo trying to install a driver for a Canon iP1700, I've about given up.  Can't even install the Turboprint trial version for which  I keep getting dependency error messages.  I'm not on line with the Ubuntu computer, and download the files from a W# computer, and transfer them.  That seems to work well.  The last dependency message was 'libgtk1.2'.  That's when I quit trying.  My HP printer works.  Any suggestions on the Canon?

---

### Post by kellemes on 2007-08-17
Canon isn't Linux friendly at all..
Can you find additional info [here]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700")?

---

### Post by rsambuca on 2007-08-17
turboprint is extremely easy to setup in ubuntu.  Did you follow the instructions on the website?  First, in a terminal (Applications > Accessories > Terminal) and enter the following code to install libgtk1.2```
sudo apt-get install libgtk1.2
```
After it is installed, download the turboprint .deb file and double-click on it and it will automatically be installed.

---

### Post by kcid2829 on 2007-08-17
Thanks for your help.  Unfortunately, I can't download from the Ubuntu computer, so can't use the sudo apt-get command.  And I can't find the proper libgtf1.2 file using my online wind.. computer.  Any idea where the file is on the internet?

---

### Post by kcid2829 on 2007-08-17
Couldn't find the libgtk1.2 file. This really isn't easy as one has to do a lot of other work first.

---

### Post by rsambuca on 2007-08-17
To be perfectly honest, ubuntu is a total pain if you don't have an internet connection.  Anyways, all of the ubuntu packages can be found at [http://packages.ubuntu.com](http://packages.ubuntu.com)

The libgtk1.2 deb is here:  [http://packages.ubuntu.com/feisty/misc/libgtk1.2-common](http://packages.ubuntu.com/feisty/misc/libgtk1.2-common)

Just press the "all" link for your cpu type.

Normally, when you do the apt-get install libgtk1.2 command, all the dependencies are installed for you as well, but since you are doing it manually, you will have to make sure you have all of the packages installed that libgtk1.2 requires.  Without knowing what you have already installed on you system, I will list the dependencies for you, which you can download from the first link above.

libgtk1.2 depends:  

libgtk1.2-common
libc6
libglib1.2
libx11-6
libxext6
libxi6

Hopefully, you will have all the packages that these ones are dependent upon!

Good luck, and let us know how it goes.

---

### Post by kcid2829 on 2007-08-18
I downloaded all of those depemdncy packages, and installed all except
libxext6 and libxi6, because the synaptic package manager said they were installed.  Then double clicked the Turboprint deb icon on the desktop, and got an error dependency message referring to libgtk1.2.  Is it the same as libgtk1.2 common?  Help!

---

### Post by rsambuca on 2007-08-18
Sorry kcid, I gave you the wrong link for the main libgtk1.2 deb!  The link I gave you  was for libgtk1.2-common, which is a dependency of libgtk1.2.  So don't worry, you need everything you installed anyways.

The link for libgtk1.2 is here.  You will have to select the correct one for the architecture of your installation.

[http://packages.ubuntu.com/feisty/libs/libgtk1.2](http://packages.ubuntu.com/feisty/libs/libgtk1.2)

Good luck.

---

### Post by kcid2829 on 2007-08-18
Thanks.  I'm giving it a try now.  Will let you know.

---

### Post by kcid2829 on 2007-08-18
Thanks for your continued help, rsambuca.  I got the turboprint 1.96 deb file to finish without an error dependency message.  It put two icons on the desktop,  one is Turboprint-setup.  Running that one does nothing but asks for a keyfile.  The second is Turboprint-Config.  running that one results in an error message 'Could not open configuration file!  Start turboprint setup / xtpsetup first!'  What does this mean?  I'm at a dead end with this turboprint thing!  I have RPM files, if I could figure out how to alien them to deb files.

---

### Post by rsambuca on 2007-08-18
I think I ran tpsetup next.  Try opening a terminal and entering```
tpsetup
``` (I am not sure, but try it without "sudo" first.)

---

### Post by kcid2829 on 2007-08-19
Finally got the Canon iP1700 to print (altho with the Logo, which makes the trial version of Turboprint useless).  Thanks for your great help, rsambuca.  I had to go to the terminal and type 'sudo tpsetup'.  Then had to do a few tries with the choices that came up.  Thanks, again.  Now I'd like to get alien installed to use an RPM package.

---

### Post by rsambuca on 2007-08-19
If you lower the resolution to draft, it doesn't print with the logo on it.  You almost can't tell the difference if you are just printing text documents, or low resolution images like mapquest maps, etc.  Not great for photos, obviously!

---

### Post by rsambuca on 2007-08-19
For alien, you can just use the same procedure you did when you installed the libgtk1.2 packages.  The [[COLOR="Red"]alien package is here[/COLOR]]("http://packages.ubuntu.com/feisty/admin/alien").  Just make sure you also download the dependencies that are listed with the red dot.

---

### Post by kcid2829 on 2007-08-20
Thanks, rsambuca, I'll give both tips a go.  Have a good one.

---

### Post by iheartubuntu on 2007-10-13
Are there any other options available out there for Canon printer users? No drivers available in Turboprint for my Cannon. Ive got a L380 fax/copier/printer. In Windows, the driver has other numbers attached to it like:

CanonFP - FP-L170 / MF350 / L380 / L398

I had tried Ubuntu 7.10 Gutsy and it still could not find the printer.

---

