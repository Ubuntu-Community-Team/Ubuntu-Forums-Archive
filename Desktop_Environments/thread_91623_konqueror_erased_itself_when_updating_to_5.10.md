---
title: "konqueror erased itself when updating to 5.10"
date: 2005-11-17
forum: Desktop Environments
---

### Post by danv892 on 2005-11-17
G'day all

I have just upgraded from 5.04 to 5.10 and the upgrade went rather smoothly but konqueror disapeared completely. I have tried to re intall it by using synapatic pkg manager but all I get is this. konqueror:
 Depends: kdebase-kio-plugins but it is not going to be installed

Any "easy" ideas how to get around this ? I am pretty new to linux and I have totally thrown out windows XP I got fed up with the problems and spyware.

Cheers all

DJ.:)

---

### Post by HermanAB on 2005-11-17
Hmmm, you need to fix the dependencies first, so you are on the right track.

---

### Post by Limulus on 2005-11-17
Ubuntu's system for installing programs is different from (but IMHO significantly better than) Windows', so it take s a little time to learn.  There are two parts to the system; first are the repositories.  They're software libraries, the addresses of which are stored in a special file on your system.  The second part is Synaptic (or "Add Applications" or apt in terminal) which downloads and installs software from the libraries.  Your message is due to one of two things: either you are missing a repository or two in your list, or there is a software conflict preventing the installation of kdebase-kio-plugins.  Here is how I would go about solving the problem:

First, as per my site [http://members.shaw.ca/Limulus/ubuntu.html](http://members.shaw.ca/Limulus/ubuntu.html) go to Terminal (either under Applications -> System Tools or Applications -> Accessories  I forget which since I rearranged them in my system a while back ^_-) and type:

sudo gedit /etc/apt/sources.list

After entering your password, that will open the text editor with the list of repositories.  When you upgraded, if the entries didn't get changed, that could be why you're having this problem.  If you see the word "hoary" anywhere in it, it needs to be changed to "breezy".  You should at least have these three entries:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security main universe multiverse restricted

or slight variations on them.  You can see my site for more; I would also add:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main universe multiverse restricted

but you don't have to.  When you're done, if you've made changes, save and exit.  Then go back to Synaptic (System -> Administraton -> Synaptic Package Manager) and press the Reload button (you may notice errors before the reload, but ignore them).

Now, to test to see if its working, scroll down to find or search for kdebase-kio-plugins and right-click it and select "mark for installation".  If it doesn't complain, great.  Also mark konqueror for installation, press apply and install them :)  If it works, let us know...

If it still complains when trying to install kdebase-kio-plugins, copy the error message and paste it into a reply.

---

### Post by danv892 on 2005-11-17
Thanxs guys!
Got it working yay! 

:)

---

