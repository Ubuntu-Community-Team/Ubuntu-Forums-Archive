---
title: "Package Problems"
date: 2005-12-07
forum: General Help
---

### Post by damonkohler on 2005-12-07
This really relates to the [last thread]("http://www.ubuntuforums.org/showthread.php?t=99897") I posted, but I think I'm not getting replies because I picked a bad title for the post.

> So I installed mt-daapd and got my iTunes streaming working. The only problem is that to do it, I had to use dpkg --force-depends. Now I can't use apt-get because it's always complaining:

```

>:~/$ sudo apt-get install id3tool
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mt-daapd: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

>:~/$ sudo apt-get -s -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  mt-daapd
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
Remv mt-daapd [0.2.3-1]

```

Any suggestions?

---

### Post by endersshadow on 2005-12-07
have you tried apt-get -f install?

---

### Post by hedone on 2005-12-07
try to use Synaptic and let us know what is the result!

---

### Post by damonkohler on 2005-12-07
I included the simulated results of apt-get -f install. If I run synaptic, or do the -f install, it will remove my newly added package mt-daapd. Which, I don't want to do since it works just fine. I just need to convince apt that I don't care about the conflict so I can go on installing other things.

---

### Post by endersshadow on 2005-12-07
[QUOTE=damonkohler]I included the simulated results of apt-get -f install. If I run synaptic, or do the -f install, it will remove my newly added package mt-daapd. Which, I don't want to do since it works just fine. I just need to convince apt that I don't care about the conflict so I can go on installing other things.[/QUOTE]

Sorry, I'm an idiot...missed that.

You can try this:

```
sudo apt-get install --assume-yes --force-yes id3tool
```

Note: You wanted to bypass the dependency...the --force-yes will do that.

---

### Post by flopsy on 2005-12-07
EDIT: Ignore that, you seem to have hoary's libc6. On my breezy system,
```

gee@daisy:~$ apt-cache policy libc6
libc6:
  Installed: 2.3.5-1ubuntu12
  Candidate: 2.3.5-1ubuntu12
  Version table:
     2.3.5-1ubuntu17 0
          1 http://gb.archive.ubuntu.com dapper/main Packages
 *** 2.3.5-1ubuntu12 0
        500 cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
        500 http://archive.ubuntu.com breezy/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by damonkohler on 2005-12-07
So I need to upgrade to Breezy then?

---

### Post by damonkohler on 2005-12-08
sudo apt-get install --assume-yes --force-yes id3tool doesn't seem to do the trick.

```
damonkohler@dingo:~$ sudo apt-get install --assume-yes --force-yes id3tool
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mt-daapd: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
damonkohler@dingo:~$

```

---

### Post by flopsy on 2005-12-08
It is not necessary for you to upgrade to breezy. As I see it, you have four options:
[LIST=1]
[*]Download id3tool ( [http://packages.ubuntu.com/hoary/sound/id3tool](http://packages.ubuntu.com/hoary/sound/id3tool) ) and install with dpkg --force-depends -i blah.deb. This will solve the immediate problem.
[*]Build mt-daapd from source (removing apt out of the process). This may be the best solution for you.
[*]Rebuild the mt-daapd package for hoary. The best solution, if you know how.
[*]Use this fake libc6-breezy-equivs package I made for you. It should (hopefully) fool apt into thinking you have the requisite version of libc6 installed. Be warned though, it is an terrible thing to do, and could cause problems further down the line with packages that really do need the newer version. Get it from the link in my sig.[/LIST]

---

