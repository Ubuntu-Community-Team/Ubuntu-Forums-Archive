---
title: "OpenOffice 3.1 not showing in Applications -&gt; Office"
date: 2009-06-22
forum: General Help
---

### Post by StOlEnDeStInY on 2009-06-22
I installed Open Office 3.1 by downloading the following package (I surely should have used the Synaptic but never mind :( )

OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz

I installed all the deb files using

```
sudo dpkg -i *.deb
```

Then I installed openoffice.org3.1-debian-menus_3.1-9393_all.deb which completed after I remoevd initial Open Office suite which came with my Ubuntu version..

But it doesn't seem to show up in Applications -> Office! Any ideas anyone?

---

### Post by StOlEnDeStInY on 2009-06-22
Just to add to it I had openoffice 2.4 installed by default. I uninstalled it through synaptic package manager.. I can see OpenOffice 3,1 install showing in the Synaptic as well as the menubar, with the latest version being shown as installed.. Any ideas? :)

---

### Post by DeMus on 2009-06-22
> **StOlEnDeStInY said:**
> Just to add to it I had openoffice 2.4 installed by default. I uninstalled it through synaptic package manager.. I can see OpenOffice 3,1 install showing in the Synaptic as well as the menubar, with the latest version being shown as installed.. Any ideas? :)

After using the tar instructions you see inside the folder with all the *.deb files another folder. cd to it and use the dpkg instruction again. After this the menu listings will be there.

---

### Post by Soul-Sing on 2009-06-22
for jaunty: add:
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

to your [COLOR="Red"]software sources[/COLOR]/third party software. Reload it and you got the newest openoffice on your system replacing the older on.
Also in applications: etc.
[COLOR="Red"][COLOR="Red"][COLOR="Red"][COLOR="Red"]Also the openoffice updates come/are done automat. in this way.[/COLOR][/COLOR][/COLOR][/COLOR]
Before this you have to uninstall the earlier version you installed manually, as you told.
The older version of openoffice, visual in synaptic package manager, should not be uninstalled!

: [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by SteveDee on 2009-06-22
> **StOlEnDeStInY said:**
> I installed Open Office 3.1 by downloading the following package (I surely should have used the Synaptic but never mind :( )

OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz

I installed all the deb files using

```
sudo dpkg -i *.deb
```

Then I installed openoffice.org3.1-debian-menus_3.1-9393_all.deb which completed after I remoevd initial Open Office suite which came with my Ubuntu version..

But it doesn't seem to show up in Applications -> Office! Any ideas anyone?

You just need to manually create a menu entry.

Go to System > Preferences > Main Menu
 - In the left pane select the location required for your OpenOffice apps.
 - Click the New Item button
 - In the new launcher add:-
Type: Application
Name: Word Processor
Command: ooffice -writer %U
Comment: its not great, but its free!

You should now be able to launch OpenOffice Writer.

For Calc the command is: ooffice -calc %U

---

### Post by StOlEnDeStInY on 2009-06-22
> **DeMus said:**
> After using the tar instructions you see inside the folder with all the *.deb files another folder. cd to it and use the dpkg instruction again. After this the menu listings will be there.


I've already done that. "Then I installed openoffice.org3.1-debian-menus_3.1-9393_all.deb which completed after I removed initial Open Office suite which came with my Ubuntu version.."

Leoquant -> Now that I have removed it, what should i do? I don't even know how to open Open office 3.1's word processor and other utilities through terminal and it is not showing in Applications -> Office :(

Right now I can't open office files and that is a problem.. I have added the repository you asked me to (Hardy version) but the latest open office was showing up earlier too.. Just that it never asked me to update it..

---

### Post by fooman on 2009-06-22
if you have already added the repos to your software sources and your not getting an upgrade,  try this:

open a terminal and run these 3 commands one at a time (the first command will fetch the PGP key so you don't see a warning/error when you run the update):

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 247D1CFF
``````
sudo apt-get update
``````
sudo apt-get upgrade
```if that does not do the trick,  run this one:

```
 sudo apt-get install openoffice.org
```that should fix it.  if it doesn't,  post back with any output you see in the terminal.

---

### Post by Soul-Sing on 2009-06-22
The whole process: [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

---

### Post by StOlEnDeStInY on 2009-06-23
It worked! But I still have one doubt viz this:

When I tried to install Open Office 3.1 through the debian files earlier, I had to install separately a debian file namely, openoffice.org3.1-debian-menus_3.1-9393_all.deb. When I tried to install that file it had a conflict with openoffice.org-core. So i manually removed openoffice.org-core from Synaptic.

Now when I tried to upgrade using update manager as given in the how-to, it removed open-office.org debian menus and installed back openoffice.org-core. I cannot understand why the contradiction? If debian menus are coming with the downloaded package, why aren't they finally being installed?

Also after updating through update manager and my openoffice calc, draw, base and else installed earlier through all the debian menus earlier, why do we still have to go for Add-Remove program? I've rarely ever come across an installation guide which uses add-remove program option, its almost always synaptic.. Am I missing something here?

Thank you all especially leoquant for your time :)

---

### Post by beacon on 2009-07-19
I have spent nearly two days, going over and over the steps outlined in these clear and apparently simple posts. I seem to have updated Open Office, and I am told the system is up-to-date, but I can't find the update in the applications. I still get the old version of OO's database, for example, when I have downloaded and want to use base. I see that others have had similar difficulties, but none of the solutions offered have worked for me. I'd be most grateful for any help.

---

