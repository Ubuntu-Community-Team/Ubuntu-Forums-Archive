---
title: "Update fails: files not found??"
date: 2006-09-01
forum: Desktop Environments
---

### Post by johann_p on 2006-09-01
I am running Ubuntu Dapper. My update manager shows that there are updates available (dia-common, ktorrent, libtheora) but when I click to install the updates the update fails with the following messages:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/d/dia/dia-gnome_0.95.0-4ubuntu1~dapper1_i386.deb]("http://au.archive.ubuntu.com/ubuntu/pool/main/d/dia/dia-gnome_0.95.0-4ubuntu1%7Edapper1_i386.deb")
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/d/dia/dia-libs_0.95.0-4ubuntu1~dapper1_i386.deb]("http://au.archive.ubuntu.com/ubuntu/pool/main/d/dia/dia-libs_0.95.0-4ubuntu1%7Edapper1_i386.deb")
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/d/dia/dia-common_0.95.0-4ubuntu1~dapper1_all.deb]("http://au.archive.ubuntu.com/ubuntu/pool/main/d/dia/dia-common_0.95.0-4ubuntu1%7Edapper1_all.deb")
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/k/ktorrent/ktorrent_2.0.1-0ubuntu1~dapper1_i386.deb]("http://au.archive.ubuntu.com/ubuntu/pool/main/k/ktorrent/ktorrent_2.0.1-0ubuntu1%7Edapper1_i386.deb")
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora-dev_0.0.0.alpha7-1ubuntu1~dapper1_i386.deb]("http://au.archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora-dev_0.0.0.alpha7-1ubuntu1%7Edapper1_i386.deb")
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora0_0.0.0.alpha7-1ubuntu1~dapper1_i386.deb]("http://au.archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora0_0.0.0.alpha7-1ubuntu1%7Edapper1_i386.deb")
  404 Not Found

How can the update manager find updates that are then not available? This is odd.

---

### Post by ng0g on 2006-09-01
I just installed yesterday and I am getting a similar message when I try to update. I get:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb)
  Connection failed [IP: 146.137.96.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060725_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060725_all.deb)
  Connection failed [IP: 146.137.96.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_6.06+20060725_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_6.06+20060725_all.deb)
  Connection failed [IP: 146.137.96.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.06+20060725_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.06+20060725_all.deb)
  Connection failed [IP: 146.137.96.15 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_6.06+20060725_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_6.06+20060725_all.deb)
  Connection failed [IP: 146.137.96.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.4.8-3ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.4.8-3ubuntu1.1_i386.deb)
  Connection failed [IP: 146.137.96.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_0.120_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_0.120_i386.deb)
  Connection failed [IP: 146.137.96.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-standard_0.120_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-standard_0.120_i386.deb)
  Connection failed [IP: 146.137.96.15 80]
...etc....etc:confused: 

Yet I can to the site with my Firefox with no problems and I can ping the site with no problems.  I am not using proxy.  I have a cable modem with a very fast connection.  All previous versions of Ubuntu have updated with no problems.:confused:

---

### Post by randell6564 on 2006-09-01
At the terminal type:

[B]sudo gedit /etc/apt/sources.list
[/B]
Enter your password and then post the results

.

---

### Post by taurus on 2006-09-01
Edit your /etc/apt/sources.list and remove the "us" from the repos...  Then update and upgrade it again!

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by randell6564 on 2006-09-01
> **taurus said:**
> Edit your /etc/apt/sources.list and remove the "us" from the repos...  Then update and upgrade it again!

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

Why remove the "us"?  is there a problem with it?

---

### Post by taurus on 2006-09-01
I have noticed that site goes down more times than you want to count!!!  I think it went down last week or two weeks ago and everybody got all excited here because they couldn't upgrade their machine...  I just removed the "us" in my repos and everything is working without any problem since.  You can leave it in if you want.

---

### Post by randell6564 on 2006-09-01
> **taurus said:**
> I have noticed that site goes down more times than you want to count!!!  I think it went down last week or two weeks ago and everybody got all excited here because they couldn't upgrade their machine...  I just removed the "us" in my repos and everything is working without any problem since.  You can leave it in if you want.

Strange. all my repos are "US" and I am not having any problems.

---

### Post by fragos on 2006-09-01
I've seen something similar when the repositories hadn't caught up in terms of dependencies.  In that situation the problem was cleared up in a day or two.

---

### Post by randell6564 on 2006-09-01
Here is my /etc/apt/sources.list in case the OP wants to copy and paste it.


[B]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[/B]

---

### Post by johann_p on 2006-09-02
> **randell6564 said:**
> At the terminal type:

[B]sudo gedit /etc/apt/sources.list
[/B]
Enter your password and then post the results

.

Here is the result of grep -v '^#' /etc/apt/sources.list :

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://www.sgtpepper.net/hyspro/deb](http://www.sgtpepper.net/hyspro/deb) unstable/

I am in Europe/Austria, beats me how au.* (I assume that means Australia, across the world) could get in here.

But that is probably a different issue.

---

### Post by ng0g on 2006-09-02
I did the following after removing the "us".  I still have a problem.  I cannot understand the "connection failed" as I can get to that site with my web browser with no problem.

----------------
steve@Amy:~$ sudo gedit /etc/apt/sources.list
Password:
steve@Amy:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 146.137.96.7 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Reading package lists... Done
steve@Amy:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
---------------------
](*,) ](*,) ](*,)

---

### Post by johann_p on 2006-09-02
In my opinion this is not supposed to happen and must be a bug. I have filed [https://launchpad.net/distros/ubuntu/+bug/58560](https://launchpad.net/distros/ubuntu/+bug/58560) 

ng0g: This looks like a similar, but *different* problem -- obviously it is a bug to not show any details about why the connection failed, which makes it hard to figure out what is going on. But this is different from going to a repository host and not finding a package file that should be there.

---

### Post by markfid on 2006-09-02
I seem to be having the same problem :(

Just did what you guys said here, removed the au. from the archive location like this:

(The first line is the old one and has been commented out with the "#")

```

#deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

```

I did this for all the lines that started with "au." and now all is working great =D> 

Thanks a lot,

Mark.

---

### Post by ng0g on 2006-09-02
I see that this is not the same problem.  It is making me nuts.  I have worked on this until I drempt about it last night.  I can ping that site, and I can get to it with my web browser.  But I cannot do an update. I have been using Ubuntu on this computer through several versions and I have never had a single problem until now.  My head is beginning to hurt from beating it against the wall.  I am surprised that noone else has reported the problem besides me.  Should I open a new thread on this??  Feel free to contact me off line if you want.](*,)

---

### Post by johann_p on 2006-09-02
WHat happens if you try to download the actual package files, e.g. [http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb)

Just paste this URL into your browser and save the file somewhere or run the command "wget http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb"

If this works and at the same time you still get a connection  problem in the update manager, something is seriously flawed there.

If you manage to download the .deb files you should then be able to manually install them using the dpkg command.

In my case, unfortunately, there is definitely nothing to download, since the .deb file cannot be found on the repository server :(

---

### Post by johann_p on 2006-09-02
OK - an update on this problem: for some reason, the update manager wants to fetch a file that has "~dapper1" in the filename. The repository contains a (recent) file with the same name, but without that strange "~dapper1" in the name. Somebody seems to have got the information wrong in wherever Dapper gets to know about new updates (from where does the system get this information and who is responsible for updating it?).

---

### Post by randell6564 on 2006-09-02
> **johann_p said:**
> Here is the result of grep -v '^#' /etc/apt/sources.list :

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://www.sgtpepper.net/hyspro/deb](http://www.sgtpepper.net/hyspro/deb) unstable/

I am in Europe/Austria, beats me how au.* (I assume that means Australia, across the world) could get in here.

But that is probably a different issue.

Wel, Im not a real pro, but it looks to me like you are missing some repo's.  If you look at my list and compare, you will see them. You can use my list.  and then just add your budgetdedicated and sgtpepper to it.
I have no problems with updating at all.

---

### Post by johann_p on 2006-09-02
> **randell6564 said:**
> Wel, Im not a real pro, but it looks to me like you are missing some repo's.  If you look at my list and compare, you will see them. You can use my list.  and then just add your budgetdedicated and sgtpepper to it.
I have no problems with updating at all.

I cannot see any repos that are missing -- which do you mean? Source code repos are definitely not necessary. 
That you have no problems is most likely due to the fact that you do not have those packages installed where the update poses a problem (do you have ktorrent or dia installed?).

In the meantime, the problem seems to have been acknowledged as a problem that needs to be fixed ([https://launchpad.net/distros/ubuntu/+bug/58560](https://launchpad.net/distros/ubuntu/+bug/58560)) 

It seems somebody has messed up and used the wrong file names at some place.

I still have no idea how the mirrors get picked though -- I certainly never asked Ubuntu to use an Australian mirror!

---

### Post by ng0g on 2006-09-02
> **johann_p said:**
> WHat happens if you try to download the actual package files, e.g. [http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb)

Just paste this URL into your browser and save the file somewhere or run the command "wget http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb"

If this works and at the same time you still get a connection  problem in the update manager, something is seriously flawed there.

If you manage to download the .deb files you should then be able to manually install them using the dpkg command.

In my case, unfortunately, there is definitely nothing to download, since the .deb file cannot be found on the repository server :(

Pasting this into my browser allows me to download and save the file to my disk.

---

### Post by randell6564 on 2006-09-02
> **johann_p said:**
> I cannot see any repos that are missing -- which do you mean? Source code repos are definitely not necessary. 
That you have no problems is most likely due to the fact that you do not have those packages installed where the update poses a problem (do you have ktorrent or dia installed?).

In the meantime, the problem seems to have been acknowledged as a problem that needs to be fixed ([https://launchpad.net/distros/ubuntu/+bug/58560](https://launchpad.net/distros/ubuntu/+bug/58560)) 

It seems somebody has messed up and used the wrong file names at some place.

I still have no idea how the mirrors get picked though -- I certainly never asked Ubuntu to use an Australian mirror!

Yes, I do have dia.  It seems that you have figured it out.  Thats good! I just hope that someone fixes the problem soon for your sake.

---

### Post by phl73 on 2006-09-06
I've just recently installed Edubuntu and am having the exact same problem.  Unfortunately, removing the "us." from the URIs did not work for me.  Any way to tell when this problem will get fixed?

---

