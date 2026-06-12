---
title: "Need help fixing sources list"
date: 2006-10-07
forum: Desktop Environments
---

### Post by IusedTObeSOMEONEelse on 2006-10-07
Hi every one!! After a serios crash  & burn last nite I had to re-install. Some thing seems to be not right. If some one could look over the following and let me know what & how to change  to get me going again. Thanks much, Sally
                     E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
:~$   sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list
Password:
~$ sudo apt-get -fix-missing
E: Command line option 'i' [from -fix-missing] is not known.               :~$ sudo /etc/apt/sources.list
sudo: /etc/apt/sources.list: command not found

---

### Post by aysiu on 2006-10-07
How about getting a fresh sources.list?

*sudo /etc/apt/sources.list* isn't a command, by the way.

Try ```
gksudo gedit /etc/apt/sources.list
``` and then highlight everything there and erase it. Then paste in this code: ```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu edgy-commercial main

#deb http://packages.freecontrib.org/plf/ edgy free non-free
#deb-src http://packages.freecontrib.org/plf/ edgy free non-free 
``` Save and exit. Then do ```
sudo aptitude update
```

---

### Post by IusedTObeSOMEONEelse on 2006-10-07
Hi Aysiu! Yes I went with re-install. Thanks I am letting it do it's thing with what you gave me. Thanks so much. So far all is going. This one error has come in there:                                                           
~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release [34.7kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [14B]
Err [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages
  404 Not Found
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages [14B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [14B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release [19.6kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources [14B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [14B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [14B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release [19.6kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [934kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [6419B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources [273kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources [1427B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [3554kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources [1071kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages [127kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources [45.0kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [14B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources [14B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources [14B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [14B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [14B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [14B]
Fetched 6087kB in 3m23s (29.8kB/s)
Reading package lists... Done
Can I go ahead and reboot or do I need to fix some thing else, again, thanks so much

---

### Post by aysiu on 2006-10-07
I just checked and there's no commercial repository for Edgy yet. So you can ```
sudo nano -B /etc/apt/sources.list
``` and then delete (Control-K) that line and then save (Control-X, Y, Enter), and the ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by IusedTObeSOMEONEelse on 2006-10-07
Ok, so I let the terminal do it's thing all afternoon. Then computer said to restart, so I did. Now I am on my other machine as when I restarted it got to the point where it said loading kernal ok. Then I got a blue screen that had a gray little window that said: Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. would you like to see the output? so I hit yes, then I end up with command line  and it asks me to log in. After log in I get -bash: no job control in this shell. Then it goes back to my screen name:"$. I am really lost now. Can some one please assist me?

---

### Post by aysiu on 2006-10-07
You do realize that Edgy is in testing, right? It hasn't been officially released. It's supposed to break.

As for the X server.... have you tried this? ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by IusedTObeSOMEONEelse on 2006-10-07
yes I do understand about the testing phase. I did try the code you provided and put password and what I got back was this: /usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed. Then it went back to screen name:"$ I am currently looking back into xserver broken  threads to get a better understanding of what I'm doing and maybe I will find some thing usefull. Thanks.

---

### Post by aysiu on 2006-10-07
Not fully installed, huh? How about this, then? ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

### Post by IusedTObeSOMEONEelse on 2006-10-07
It's going through it's thing. You do know that I am doing this in the recovery mode. I do not know if that is correct or not but it's the only thing I could get into. I guess I'll find out! Thank you "Aysiu" Now it tells me I need to manually run "dpkg --configure -a to correct the problem

---

### Post by IusedTObeSOMEONEelse on 2006-10-07
Thanks so much Aysiu!! I have it up at this time and running well. Now I just have to be carefull with what I do. It's telling there are updates, so I will let it go through that. Thank you. Sally

---

