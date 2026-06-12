---
title: "i need to install schooltool for my school server"
date: 2006-08-08
forum: Desktop Environments
---

### Post by foxhound_oki on 2006-08-08
hi.  i need some help fast.  i have a district inspection for my schools network, servers, and new software.   i recently about three months ago installed ubuntu server and got the hang of it.  now i have been told by hq, about two weeks ago to download and install schooltool and set it up.  could someone help me download and install schooltoon on our ubuntu server2 please.  the inspection is next week and i need this to be done.  thanks

Sean Fox
Administrative Technologist

---

### Post by computergroove on 2006-08-08
I went to schooltool.org and couldnt find any download areas. Do you have the program? What format is it in?

---

### Post by foxhound_oki on 2006-08-08
thanks for replyin here.  there is a documentation folder on the left of the window and it has setting up a deployment server and then your development environment.  there are some instructions. i followed them to number 4.  im using ubuntu server and its all shell.  so how can i download the ez_setup.py file so i can do python ez_setup.py?

---

### Post by Mike'sHardLinux on 2006-08-08
Hi!

how about this:
```
wget http://peak.telecommunity.com/dist/ez_setup.py
```
Schooltool looks really interesting. I wish I had a use for it. :D

---

### Post by foxhound_oki on 2006-08-09
> **Mike'sHardLinux said:**
> Hi!

how about this:
```
wget http://peak.telecommunity.com/dist/ez_setup.py
```
Schooltool looks really interesting. I wish I had a use for it. :D

okay...  do i have to state a specific locations to download it.  i am setting up this software in the /usr/local/share.  i need to have that file there, as where everything else is at.

---

### Post by Ramses de Norre on 2006-08-09
wget downloads to your home folder and I didn't find any option to change that in the man page, use ```
sudo cp ez_setup.py /usr/local/share/ez_setup.py
``` to copy it to the right location.

---

### Post by foxhound_oki on 2006-08-09
> **Ramses de Norre said:**
> wget downloads to your home folder and I didn't find any option to change that in the man page, use ```
sudo cp ez_setup.py /usr/local/share/ez_setup.py
``` to copy it to the right location.

will that still work for me though. ill be logged into ubuntu server.  there is not graphical interface.  just command.

---

### Post by Ramses de Norre on 2006-08-09
Well, ```
wget http://peak.telecommunity.com/dist/ez_setup.py && sudo mv ~/ez_setup.py /usr/local/share/
``` will download the file and move it over to /usr/local/share, (I changed the command to use mv, that could be more useful) and shouldn't you create a seperate folder for the app in /usr/local/share/?

If you want to do so: sudo mkdir /usr/local/share/schooltool (for example) and include that in the path for the mv command.

This are all commands so they certainly don't need a GUI;)

---

### Post by foxhound_oki on 2006-08-09
> **Ramses de Norre said:**
> Well, ```
wget http://peak.telecommunity.com/dist/ez_setup.py && sudo mv ~/ez_setup.py /usr/local/share/
``` will download the file and move it over to /usr/local/share, (I changed the command to use mv, that could be more useful) and shouldn't you create a seperate folder for the app in /usr/local/share/?

If you want to do so: sudo mkdir /usr/local/share/schooltool (for example) and include that in the path for the mv command.

This are all commands so they certainly don't need a GUI;)

okay one problem.  its all working good up to the point to where i can't logon to the server.  lol.  i have typed [http://localhost:7080](http://localhost:7080) and nothing.  i have tried my servers name.  nothing.  ive tried the static ip, nothing.  what is the problem here.  do i need to do inorder to make it accessable.   im going to restart the server and check the configuration file again.

---

### Post by fatihsanli58 on 2008-04-30
hi,
here is how to install schoolTool-2008 in hardy.
1. add there line to your software resources
deb [http://ppa.launchpad.net/schooltool-owners/ubuntu](http://ppa.launchpad.net/schooltool-owners/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/schooltool-owners/ubuntu](http://ppa.launchpad.net/schooltool-owners/ubuntu) hardy main
2) Update your software list.

Either type "sudo apt-get update" in a Terminal or, if you've got the Synaptic package manager installed, go to System > Administration > Synaptic Package Manager, launch it, and click "Reload."

3) Install schooltool-2008

Either type "sudo apt-get install schooltool-2008" in a terminal (and answer "y" to the subsequent questions), or in Synaptic search for "schooltool-2008", select it for installation, and hit "Apply."

If all goes well, many, many small Zope components will be installed and you'll have a SchoolTool server running on [url]http://localhost:7080. (write[this address in your browser) 
The login is "manager" and the default password is "schooltool".

---

### Post by mikwig on 2008-05-12
Have a different newbie question... I have installed schooltool-2008 via the repository as suggested in the previous reply on our school server, and must say it is exactly what we need.

...except, I have no idea on how to make it accessible to another computer via the web. 

[http://localhost:7080](http://localhost:7080) works fine from the server, but the weblink - 
[http://mikwig.com.cc:7080](http://mikwig.com.cc:7080) does not.

Do I need to alter the configuration for apache, zope, schooltool or something else. I am at a loss. 

If you go to [http://mikwig.co.cc](http://mikwig.co.cc) you will see my apache/router config is suitable for basic stuff.

How do I make schooltool accessible over the web?

---

