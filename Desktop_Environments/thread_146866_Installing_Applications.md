---
title: "Installing Applications"
date: 2006-03-19
forum: Desktop Environments
---

### Post by Geffers on 2006-03-19
I'm relatively new to ubuntu having previously used Mandrake.

Mandrake used RPMs for installation but I understand ubuntu is based on debian and different installation methods used.

If I want to install a program on my Kubuntu system what type of Linux files should I be searching for.

Also, will I need to use the command line for installation (eg make, instal) or can I use one of the graphical utilities supplied with Kubuntu.

Geffers

---

### Post by niviche on 2006-03-19
You can install apps:

-by using Adept to look in the repositories

-by downloading a .deb package and right click it to install it.

-build it from sources. You will need to install (through Adept) the "build-essential" package for this.

---

### Post by TLE on 2006-03-19
I don't know about Kubuntu, but in Ubuntu you can press the little help button in the top of the screen or click the desktop once and press F1, this wil bring up the help screen, then there should be an entry called the starter guide. And in the starter guide is a section on installing software. Have a look at it, and then if you still have questions (or if that particular help function is not available under Kubuntu) write back here.

---

### Post by vidak on 2006-03-19
[QUOTE=Geffers]I'm relatively new to ubuntu having previously used Mandrake.

Mandrake used RPMs for installation but I understand ubuntu is based on debian and different installation methods used.

If I want to install a program on my Kubuntu system what type of Linux files should I be searching for.

Also, will I need to use the command line for installation (eg make, instal) or can I use one of the graphical utilities supplied with Kubuntu.

Geffers[/QUOTE]

If you like command line interface better, you can use aptitude for package management - I think it's stronger in searching packages (you can use regexp)
or if you have downloaded a .deb package, you can install it with 
dpkg -i foo.deb

For installing a package from a tarball, unzip the file with 
tar -xzf foo.tar.gz
./configure
make
sudo make checkinstall
(you will need the checkinstall tool, which can be installed eg. by 
*apt-get install checkinstall*)
and finally we got the dselect utility, for the real fans... ;)
personally, I prefer aptitude...

---

### Post by niviche on 2006-03-19
[QUOTE=vidak]
or if you have downloaded a .deb package, you can install it with 
dpkg -i foo.deb[/quote]

True. Note that the right click action "install package" does exactly this.

---

### Post by aysiu on 2006-03-19
Read this:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Geffers on 2006-03-19
Thanks everybody for the replies, I'm getting there but may be having a wee problem confusing programs that are for the Gnome desktop rather than the KDE.

I've already had a problem with ndisgtk, installed but couldn't get it to run so ended up using the command line as per advice from a different thread.

geffers

---

