---
title: "rpms?"
date: 2005-08-18
forum: Desktop Environments
---

### Post by tmasboa on 2005-08-18
how do i install rpms? 
is there a console program that will install them?
Right now, it just tries to extract them.

In Fedora and RH9, it pulled up a program that installed it for you.

Thanks

---

### Post by JonahRowley on 2005-08-18
You can install RPM's with the **alien** command, which will convert them to debs.  Generally, you don't install RPM's on Ubuntu unless you need to.  Fortuntately, there is plenty of stuff in the Ubuntu apt repository, but if you still need to install an RPM, use alien.

---

### Post by tmasboa on 2005-08-18
thanks, but how do you install debs? :)

---

### Post by jesse on 2005-08-18
Ubuntu is not rpm based like Red Hat and Mandriva, but is Debian based. Ubuntu, like Debian, uses deb packages rather than rpms. Sometimes you can install rpms after turning them into debs using the program alien, but this doesn't always work. 

To install alien, open a terminal and type the following. 

sudo apt-get update
sudo apt-get install alien

(It may already be installed.) 

To turn an rpm into a deb package, go to the directory where you saved the rpm. 
For example, if Madonna saved it on her desktop, she would open a terminal and type 

cd /home/madonna/Desktop

Once there, you can turn the rpm into a deb by using alien. 
Here's the command: 

sudo alien -d completefilename.rpm

This will generate a deb package. Install it with the following command. 

sudo dpkg -i completefilename.deb

Keep in mind that installing the deb you created might work and might not. 
Chances are you can probably find the programs you need by using synaptic package manager in the Systems/Administration menu on your Gnome panel, so you usually won't need to download rpms from the internet and convert them to debs using alien.

---

### Post by jesse on 2005-08-18
Oops. I didn't realize someone had already responded.

---

