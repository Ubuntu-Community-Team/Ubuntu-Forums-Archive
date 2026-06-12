---
title: "Restore Compiz config to the default"
date: 2011-04-15
forum: Desktop Environments
---

### Post by XMasterrrr on 2011-04-15
hello community :)

so i got a problem that making me very sad

i typed down this commands to download the compiz unsupported plugins

sudo add-apt-repository ppa:compiz/ppa
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install compiz-fusion-plugins-unsupported

but after all i got some new plugins(they are few only) and every thing is set to false

and now all my desktop is as ****!!!!!!!!!!!!! can't even do any thing 

so i need help in restoring this and please i want it in terminal only because i can't work with any GUI because of this

another question does any one know how to download and install all compiz plugins the supported and unsupported one's  with command line too :)

thank's guys

---

### Post by stinkeye on 2011-04-15
The compiz ppa used to be experimental and would break things on Maverick.
I don't know if that's still the case.
I would purge the ppa.
This will disable the Compiz PPA and downgrade all the packages you've
 installed from this PPA to the version in the official Ubuntu repositories.

```
sudo apt-get install ppa-purge
```
then
```
sudo ppa-purge ppa:compiz/ppa
```


See this page for instructions on how to download and use a script to install experimental plugins.
[**_[COLOR="DarkRed"]http://forum.compiz.org/viewtopic.php?f=114&t=12012[/COLOR]_**]("http://forum.compiz.org/viewtopic.php?f=114&t=12012")

---

### Post by JOHNNYG713 on 2011-04-15
Open System/Administration/**synaptic package manager **click "settings" tab then "Repositories", click "Other Software"  and delete the compiz ppa,  close and then reload as prompted, Then in the search box, compiz, reinstall compiz and all compiz components, via Synaptic.
 after reinstalling compiz log out and in and see if all is back to normal ! If so go here **[http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+32%2664+NEW+%21?content=118511](http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+32%2664+NEW+%21?content=118511)** and download the script I have posted for ALL of Unsupported and Experimental Plugins ! Hope this helps !

---

### Post by XMasterrrr on 2011-04-16
Thank's stinkeye and johnnyg713 you do too much for me :)

is there's any rate or thank's button to do so for you guys ?

---

### Post by JOHNNYG713 on 2011-04-16
No My friend, just get your nix runn'n and enjoy! remember to mark your thread as "SOLVED" if all is well and good ! :smile:

---

### Post by outcast247 on 2011-11-03
> **stinkeye said:**
> The compiz ppa used to be experimental and would break things on Maverick.
I don't know if that's still the case.
I would purge the ppa.
This will disable the Compiz PPA and downgrade all the packages you've
 installed from this PPA to the version in the official Ubuntu repositories.

```
sudo apt-get install ppa-purge
```
then
```
sudo ppa-purge ppa:compiz/ppa
```


See this page for instructions on how to download and use a script to install experimental plugins.
[**_[COLOR="DarkRed"]http://forum.compiz.org/viewtopic.php?f=114&t=12012[/COLOR]_**]("http://forum.compiz.org/viewtopic.php?f=114&t=12012")
Hey i am also having a kind of  same problem.when i open compiz setting i selected preferences then
tried to select plugging list..which i could not cause it was in gray color not available & suddenly whole system got stuck after reboot now i don't see launch panel, & the user,time,wifi & sound icons on title bar
is been disapeared ..i have tried the command above but did not fix...the result was like this:

( naube@Naube:~$ sudo apt-get install ppa-purge
[sudo] password for naube: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-dnspython indicator-status-provider-emesene python-xmpp
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-parser-perl libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
  libtimedate-perl ppa-purge
0 upgraded, 9 newly installed, 0 to remove and 2 not upgraded.
Need to get 2,896 kB of archives.
After this operation, 9,146 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libboost-iostreams1.46.1 i386 1.46.1-5ubuntu2 [40.2 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libcwidget3 i386 0.5.16-3.1ubuntu1 [392 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main aptitude i386 0.6.4-1ubuntu2 [2,316 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libsub-name-perl i386 0.05-1build1 [10.6 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libio-string-perl all 1.08-2 [12.0 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libtimedate-perl all 1.2000-1 [41.6 kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/universe ppa-purge all 0.2.8+bzr56 [4,360 B]
Fetched 2,896 kB in 1min 52s (25.7 kB/s)                                       
Selecting previously deselected package libboost-iostreams1.46.1.
(Reading database ... 142374 files and directories currently installed.)
Unpacking libboost-iostreams1.46.1 (from .../libboost-iostreams1.46.1_1.46.1-5ubuntu2_i386.deb) ...
Selecting previously deselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.1ubuntu1_i386.deb) ...
Selecting previously deselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package libsub-name-perl.
Unpacking libsub-name-perl (from .../libsub-name-perl_0.05-1build1_i386.deb) ...
Selecting previously deselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.34-1_all.deb) ...
Selecting previously deselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.2000-1_all.deb) ...
Selecting previously deselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb) ...
Selecting previously deselected package ppa-purge.
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr56_all.deb) ...
Processing triggers for man-db ...
Setting up libboost-iostreams1.46.1 (1.46.1-5ubuntu2) ...
Setting up libcwidget3 (0.5.16-3.1ubuntu1) ...
Setting up aptitude (0.6.4-1ubuntu2) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up libsub-name-perl (0.05-1build1) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libio-string-perl (1.08-2) ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up libparse-debianchangelog-perl (1.2.0-1ubuntu1) ...
Setting up ppa-purge (0.2.8+bzr56) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
W: Duplicate sources.list entry [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_cairo-dock-team_ppa_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
naube@Naube:~$ sudo ppa-purge ppa:compiz/ppa
Updating packages lists
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: compiz ppa
Warning:  Could not find package list for PPA: compiz ppa )
Any help..

---

### Post by stinkeye on 2011-11-03
This was a solution for 10.10 where someone had enabled the ppa for compiz.
I don't think this is your problem.
See here for re-enabling the unity plugin using ccsm (compizconfig-settings-manager)
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1873821[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1873821")

---

### Post by totfit on 2011-11-03
I hosed my desktop and was getting ready to give it up and reinstall "some" OS maybe even jump ship to Mint. Instead I just deleted everything in .compiz and everything in the compiz folder in .config. I booted to a live cd to do it as I couldn't even get to the terminal or anything in Ubuntu. I "thought" it would work and it worked like a charm. Contrary to the naysayers, I kind of like early Unity and expect things to get better and it behaves a lot better for me than Gnome 3 with some of my apps. I think I have some .java issues with Gnome 3.

---

