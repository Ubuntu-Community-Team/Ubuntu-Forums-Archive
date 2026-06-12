---
title: "Is it possible to upgrade Feisty to something newer?"
date: 2009-05-14
forum: General Help
---

### Post by gdanko on 2009-05-14
I have an old feisty server that has served me well and now it's no longer supported. Is there a way to upgrade my feisty box without booting off the CD? A dist upgrade would be wonderful.

---

### Post by logos34 on 2009-05-14
yes, but only one release at a time (feisty-->gutsy)

---

### Post by whoop on 2009-05-14
they move all the old repositories somewhere else. So they should be still online somewhere. Then it's just a matter of updating your sources list.

Do a search on google with a query like "upgrading feisty after end of life" or something and I'm sure you will find useful stuff. Maybe:
[http://jacob.steelsmith.org/content/upgrade-ubuntu-feisty-post-end-life](http://jacob.steelsmith.org/content/upgrade-ubuntu-feisty-post-end-life)

---

### Post by logos34 on 2009-05-14
> **whoop said:**
> they move all the old repositories somewhere else. So they should be still online somewhere. Then it's just a matter of updating your sources list.


I just had a look at that page:
> 
In any case, back to Feisty. Because the repositories are moved, **the tool to upgrade the server distribution, found in the package update-manager-core, is not available. **To install the tool, edit your sources.list file:

you mean they even remove the update mngr?  I didn't know that.  hmm.  they don't make it easy do they

---

### Post by gdanko on 2009-05-14
gdanko@shops:~$  sudo apt-get update && sudo apt-get upgrade && sudo apt-get install update-manager-core
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gdanko@shops:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting '/tmp/tmpZvnNV2/gutsy.tar.gz'
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 45, in <module>
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 98, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.5/tarfile.py", line 1139, in open
    return func(name, "r", fileobj)
  File "/usr/lib/python2.5/tarfile.py", line 1200, in gzopen
    fileobj = file(name, mode + "b")
IOError: [Errno 2] No such file or directory: '/tmp/tmpZvnNV2/gutsy.tar.gz'

---

### Post by gdanko on 2009-05-14
My other server claims there is no upgrade path

gdanko@monitor:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

It is Hardy.

---

### Post by whoop on 2009-05-14
> **gdanko said:**
> My other server claims there is no upgrade path

gdanko@monitor:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

It is Hardy.
hardy searches for an LTS release by default, and no newer LTS has been released yet

---

### Post by whoop on 2009-05-14
> **gdanko said:**
> gdanko@shops:~$  sudo apt-get update && sudo apt-get upgrade && sudo apt-get install update-manager-core
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gdanko@shops:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting '/tmp/tmpZvnNV2/gutsy.tar.gz'
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 45, in <module>
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 98, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.5/tarfile.py", line 1139, in open
    return func(name, "r", fileobj)
  File "/usr/lib/python2.5/tarfile.py", line 1200, in gzopen
    fileobj = file(name, mode + "b")
IOError: [Errno 2] No such file or directory: '/tmp/tmpZvnNV2/gutsy.tar.gz'

What does your sources list look like?

---

### Post by dougfractal on 2009-05-14
I resently did a Hardy to Jaunty upgrade, It might just work for you.


Ubuntu 8.04 to 9.04 Upgrade

[https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu/8.04)
[http://www.kubuntu.org/~jriddell/9.04-upgrade/kubuntu-8.04-to-9.04-beta-upgrade](http://www.kubuntu.org/~jriddell/9.04-upgrade/kubuntu-8.04-to-9.04-beta-upgrade)

This can also work for ubuntu

```
#!/bin/bash
rm jaunty.tar.gz jaunty.tar.gz.gpg
wget [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz)
wget [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz.gpg)

gpg --keyring /etc/apt/trusted.gpg --verify jaunty.tar.gz.gpg jaunty.tar.gz
if [ $? != 0 ]; then echo "Digital signature on download did not match, quitting"; fi

tar xf jaunty.tar.gz
gksu "./dist-upgrade.py --frontend=DistUpgradeViewGtk"
```


other dist-upgrade.py --frontend=DistUpgradeViewText, DistUpgradeViewGtk,
DistUpgradeViewKDE

---

### Post by gdanko on 2009-05-15
> **whoop said:**
> What does your sources list look like?

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security universe
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by gdanko on 2009-05-15
> **dougfractal said:**
> I resently did a Hardy to Jaunty upgrade, It might just work for you.


Ubuntu 8.04 to 9.04 Upgrade

[https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu/8.04)
[http://www.kubuntu.org/~jriddell/9.04-upgrade/kubuntu-8.04-to-9.04-beta-upgrade](http://www.kubuntu.org/~jriddell/9.04-upgrade/kubuntu-8.04-to-9.04-beta-upgrade)

This can also work for ubuntu

```
#!/bin/bash
rm jaunty.tar.gz jaunty.tar.gz.gpg
wget [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz)
wget [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/dist-upgrader-all/current/jaunty.tar.gz.gpg)

gpg --keyring /etc/apt/trusted.gpg --verify jaunty.tar.gz.gpg jaunty.tar.gz
if [ $? != 0 ]; then echo "Digital signature on download did not match, quitting"; fi

tar xf jaunty.tar.gz
gksu "./dist-upgrade.py --frontend=DistUpgradeViewGtk"
```


other dist-upgrade.py --frontend=DistUpgradeViewText, DistUpgradeViewGtk,
DistUpgradeViewKDE

No GTK here. This is the server version.

---

### Post by gdanko on 2009-05-15
For my Hardy server I am good. This URL helped:
[http://www.ubuntugeek.com/upgrade-ubuntu-810-intrepid-to-ubuntu-904-jaunty-server.html](http://www.ubuntugeek.com/upgrade-ubuntu-810-intrepid-to-ubuntu-904-jaunty-server.html)

Edit /etc/update-manager/release-upgrades:
* sudo vi /etc/update-manager/release-upgrades

and set
* Prompt=normal

Now if I can get my Feisty box current I am set :)

---

### Post by whoop on 2009-05-15
> **gdanko said:**
> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security universe
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty-security multiverse
I think a do-release-upgrade won't work because feisty is EOL and it is not an LTS and gutsy is EOL too.
So two different ideas come to mind:
* Change sources to edgy making it an LTS that is EOL but might be upgradeable to hardy the current LTS.
* Change sources to gutsy, do apt-get update and dist-upgrade. Then change sources to hardy (pointing to a regular repository), do apt-get update and dist-upgrade again (making it the current LTS)

It would be cool if you could make it work...

---

### Post by gdanko on 2009-05-15
> **whoop said:**
> I think a do-release-upgrade won't work because feisty is EOL and it is not an LTS and gutsy is EOL too.
So two different ideas come to mind:
* Change sources to edgy making it an LTS that is EOL but might be upgradeable to hardy the current LTS.
* Change sources to gutsy, do apt-get update and dist-upgrade. Then change sources to hardy (pointing to a regular repository), do apt-get update and dist-upgrade again (making it the current LTS)

It would be cool if you could make it work...

Genius, man! I backed up sources.list and replaced it with Hardy's and I was able to upgrade to Hardy! Now I am upgrading to Intrepid via do-release-upgrade. I will move to Jaunty next!

---

### Post by whoop on 2009-05-15
> **gdanko said:**
> Genius, man! I backed up sources.list and replaced it with Hardy's and I was able to upgrade to Hardy! Now I am upgrading to Intrepid via do-release-upgrade. I will move to Jaunty next!
Cool! keep us up to date on your progression. Glad there is still a trick to get old installs up to date again.

P.S. So you skipped the gutsy step all together?

---

### Post by gdanko on 2009-05-15
Yeah! Gutsy failed on apt-get update. Hardy was a success! My server is now a solid Jaunty. Works like a champ.

---

### Post by gdanko on 2009-05-15
With that said, a couple of things broke during the process.

1) libcurl was gone, had to reinstall.
2) eth0:1 and eth0:2 would not come up after reboot, don't ask me why.
3) My home dir was owned by 0:0

But all in all it was successful.

---

### Post by nmsmith on 2009-05-16
Another alternative, for the record, would have been to download the Alternative Install CD for Gutsy and then use that to upgrade.

If ubuntu aren't still hosting it then it will certainly be floating around the web somewhere.

---

### Post by gdanko on 2009-05-16
Yes but my goal was to avoid driving to the data center. :) I wanted to upgrade from the comfort of my desk.

---

### Post by dougfractal on 2009-05-18
> ```
gksu "./dist-upgrade.py --frontend=DistUpgradeViewGtk"
```


other dist-upgrade.py --frontend=DistUpgradeViewText, DistUpgradeViewGtk,
DistUpgradeViewKDE

__________________________________________________

No GTK here. This is the server version.


sudo ./dist-upgrade.py --frontend=DistUpgradeViewText

---

### Post by mjmckinnon on 2009-05-21
Today, I attempted to update an old Feisty box to Gutsy, but encountered the same issue discussed here (i.e. gutsy.tar.gz was not found when doing do-release-upgrade)

This was easily fixed by editing **/var/lib/update-manager/meta-release** which incorrectly refers to [http://archive.ubuntu.com/](http://archive.ubuntu.com/) as the home server for Gutsy, but it has been moved to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

Therefore (on Feisty), edit /var/lib/update-manager/meta-relase and just replace all occurences of:

[http://archive.ubuntu.com/ubuntu/dists/gutsy/](http://archive.ubuntu.com/ubuntu/dists/gutsy/)

*with*

[http://old-releases.ubuntu.com/ubuntu/dists/gutsy/](http://old-releases.ubuntu.com/ubuntu/dists/gutsy/)

Good Luck!

---

### Post by Juparave on 2010-01-07
> **mjmckinnon said:**
> Today, I attempted to update an old Feisty box to Gutsy, but encountered the same issue discussed here (i.e. gutsy.tar.gz was not found when doing do-release-upgrade)

This was easily fixed by editing **/var/lib/update-manager/meta-release** which incorrectly refers to [http://archive.ubuntu.com/](http://archive.ubuntu.com/) as the home server for Gutsy, but it has been moved to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

Therefore (on Feisty), edit /var/lib/update-manager/meta-relase and just replace all occurences of:

[http://archive.ubuntu.com/ubuntu/dists/gutsy/](http://archive.ubuntu.com/ubuntu/dists/gutsy/)

*with*

[http://old-releases.ubuntu.com/ubuntu/dists/gutsy/](http://old-releases.ubuntu.com/ubuntu/dists/gutsy/)

Good Luck!

This did it for me, also I modified the downloaded version of  *prerequists-sources.list* (gutsy.tar.gz) to replace _archive_ to _old-release_, and then I ran 
```
# ./dist-upgrade.py --frontend=DistUpgradeViewText
```

Thanks

---

### Post by ToniMe on 2010-06-02
> **gdanko said:**
> Genius, man! I backed up sources.list and replaced it with Hardy's and I was able to upgrade to Hardy! Now I am upgrading to Intrepid via do-release-upgrade. I will move to Jaunty next!

Hi everybody on this thread!  I  would  like to ask  especially Gdanko for help as he seems to have worked this out. I 've been with ubuntu (feisty, gutsy, hardy and now lucid) for 4 years now and I have been able to handle the system only thanks to you guys and the whole community. However, I still don't know about linux things and now I have to help my daughter, who lives abroad and has feisty desktop eol. She can't update the system and I need to instruct her how to deal with the problem from distance. So, from what I understand here, she can just change the source.list with hardy's and then 

sudo apt-get update && sudo apt-get upgrade

OR 
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install update-manager-core

Which is the right thing to do? Please advise on every step that has to be done so that she can end up with hardy ubuntu desktop.

---

### Post by dino99 on 2010-06-02
as lot of hard changes in the background have happened with karmic release, the best choice is to upgrade to Jaunty, no more.

we can dist-upgrade from :
- previous to next
- LTS to LTS

---

### Post by ToniMe on 2010-06-03
I know, I've read around about the issue. Perhaps I got the wrong impression from the earlier posts on the thread that it was quite possible to do. Anyway, Ive decided not to experiment and moreover, from a distance, for the time being. No matter feisty, the machine is still a working one. And thank you for your reply.

---

