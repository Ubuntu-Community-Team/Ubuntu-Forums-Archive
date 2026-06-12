---
title: "Ubuntu 12.04 - unmet dependencies while trying to install xserver-xorg"
date: 2017-11-29
forum: Desktop Environments
---

### Post by czezz on 2017-11-29
Ubuntu 12.04.5 LTS

I want to install X-window / GUI to my Ubuntu 12.04  server.
However that fails because of unmet dependencies.
I cant figure out how can I fix/workaround this problem. Maybe someone of you have found a way?
```


# apt-get install xserver-xorg
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg : Depends: xserver-xorg-core (>= 2:1.11)
                Depends: xserver-xorg-video-all (>= 0~) or
                         xorg-driver-video
                Depends: xserver-xorg-input-all (>= 0~) or
                         xorg-driver-input
                Depends: xserver-xorg-input-evdev (>= 0~)
                Depends: x11-xkb-utils but it is not installable
                Recommends: libgl1-mesa-dri
E: Unable to correct problems, you have held broken packages.

```

---

### Post by ajgreeny on 2017-11-29
Ubuntu-12.04 is no longer supported so you will need to upgrade, or better, clean install a supported version after backing up all your personal files in your home.

There is no point trying to add an X server to your current system as the repos have been moved to an EOL address and no packages will receive any further upgrades and will therefore be a security risk.

---

### Post by czezz on 2017-11-29
Hi, thanks for reply.
I do understand that 12.04 is out of support.
In my case this is no critical/productive machine. It is a test system and for the moment it needs to stay on 12.04 level.
What I want to do is to install minimal X-Window so I can run web browse on it.

Maybe there is a way to install it manually (.deb) ?

---

### Post by westie457 on 2017-11-29
Welcome to the Forums.

Looking at this page [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)
It is time to back up your files and clean install 14.04 or for preference 16.04 then we can try to add the GUI.

---

### Post by howefield on 2017-11-29
> **ajgreeny said:**
> Ubuntu-12.04 is no longer supported so you will need to upgrade, or better, clean install a supported version after backing up all your personal files in your home.

There is no point trying to add an X server to your current system as the repos have been moved to an EOL address and no packages will receive any further upgrades and will therefore be a security risk.

Slightly off topic, 12.04 hasn't been moved to an end of life address and is still supported for those who wish to pay for Extended Security Maintenance.

---

### Post by ajgreeny on 2017-11-29
Thanks for that info howefield; I was not aware of that and did not even look to see if I was correct as we are now 5 years and 7 months past release and simply assumed Precise was now gone.

---

### Post by czezz on 2017-11-29
Hi, thanks for replies.
I do understand that 12.04 is end of life.
My question is: is there any archival repo that I can connect to and add X-window to my archaic system?
Or maybe there is some guide to manually install X-window (.deb) ?

---

### Post by ajgreeny on 2017-11-29
In spite of my comment in post #2, and my recommendation that you should update to a fully supported version as soon as possible, can I check that before trying to install **xserver-xorg** you ran the ```
sudo apt-get update
``` command to refresh all the repos, and what output was there from that command?

If you could not access the repos for Precise had they already been moved, the output would have shown many errors.

---

### Post by czezz on 2017-11-29
Here is an output.
Like I said the upgrade is not an option for this machine. It will be decommission but before I need to install X-Window and run (any) web browser. That-s all i want to do. 


```


$ sudo apt-get update
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Hit http://security.ubuntu.com precise-security Release
Hit http://us.archive.ubuntu.com precise Release
Hit http://us.archive.ubuntu.com precise-updates Release
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://us.archive.ubuntu.com precise-backports Release
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Get:1 http://us.archive.ubuntu.com precise/main Sources [934 kB]
Get:2 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:3 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]
Get:4 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]
Hit http://security.ubuntu.com precise-security/universe Translation-en
Get:5 http://us.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get:6 http://us.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:7 http://us.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]
Get:8 http://us.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]
Get:9 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]
Get:10 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]
Get:11 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]
Get:12 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/main Sources
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/universe Sources
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 12 B in 10s (1 B/s)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  landscape-common
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by mörgæs on 2017-11-29
> **czezz said:**
> It will be decommissioned...

There is no need to let go of the hardware. If it runs a 12.04 server it will also run 16.04. 

Only the software needs to leave.

---

### Post by czezz on 2017-11-29
mörgæs - thank you for this priceless advice but its completely offtopic.

Here is my workaround:
Luckily the server has installed: xauth. That is enough to do X11 forwarding through ssh.
I get what I wanted this way :)

---

