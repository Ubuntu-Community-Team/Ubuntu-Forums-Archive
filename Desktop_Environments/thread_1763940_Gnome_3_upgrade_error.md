---
title: "Gnome 3 upgrade error"
date: 2011-05-21
forum: Desktop Environments
---

### Post by dane1986 on 2011-05-21
Hi I have been using Ubuntu for a few years now and have recently upgraded to to the lastest version 11.04. When I first upgraded I did not like Unity at all, and upgraded to gnome 3 without an issue. 

I then made a the silly mistake of fiddling with Synaptic package manager and destroyed my installation. I am now trying to make a fresh install of Ubuntu 11.04 and gnome 3, however I am having no luck.

I use the following commands to add the repository and upgrade to gnome 3:

$ sudo add-apt-repository ppa:gnome3-team/gnome3

$ sudo apt-get update

$ sudo apt-get dist-upgrade

$ sudo apt-get -f install  (to rectify error)

$ sudo apt-get install gnome-shell

$ sudo apt-get install gnome-tweak-tool

I have tried 4 times now, trying different methods, installing all updates before installing gnome 3 and without installing any upgrades.

After the gnome 3 upgrade I reboot and it boots back into a desktop environment which looks like a hybrid of Unity and Gnome 3, there is no option to boot into gnome-shell at the login screen.

I then open the update manager and it prompts a partial upgrade. An error occurs in the upgrade with the gnome-control-center. After the upgrade I go to Synaptic package manager and the package appears to be fine, but I reinstall it anyway.

On reboot, at the login screen, the only option is 'other'. I tried to enter my user name and password and the window fades out and it doesn't log in, I can't access recovery terminal or anything, I can only shutdown or restart.

Does anyone have an idea of what this problem may be? As I said I have tried 4 times now and am out of ideas. Thanks Dane.

---

### Post by mörgæs on 2011-05-21
Hi, welcome to the fora.

Let's begin with getting the machine to work in a default 11.04. If you do a fresh install of 11.04 without adding anything (only regular updates, no dist-upgrade and certainly no partial upgrades), how does the machine behave?

---

### Post by dane1986 on 2011-05-22
With standard natty with unity installed the system runs perfectly. All updates install fine with no errors. Dane

---

### Post by mörgæs on 2011-05-22
So far, so good... Several  driver problems have been reported for 11.04, but you seem to be lucky here.

There is quite a lot of advice for Gnome 3. You could try these:
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)
[http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

I have not tried them myself, though.

---

### Post by kaginken on 2011-05-22
Personally, I dislike unity so much, and from what I've read on trying to run gnome on the latest version, well...let's just say I'm installing 10.04 LTS on my laptop as I type this.  Once they've got a solid stable gnome again, I'll upgrade.  Till then, well, that's why they make the 'LTS' versions!

---

### Post by dane1986 on 2011-05-23
Thankyou for the advice, however I have tried the commands from those post and still have the same problem. My hardware always had a problem with 10.04 and would freeze constantly and this has been fixed in 11.04, so I may have to stay with unity. Thanks for your help, Dane.

---

### Post by mörgæs on 2011-05-23
If you don't like Unity, booting into 'classic Gnome' from the login screen might ease your pain :-)

---

