---
title: "Trouble installing KDE4"
date: 2007-12-14
forum: Desktop Environments
---

### Post by Rainmaker52 on 2007-12-14
Hi all,

I hate it for my first post to be a cry for help, but I need some help :)

I'm trying to install kde4 on my xubuntu hardy install. I installed kubuntu-desktop, and tried the instructions [here](http://kubuntu.org/announcements/kde4-rc2.php)

However, I keep bumping into the following error:

```
root@ubuntu:~# apt-get install kdebase-workspace kdebase-kde4 kdebase-runtime
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase-kde4: Depends: dolphin-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: kappfinder-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: kdebase-bin-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: kdebase-kio-plugins-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: kdepasswd-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: kfind-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: knetattach-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: konqueror-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: konqueror-nsplugins-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: konsole-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: kwrite-kde4 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
                Depends: libkonq5 (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
  kdebase-runtime: Depends: kdebase-runtime-bin (>= 4:3.97.0-1ubuntu4) but it is not going to be installed
  kdebase-workspace: Depends: kdebase-workspace-bin (>= 4:3.97.0-1ubuntu5) but it is not going to be installed
                     Depends: klipper-kde4 (>= 4:3.97.0-1ubuntu5) but it is not going to be installed
                     Depends: ksysguard-kde4 (>= 4:3.97.0-1ubuntu5) but it is not going to be installed
                     Depends: kwin-kde4 (>= 4:3.97.0-1ubuntu5) but it is not going to be installed
                     Depends: systemsettings-kde4 (>= 4:3.97.0-1ubuntu5) but it is not going to be installed
E: Broken packages
```

I've tried using the search and Google, but can't find anything related to this error. I also tried to install it while using --ignore-authentication, because I thought it was due to the "unauthenticated" packages... But no joy.

I don't really know enough about apt to solve errors in the dep tree.

Can anyone tell me why this is error keeps coming up?

---

### Post by JACooks on 2007-12-14
I just tried following the steps provided on the link, and I didn't get the same error.  Did you follow the first couple of steps (removing previous packages, adding the PPA to your sources.list, and installing kdebase-bin)?  Mine didn't have any packages to remove, but after installing the PPA and installing kdebase-bin, it installed everything it needed when I ran the command you indicated below.

---

### Post by Rainmaker52 on 2007-12-14
That's the strange thing: I followed the steps to the letter.

I didn't even have KDE installed before this. Only reason I told apt-get to install "kunbuntu-desktop" was because I thought it might have been caused by some missing libs.

I removed the "old" packages manually, but still get the same error.

And I did add the PPA URL to sources.list, otherwise apt wouldn't even know there was a package named "kde4-accessibility" etc.

---

### Post by Triptol on 2007-12-15
Having similar problems. 

Question to you: you did change the ppa line from gutsy to hardy?

---

### Post by Rainmaker52 on 2007-12-15
I've tried both :)

I've tried adding "main experimental" etc after the PPA source line, also tried it with gutsy on my hardy install.

And ofcourse I ran apt-get update after every change #-o

---

### Post by georgie on 2007-12-16
Hi

I also followed the instructions and ran into the same error.

This worked for me

sudo dpkg --remove --force-all  kdelibs5 kde4base-data kde4libs-data kde4multimedia-data kdebase-runtime-data kde4base kdebase-runtime-data kde-icons-oxygen
sudo apt-get install -f

cd /var/cache/apt/archives

sudo dpkg -i --force-all *3.97*ubuntu4*
sudo apt-get install -f

HTH

Georgie

---

### Post by Rainmaker52 on 2007-12-17
Thank you for the tip.

Didn't have to try it out though, because after an apt-get update, it worked! :)

There is still a small dep problem somwhere, because "apt-get install kde4" results in a dep error on kdeamusements, but this is good enough for me :)

---

### Post by Marinus777 on 2008-01-11
Hi georgie,

that worked for me on Debian Etch as well, thanks!

Marinus.

---

### Post by jacksaff on 2008-01-11
Looking at the first post, you still have lots of RC2 packages in there.
Many are still in the backports repo though should be gone very soon.
Open a package manager and remove everything kde4 that has a version number lower than 4.0.0.
Then you should be able to install everything with no hassles.
Don't install any 3.97 packages (you may not be able to anyway).

---

