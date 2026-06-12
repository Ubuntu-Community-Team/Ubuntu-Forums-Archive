---
title: "Installing Java for Firefox"
date: 2005-01-28
forum: Desktop Environments
---

### Post by cmilhaus on 2005-01-28
In the instructions posted elsewhere on line, the "how to" states to add two lines to the following file:** /etc/apt/sources.list**
Ok, I found the file!! However it is "read only" and I can't seem to find anywhere around that I can change the properties of the file to add the two lines in order to add Java.
So if someone can tell this semi-reformed windows user how to do this I would be most grateful and will joyfully be on about installing Java on my Linux Distribution.
I really love Ubuntu. It's my main distribution and I can't wait for the next release, I saw prewiews on it yesterday
Thanks so much fo any leads.

---

### Post by mirons on 2005-01-28
Why change the permissions of the file? Just edit it as root with something like

$ sudo emacs /etc/apt/sources.list

---

### Post by hashimoto on 2005-01-28
or 
sudo gedit /etc/apt/sources.list

anyway, it is read only to you as a normal user. You need to gain the super used rights before editing the file. Hence "sudo". emacs and gedit will start the "notebook" for editing and the path leads to open the right file.

BR
Hashimoto

---

### Post by WirelessMike on 2005-01-28
Why not just add the repository using Synaptic?

You could always add this repository:
[URI] [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) [Distribution] warty [Section] java

This repository will give you the choice to install sun-java 1.3, 1.4 or 1.5 (I suggest 1.4).

To add repositories in Synaptic, Click Settings -> Repositories, then click New in the Repositories window.  Refresh your list after that, and you should see a few sun-java apps you can install.  Install one, then create a link to the appropriate java source (like ns610-gcc32/libjavaplugin_oji.so) in the mozilla-firefox plugins directory.

---

### Post by kosmic on 2005-01-28
or instead you could use the old way.


get the Java package from -> [www.java.com](www.java.com) (Java JRE 1.5)


then do - chmod +x (the name of the file you just downloaded, ex.: if the name of the file is JAVA_JRE_1.5 you shoul do **chmod +x JAVA_JRE_1.5** )

then ./JAVA_JRE_1.5, and this will create another directory

now become root (su -) and do - mv /new_directory /usr/java
or do (sudo mv /new_directory /usr/java)

now make a symbolic link to install the java plug in.

as root do -  ln -s /usr/java/plugins/i386/ns7/libjavaplugin_oji.so /firefox_directory/plugins/libjavaplugin_oji.so

if you can't become root then append **sudo** tho the begining of the file

and the last step a symbolic link to the java executable

ln -s /usr/java/bin/java /usr/bin/java

and voila java in firefox.

Hope I didn't forget nothing because I'm at work, and using windows right now

---

