---
title: "Panel Aplets like Kaquarium, Kweather, QuickLauncher, etc"
date: 2006-04-17
forum: Desktop Environments
---

### Post by pranav on 2006-04-17
I have an external taskar.

The main panel is filled with Kaquarium, Kweather, Quicklauncher, Lock/Logout applet, Kdict (dictionary applet) Kmenu button and the usual desktop pager.

I want suggestions on any other cool applets that i can download n install.

Tell me what is that differnt thing dat u have installed on your panel which is unusual and cool. Pls post how it can be installed.

Mention the repository that needs to be enabled n the commands as well.

---

### Post by gingermark on 2006-04-17
I WANT! I WANT! I WANT! :)

Anyways, I don't use it, but have a look at KBFX. It replaces your K-Menu Button, and you can use pretty much any image you want for it, You can download a deb for Dapper [here](http://kde-apps.org/content/show.php?content=37934).
EDIT: You might want to also read the full description [here](http://www.kde-apps.org/content/show.php?content=24898) - it does a little more than it did in previous releases!

No so much for the panel, but SuperKaramba (which should be in the Dappar repos, not sure which one, but there aren't exactly many) allows you to download and run many desktop applets (otherwise known as widgets). There's some pretty cool stuff available for it.

---

### Post by pranav on 2006-04-17
I checked out the links above... too much stuff, i am confused. Please suggest something that you like and vouch for. The thing is i am new to GNU/Linux and i do not knw how to "uninstall" or remove something i will install. So i am afraid i might screw up dependencies.

---

### Post by gingermark on 2006-04-17
OK, well you need to learn how to install and remove programs before you ask that kind of question then!

First off, if you haven't already, do the following:

Press Alt+F2 and type 'kdesu kate /etc/apt/sources.list'
Enter your password when prompted.
A text file will open. Remove any '#' symbols that occur before a line that begins 'deb'. Save the file.

To install SuperKaramba:
Open Konsole and type
```
sudo apt-get update
sudo apt-get install superkaramba
```
To install KBFX:
Download the .deb file somewhere (for example your Desktop)
Then in Konsole do
```
cd Desktop
sudo dpkg -i 37934-kbfx_0.4.9.1-1_i386.deb
```

To remove SuperKaramba:
```
sudo apt-get remove superkaramba
```
To remove KBFX:
```
sudo dpkg -r kbfx
```

SuperKaramba themes are available from [kde-look.org](http://www.kde-look.org), and there is an option in the program to install them.

I can vouch for SuperKaramba - it's great.
I don't use KBFX myself although I have tried it - you might like it, and this version has some cool features. Try it out, you can always remove it.

[This page](http://www.psychocats.net/ubuntu/installingsoftware.php) should help you out with installing software in general.

---

### Post by pranav on 2006-04-17
Thank you so much, your post has an invaluable lesson for me. Thanks once again. I had just learnt to use the command apt-get install program_name
but didnt knw abt the "remove". I am learning new things, and good people (like you) on the forums are patient and very helpful.

---

