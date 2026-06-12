---
title: "GnoMenu issues"
date: 2010-02-11
forum: Desktop Environments
---

### Post by benjamin.s.vaccaro on 2010-02-11
Hello, I have recently undergone some renovations of everything in Ubuntu. I've added beryl themes to Emerald Theme Manager, added folder styles and control styles to Appearance and now I have discovered that I can change the GnoMenu (as I learned its called). So I've downloaded the zips I liked from [www.gnome-look.org](www.gnome-look.org) and then I extract but I cannot figure out how to apply it or choose different themes for GnoMenu.

This is what I have done so far.
Installation on Ubuntu:

Save the GnoMenu file to your desktop (Gnomenu)

[https://launchpad.net/gnomenu/trunk/2.2](https://launchpad.net/gnomenu/trunk/2.2)

Once it's downloaded, right-click the file and choose 'Extract Here'.

Next you need to make sure the correct dependencies are all installed, so open a terminal (Applications >> Accessories >> Terminal) and type in :

sudo apt-get install python python-xdg python-cairo python-gconf python-xlib deskbar-applet

Next, in the terminal you need to change in to the directory you extracted earlier. Type in:

cd ~/Desktop/gnomenu

now type:

sudo make install

REF: [http://gnome-look.org/content/show.p...content=108571](http://gnome-look.org/content/show.p...content=108571)

The problem is that I don't understand, "This will install GnoMenu, it comes with some themes installed by default. Once this is done, you'll be able to right-click on your panel and select 'Add to panel'. Select GnoMenu from the list, it'll add an icon to the panel, right-click the icon and choose 'Preferences'. From there you'll be able to install the menu themes you've downloaded and download others from the Internet."

Where on 'Add to Panel' should I see this program GnoMenu? Because I don't have one.

any ideas on what I'm doing wrong or if there is something else I should be doing? 

(Please refer to my signature to see computer specs.)

---

