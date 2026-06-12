---
title: "[HOWTO] From Ubuntu To Geubuntu Desktop"
date: 2007-12-21
forum: Desktop Environments
---

### Post by intilinux on 2007-12-21
[Geubuntu Luna Nuova]("http://distrowatch.com/weekly.php?issue=20071210#review") has been released and it rocks, boys.


[IMG]http://farm3.static.flickr.com/2375/2094706775_4eae8322bf_o.jpg[/IMG]

You can Install Geubuntu in two ways: from the [Live CD]("http://geubuntu.intilinux.com/Download.html") (see this Guide if you're confused) or using the deb packages on any Ubuntu based system (Ubuntu, Kubuntu, Xubuntu, Edubuntu, Ubuntu Studio, etcetera). The Packages has been released for i386 based systems too.

**Getting Started**

If we're installing Geubuntu on a normal *buntu system, first of all, we need to install an encripted key and add the Geubuntu 7.10 Luna Nuova and E17 repositoryes to our sources.list file.
As for importing the public key we need, just open a terminal window (Applications --> Utilities --> Terminal) and enter inside it the following two simple commands, one after the other. Press enter for each command of course:

```

wget http://lut1n.ifrance.com/repo_key.asc
wget http://geubuntu.intilinux.com/repos/amd64/gutsy/geu-key.key
sudo apt-key add repo_key.asc
sudo apt-key add geu-key.key
```
 

Now we just need to add the Geubuntu 7.10 and E17 repositories to our sources.list file.

Keep your terminal opened and enter the following commands, press enter for each command of course.

```
sudo gedit /etc/apt/sources.list
```
 

Instead of gedit, write kate if you use KDE or mousepad if you use Xubuntu. If you want to modify the file from terminal, then write nano instead of gedit.
In the text editor, reach the end of the file and add the following text:

**32Bit users**

```
## Geubuntu
deb http://e17.dunnewind.net/ubuntu gutsy e17
deb http://download.tuxfamily.org/geubuntu/ gutsy/
```

**64Bit Users**
```
## Geubuntu
deb http://e17.dunnewind.net/ubuntu gutsy e17
deb http://geubuntu.intilinux.com/repos/amd64 gutsy/
```
 
Be sure to leave and empty line at the end of the text file, save it and close the text editor you've been using. Now, from the terminal, enter the following commands:

```

sudo aptitude update
sudo aptitude upgrade
sudo aptitude install geubuntu-desktop
```
 
Agree to any request from aptitude and in a few minutes the Geubuntu system will be installed. Now have a cup of coffee and when the installation will be completed, move to the "Final Configurations" Chapter on this page.

**Final Configurations**

In order to complete our Geubuntu installation, we now have to click on the menù entry: Applications --> System Tools --> geubuntu-configuration: you'll be asked to enter the system password. Wait until the Login Winow preferences window will appear where you'll be able to choose your prefer GDM Theme clicking on the Local tab. Now you can logout. When you'll be on the login page again, remember that you now have the option, clicking on the Sessions button, to choose Enlightenment. This will start a Geubuntu session.


[URL="http://geubuntu.intilinux.com"]
HOMEPAGE[/URL]

---

### Post by K.Mandla on 2007-12-21
Moved to Desktop Environments.

---

