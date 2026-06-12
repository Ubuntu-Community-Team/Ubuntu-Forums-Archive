---
title: "New to this OS"
date: 2007-10-03
forum: Dell  Ubuntu Support
---

### Post by totallinuxnoob on 2007-10-03
Hi, I just received my Dell Inspiron 1420 preloaded with Ubuntu Fiesty and have a few questions. 

<s>how do install a network printer (samsung ml-5270), how do I install themes from gnome-look and what is the usual password for root?

---

### Post by pay on 2007-10-03
To install themes from gnome-look, go to System > Preferences >   Appereance and then click install. Navigate to your downloaded them and then your done. Ubuntu uses sudo to access root priveleges. The sudo password is your uses password. If you want to use su like in other distros, you'll have to do```
sudo su
```Or just put sudo infront of the command that needs root priveleges like ```
sudo dpkg -i *.deb
```

---

### Post by sawjew on 2007-10-04
This link [http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware&sectionIdCode=setupYourWindowsPrinterAsANetworkPrinterInUbuntu]("http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware&sectionIdCode=setupYourWindowsPrinterAsANetworkPrinterInUbuntu") gives a good tutorial on setting up a network printer.  Just make sure you have shared your printer on Windows first.

---

### Post by pheonixind on 2007-10-04
Also, going to ubuntu>add/remove> and installing art manager will help.  Usign the art manager you can download new looks that are compatable with Ubuntu without messing the OS up.  As for installing the network printer, I have never done that with Linux so I have no idea.

---

### Post by dandanplan on 2007-10-05
Hello,
if you want to install a network printer you can open a terminal (alt+F2) and type gnome-terminal and type there:```
gnome-cups-manager
```
(I had sometimes problems with setting the printer permanently so I started it as root with sudo)
```
sudo gnome-cups-manager
```

There you will have the same dialogue as in sawjew's link. It is just another way to start the cups-manager. 

And for the gnome-themes you can also download them from [http://www.gnome-look.org/](http://www.gnome-look.org/)  to your Desktop and open the Themes Dialogue (System -> Preferences -> Theme), drag and drop the archive into the window. The theme will be installed automatically. 
But you can only install the Gtk, Metacity, Icon Themes and the Mouse Themes in this manner and window. GDM Themes are for the Login Window. Compiz and Beryl are for the Desktop Effects.

---

