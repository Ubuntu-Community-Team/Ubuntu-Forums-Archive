---
title: "KDE linux software may run on GNOME Linux and vice versa ?"
date: 2009-01-30
forum: Desktop Environments
---

### Post by lse123 on 2009-01-30
KDE linux software may run on GNOME Linux and vice versa ?

---

### Post by Hooya on 2009-01-30
Yes.  In fact, you can have kubuntu and regular ubuntu at the same time!

sudo apt-get install kubuntu-desktop
sudo apt-get install ubuntu-desktop

depending on which flavor you already have.  You can then choose which one to load at your login screen.  All the apps will run on any flavor of ubuntu.

---

### Post by sub2007 on 2009-01-30
Yup that's correct. Just install what you want through the repositories and it will install the relevent KDE libraries.

The main drawback is that the applications are not GTK integrated - they use Qt and therefore will not use whatever themes you have on GNOME. Many people feel that this is a drawback. Also the load times can be longer than the application would be natively (ie using KDE). Finally, not that I've noticed, is that some features may not work running it under GNOME as they would work if you run it natively.

But I've had very good success running KDE applications under GNOME/Xfce.

---

### Post by Hooya on 2009-01-30
I run everything in Fluxbox, so gnome/kde whatever.  Since I'm not running an Gnome or KDE session it doesn't make a whit of difference exept for the theme issue on occasion.

---

### Post by lse123 on 2009-01-30
What are these ? where write and run such commands ? what to press and when to switch ?
sudo apt-get install kubuntu-desktop
sudo apt-get install ubuntu-desktop

---

### Post by sub2007 on 2009-01-30
You put those into a terminal window. After you do it you will need to enter your password. You can also do it in a Synaptic Package Manager window (leave out the sudo apt-get install part) if you prefer the GUI. 

Be aware that they are large downloads (around 500-600MB each) and you should only run them if you want the full desktop environment and not individual programs.

---

### Post by lse123 on 2009-01-31
I have in one partition vista and to otther UBUNTU 8.10... Well to run KDE Apps like kdevelop or quanta plus, I must make a new partition or download and install the soft you refer ONLY ? Or I may run these[kdevelop or quanta plus] without any addition at all ?

---

### Post by lse123 on 2009-01-31
may upgrade ubuntu 8.10 to kubuntu 8.10 or newer ?

---

### Post by sub2007 on 2009-01-31
You should be able to run KDevelop and Quanta Plus without installing the whole of KDE into your current install of Ubuntu. Just enter into a terminal window:

sudo apt-get install kdevelop quanta

It will install a lot but you won't have to run a separate instance of KDE to use the programs. You definitely don't need a new partition.

---

### Post by lse123 on 2009-02-01
How to appear the "terminal window" ...? what to press after insert THIS command ? to install all KDE I must use:
sudo apt-get install kubuntu-desktop
???
this can be stopped and recontinued , is download , isn't it ?
can install this from kubuntu 8.10 cdrom ?

---

### Post by lse123 on 2009-02-01
to install all KDE, means no need for kde libraries any more ? is it needed backup ALL the DATA first ?

---

### Post by lse123 on 2009-02-01
how many MBs the download [quanta & kdevelop] OR [KDE ALL] for ubuntu 8.10 ? I must do this and AFTER run the installation file eg quanta plus ?

---

### Post by vancouverite on 2009-02-01
Hi lse123,
I think the best way for you to install the programs you want is using the graphical package manager.  The following should work to get your KDE apps working.

Go to *System* -> *Administration* -> *Synaptic Package Manager*

It will ask you for your password because you are about to perform system maintenance, and then *Synaptic* will start.  Once it has loaded select *search* and enter the name of the program that you want to install, e.g. "kdevelop".

It will return a list of packages that mention kdevelop.  In general the most basic name will be the package you want, but read the descriptions to be sure.  In this case I see "kdevelop" and when I click on it I see that it is what I want in the description below.

Right click on kdevelop and select *Mark for installation*.  When you do this it will open another window telling you the names of other packages that need to be installed, many of which are KDE.

Select *Mark*.  If you want to know how much disk space will be used, on the bottom left select *Custom Filters* and then from the list above select *Marked Changes*.  It will show you a list of the packages that you are about to install and on the bottom of the window is says (for me anyway) "7 packages listed, 1514 installed, 0 broken. 7 to install/upgrade, 0 to remove; 46.8 MB will be used".  Your numbers will likely be different, but the last is the space needed.

Select *Apply* from the top and confirm your way through.  It will automatically install the program and you are good-to-go.  Go to *Applications* and it should be listed somewhere in one of the sub-menus.  If not, log out and then log back in and check again.

If you find that there is some functionality missing, find kdevelop in *Synaptic* again, right click on it, and look at the packages that appear under *Mark Recommended for Installation* and *Mark Suggested for Installation*.  You might just install all of those to be sure you have full functionality.

Hope this helps.
Van

---

### Post by lse123 on 2009-02-01
I must do this[INSTALL PACKAGES/REPOSITORIES/LIBRARIES OF KDE] **and AFTER run the installation file** eg quanta plus ?

---

### Post by lse123 on 2009-02-02
I already installed=extracted quanta plus but not install the repository on ubuntu 8.10, is needed **after **install/download repository to reextract ? I must delete any prior re-extracting ?

---

### Post by maybeway36 on 2009-02-02
Did you extract a .tar.gz? It's easier to not use .tar.gz and use Synatpci or Add/Remove Software when you can.

---

### Post by Hooya on 2009-02-02
Think of Synaptic as a big install CD.  You select what programs you want to install, click the "Apply" button and they download and install for you.  You don't need to download or extract anything from any website.  It's all done for you within the Synaptic program.

---

### Post by lse123 on 2009-02-02
I already extract a .tar.gz[quanta], what to do now ? DEL it ?

For Synaptic :  you still have the download file as backup , via this way ?

---

### Post by Hooya on 2009-02-04
Forget the tar.gz file.  Delete it and anything you've extracted from it.

You do not need to worry about downloading backups or anything using synaptic.  Just try it and you'll see.

---

### Post by lse123 on 2009-02-05
if i do not DEL it, any conflict/problem ? how delete extracted files ?

---

### Post by jacksaff on 2009-02-05
No, there will not be any problem if you unpacked the tar file, but as you will not be using it you may as well delete it to free space.

---

### Post by brainac0cult on 2009-02-05
of course but dont ever leave ubuntu forums,,, not ever!!!!

---

### Post by lse123 on 2009-02-07
running 
sudo apt-get install kdevelop quanta
or from Synaptic, success install indicated by an icon to start app, in the menues ? no icon , means no success ?

---

### Post by sub2007 on 2009-02-08
KDE packages sometimes don't make icons in the menu. Try typing into a terminal the name of the package (so type "kdevelop" or "quanta" and see if it is able to run).

---

### Post by lse123 on 2009-02-08
is any way make a desktop icon or menu item ?

---

