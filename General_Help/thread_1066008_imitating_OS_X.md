---
title: "imitating OS X"
date: 2009-02-10
forum: General Help
---

### Post by u'b'u'n't'u on 2009-02-10
I love playing around with the appearance of my desktop, but I need help on this one. My desktop looks almost exactly like leopard except for the to menu bar. How can I get the mac-like toolbar like this one:

[http://www.slipperybrick.com/wp-content/uploads/2007/10/mac-osx-leopard-available.jpg](http://www.slipperybrick.com/wp-content/uploads/2007/10/mac-osx-leopard-available.jpg)

How do I get the File, Edit, View, Go, Window,and Help buttons

(im a n00b)

---

### Post by dorkizzle on 2009-02-10
i think you are looking for gnome global menu.

[http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/)

---

### Post by u'b'u'n't'u on 2009-02-10
i installed the deb, yet when i add it nothing happens! when i right click and go to preferences i get a small window with nothing!

---

### Post by UbuntuNerd on 2009-02-10
you mean you want the apple logo on the left?

---

### Post by k3ttc4r on 2009-02-10
here, try this one, it worked for me..

>  Comment by Cassidy.James.Blaede,  Jan 15, 2009

Here's a link to a .deb for Ubuntu Intrepid! I converted it from the Fedora package and it seems to work just fine!

[http://sites.google.com/site/cajablatech/various-ubuntu-files/gnome-globalmenu_0.7.1-1.fc10_i386.deb](http://sites.google.com/site/cajablatech/various-ubuntu-files/gnome-globalmenu_0.7.1-1.fc10_i386.deb)


---

### Post by azwar on 2009-02-10
Hi, 

I think maybe you forgot to install the dependencies.Although installing the .deb for gnome global menu didn't asking for dependencies but this 'vala'.deb is compulsory to use with gnome global menu. 

Put this line in your repository and update.

Gnome global menu Repo.
deb [http://ppa.launchpad.net/globalmenu-team/ubuntu](http://ppa.launchpad.net/globalmenu-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/globalmenu-team/ubuntu](http://ppa.launchpad.net/globalmenu-team/ubuntu) intrepid main

Vala Repo
deb [http://ppa.launchpad.net/bruce89/ubuntu](http://ppa.launchpad.net/bruce89/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/bruce89/ubuntu](http://ppa.launchpad.net/bruce89/ubuntu) intrepid main

in terminal type 

sudo apt-get install valac gnome2-globalmenu

Then, create a hidden file in your home folder called '.gnomerc'. It should be like this "/home/azwar/.gnomerc" and copy & paste this word "export GTK_MODULES=globalmenu-gnome" without quotation in that file and save the file.

Then log out, right click on top panel and select the Global menu.

Now, you can use the menu on top panel. 

p/s : you need to remove the "user swithcer" applet from top panel first. Sometimes the global menu need reload. I follow this guide and it's working [http://nancib.wordpress.com/2008/11/26/get-the-globalmenu-without-all-of-the-hassle/](http://nancib.wordpress.com/2008/11/26/get-the-globalmenu-without-all-of-the-hassle/) (thanks PENG), but I summarize in short here.

---

