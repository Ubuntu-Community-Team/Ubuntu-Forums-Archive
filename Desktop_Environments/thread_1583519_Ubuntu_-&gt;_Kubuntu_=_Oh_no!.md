---
title: "Ubuntu -&gt; Kubuntu = Oh no!"
date: 2010-09-27
forum: Desktop Environments
---

### Post by pivotraze on 2010-09-27
So I just recently ran the default way to get Kubuntu on an Ubuntu desktop.
> sudo apt-get install kubuntu-desktop
It ran correctly and installed everything. Rebooted, and booted into KDE. NOTHING works. Running Reconk (sp?) just causes a crash after typing 3 characters for search. Whenever I try to install something, it tells me that the batch install thing failed to run because I don't have the correct permissions. So I changed to my Chromium and it told me that it couldn't connect to site (and the wireless WAS connected.)

So, since it failed so horribly, how can I remove all remnants of Kubuntu Desktop 10.10?

---

### Post by NightwishFan on 2010-09-28
Try this in the terminal. Not sure if it will work.
```
sudo tasksel remove kubuntu-desktop
```

---

### Post by pivotraze on 2010-09-28
Nope, didn't work. Here is the output:
> cody@cody-laptop:~$ sudo tasksel remove kubuntu-desktop
tasksel: aptitude failed (100)
cody@cody-laptop:~$ 


---

### Post by NightwishFan on 2010-09-28
Try this first:
```
sudo apt-get -f install
```

---

### Post by pivotraze on 2010-09-28
> cody@cody-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libubuntuone-1.0-1 python-ubuntuone libdmapsharing2 libvala-0.10-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cody@cody-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdmapsharing2 libubuntuone-1.0-1 libvala-0.10-0 python-ubuntuone
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 3,437kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157979 files and directories currently installed.)
Removing libdmapsharing2 ...
Removing python-ubuntuone ...
Removing libubuntuone-1.0-1 ...
Removing libvala-0.10-0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
cody@cody-laptop:~$ 


That is the new output. What next? Here is the output from rerunning your first command:
> cody@cody-laptop:~$ sudo tasksel remove kubuntu-desktop
tasksel: aptitude failed (100)
cody@cody-laptop:~$
It turned blue with a progress bar for a second, then went back to terminal with that error.

---

### Post by NightwishFan on 2010-09-28
You might have to remove them manually in synaptic. :(

Go to Synaptic and choose Sections, find the KDE sections. Then remove all the packages. You can sort them to show all the installed ones in a row and select them all.

---

### Post by pivotraze on 2010-09-28
*Sigh* That will just take longer than installing Ubuntu 9.10, and upgrading to 10.04, correct? :(

---

### Post by NightwishFan on 2010-09-28
Probably not actually. :)

Try one last thing first:
```
sudo tasksel install kubuntu-desktop
```
then
```
sudo tasksel remove kubuntu-desktop
```

---

### Post by pivotraze on 2010-09-28
> cody@cody-laptop:~$ sudo tasksel install kubuntu-desktop
[sudo] password for cody: 
xserver-xorg					install
cody@cody-laptop:~$ sudo tasksel remove kubuntu-desktop
tasksel: aptitude failed (100)
cody@cody-laptop:~$ 


*sigh* nope :(

---

### Post by Old *ix Geek on 2010-09-28
Just because you're having problems with KDE doesn't mean you have to remove it. It may be a simple case of some necessary files not being installed, or perhaps being corrupted.

You can use Synaptic to search for vital components of KDE and install them if they're not already installed. While there you can also reinstall anything that may be questionable.

So, if I were you, I'd log in with Gnome, use Synaptic to find KDE components that look like they should be installed (you can tell by their names and/or descriptions) and install them, then try again and see what happens.

---

### Post by damnated on 2010-09-28
This worked for me when I wanted to remove KDE. [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by NightwishFan on 2010-09-28
Packages change between versions though. That tutorial is for Lucid.

---

