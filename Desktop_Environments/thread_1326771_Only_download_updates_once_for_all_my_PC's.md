---
title: "Only download updates once for all my PC's"
date: 2009-11-14
forum: Desktop Environments
---

### Post by toogooda on 2009-11-14
Hi All,

My family have moved completely to Ubuntu (Finally Microsoft free:p) 
We have 4 computers at home all on the same version (just upgraded to 9.10) I love the way all my apps not just OS security get updated and want to stay up to date.
The problem is we don't have a flat rate plan for internet so downloading updates on every machine from the net is costly not to mention a time waster given it has already been download once.
It would be great if I could download once then have the auto update system of the other PC's check a local repository (on one of my PC's). That way only one PC would download and all would be up to date.
I can't be the only person to think of this, in work situations where there are hundreds of ubuntu PC's I wouldn't think they would all go out to the net for updates, what do they and other multi PC households use?
I have already tried Burning APTONCD images to disk but it is out of date the same day and I couldn't automate it.

Thank you in advance for your help

---

### Post by rd1381 on 2009-11-14
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
here is your answer
though its just one way to do it and there are several other ways 
you can create a local repository on your computer and then share it with ur family.
when u install updates they get downloaded in this folder /var/cache/apt/archives
so u can keep them in another folder in ur home dir and share that with ur family so they can copy it back on their /var/cache/apt/archives so when they update the same package it doesnt doenload from internet  but from their hard disk .
and another way is like the same way before but at the end u can make a local  repository (addable in synaptic) on ur computer and ur family can add that repository to their synaptic and u just have to maintain urs and they get the update from u.i dont remember the detail but you can google for it |(it was just some terminal commands) or somebody else can tell u.

---

### Post by rd1381 on 2009-11-14
[http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/](http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/)

---

### Post by toogooda on 2009-11-15
Thanks Buddy that second link was very helpful!

I have made a repository on a potable HD that I now use on all the machines, no need to burn CD when there is updates.

For those who want to do the same this is the shell scripts I wrote:** UpdateRepository.sh**

```

# Script to update Repository
clear
# Get latest versions from internet
echo "*** Get latest versions from internet ***"
sudo apt-get update
sudo apt-get -u upgrade
# Copy files from cache to repository
echo "*** Copy files from cache to repository ***"
cp /var/cache/apt/archives/*.deb /media/TOOGOOD/Ubuntu/Repository/PackageFiles
#Change to Repository Directory
echo "*** Change to Repository Directory ***"
cd /media/TOOGOOD/Ubuntu/Repository
# Make Packages.gz file for synaptic
echo "*** Make Packages.gz file for synaptic ***"
sudo apt-get install build-essential
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
echo "*** Repository is up to date ***"

```I just plug in my HD and go to directory /media/TOOGOOD/Ubuntu/Repository then double click on UpdateRepository.sh to update the HD repository with all on the PC.[B]
Works great! :D

[/B]And update PC with second script[B] UpdateComputer.sh

[/B]```

# This script will update the computer to all the latest versions based on local repository
# Update apt
echo " *** Update apt *** "
sudo apt-get update
# Update Computer with local repository
echo " *** Update Computer with local repository ***"
sudo apt-get upgrade

```[B]

Note: Don't forget to make the scripts executable:
[/B]
Cheers,

Andrew T

---

### Post by toogooda on 2009-11-15
Sorry forgot to mention one other trick that was required. 

To make all the PC's look at the HD first before going to the internet repositories you need to edit the /etc/apt/source.list file and add the location of your new repository in the top line (Top not bottom or it will get internet versions first)

```

deb file://repository /

```the location of my repository was /media/TOOGOOD/Ubuntu/Repository

so I added 
```

deb file:///media/TOOGOOD/Ubuntu/Repository /

```Cheers,

Andrew T

---

### Post by paulisdead on 2009-11-15
I really recommend apt-cacher-ng, it basically works as a proxy for apt.  You setup one of the of the computers to be the proxy and cache all the files, and if a file's needed, it's pulled from the cache, and fetched and added to the cache if it's not found.  It's all automatic, so you don't have to move a drive around or manually sync up a repo.  The server takes a bit to setup, but the clients just need a 1 line text file created to start using it.  You just might want to expire the cache sometimes, if it gets too big.  If you're still looking for an easier way to do this, you can find plenty of howtos out there to set it up.

---

