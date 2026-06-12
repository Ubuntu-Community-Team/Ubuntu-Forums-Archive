---
title: "I deleted libqt3c102-mt and now I have problems; Help!"
date: 2005-10-24
forum: Desktop Environments
---

### Post by bdmp on 2005-10-24
Help! I tried to install skype and it was asking for a dependency,  libqt3c102-mt, but in synaptic it was already installed so I thought it was broken, so I deleted it. 

Then I realized that it was deleting all of KDE so I shut the computer down and after a restart in command line did apt-get install kde. At first I thought everything after I restarted the comp again, but then I realized that koquor is gone and my trash icon. So then in synaptic I tried to install all the kde stuff I could, but it didn't do anything. It said I was gonna download hundreds of megabytes and then it flashed "finished" in a couple seconds. 

So after that I tried to install gnome to work these problems out through with apt-get install ubuntu-desktop, but that didn't work too.

 With both the KDE and gnome installs I got marillat repo errors, but I am not sure if that is causing some of my problems.  Any suggestions?

---

### Post by beefsprocket on 2005-10-24
What packages do you have listed in /var/cache/apt/archives ?

Perhaps logging in in recovery more and running dpkg -i *kde*.deb in that directory might help out. For that matter, why not try dpkg -i *.deb?

You might have to fix any problems or inconsitencies when trying this out. Just follow whatever instructions are given.

---

### Post by shinygerbil on 2005-10-24
As far as I know, the marillat repositories are Debian-based, but not Ubuntu-compatible, apart from a few specific programs. If you don't need anything else from them, it's probably wise to delete them. I shouldn't think they are causing your problems, though.

---

