---
title: "frames of all the windows have disappeared"
date: 2008-12-13
forum: General Help
---

### Post by fababhi on 2008-12-13
I installed XGL initially and observed the 3D effects, later i tried installing Compiz-fusion. here are the steps i followed :

Open a terminal (Applications -> Accessories -> Terminal for GNOME users or KMenu -> System -> Konsole for KDE users) and type:

CODE
sudo apt-get -y remove compiz-core desktop-effects

Leave the terminal open and go to System -> Administration -> Software Sources, click on the second tab (Third-Party Software), then click on the "Add" button and paste the following code:

CODE
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

Click the "Add Source" button after you pasted the above code and do the same for the following code:

CODE
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

Don't close the Software Sources window yet!

In the terminal window, type:

CODE
wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)

CODE
sudo apt-key add DD800CD9.gpg

Now click the "Close" button on the Software Sources window and you will be asked if you want to reload the information about available software, so click the "Reload" button and wait for the window to disappear.

Copy/Paste the following lines in the terminal window:

CODE
sudo apt-get update

sudo apt-get -y upgrade

FOR GNOME USERS:

CODE
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf

FOR KDE USERS:

[B]CODE
sudo apt-get -y install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-kconfig

Now, if everything was correctly installed and you didn't encounter errors, press ALT+F2 and type:[/B]

CODE
compiz --replace

I guess there was problem wid the above procedure but my oversmartness messed things up.. here's wat i did :

i executed the highlighted code above and ran into the follwing error :

sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcompizconfig-backend-gconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libcompizconfig-backend-gconf has no installation candidate.


The statement after dat code in the procedure did mention that

 Now, if everything was correctly installed and you didn't encounter errors, press ALT+F2 and type:[/B]

CODE
compiz --replace

But in my case the command dint execute correctly and i went ahead and re-installed compiz-core which i was initially asked to remove. so i guess sumthing went wrong there...later i followed the remaining steps and found dat all the programs dat i open are frameless, meaning the minimize, maximize buttons had disappeared and yes the programs remain attached to the panel above. i cant move them....let me tell u, XGL worked properly....but i am in dilemma now..things look shabby...please help....

---

### Post by Kisil on 2008-12-13
I had a similar problem when I was first setting up Beryl.  There was a setting that let you switch between Metacity and Emerald as the window decorator, and when I enabled Emerald, my windows had no frames.  I don't remember how I eventually fixed it, and it probably wouldn't apply anyway since I'm not using XGL, but as a temporary fix, try switching window decorators.

---

### Post by Wartender on 2008-12-13
maybe ```
metacity --replace
``` will work?

---

