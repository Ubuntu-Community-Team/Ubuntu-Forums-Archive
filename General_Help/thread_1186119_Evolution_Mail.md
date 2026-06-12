---
title: "Evolution Mail"
date: 2009-06-13
forum: General Help
---

### Post by chebbie on 2009-06-13
Has somebody used Evolution mail for professional means.

I set it up correctly but I'm having to set up the Signature in a professional Manner..  It's very rough.  I cannot even choose the font for the signature.  Someone knows how to work it out?

Are the signature that I set up on the Evolution will appear similarly on Microsoft Outlook.

I'm having problems to set up the ports for IMAP e-mails.

Help.

Thanks.

---

### Post by matthewjames on 2009-06-13
If you want some fonts that for sure will work with microsoft products, do the following:
```
apt-get install msttcorefonts
cd ~/.wine/drive_c/windows
mv Fonts Fonts.old
ln -s /usr/share/fonts/truetype/msttcorefonts/ Fonts
```

This will give you some of the most default microsoft fonts. As far as your IMAP ports just check your email provider or workplace and they should give you all of the info you need.

---

### Post by chebbie on 2009-06-13
help:


chouaibe@chouaibe-desktop:~$ apt-get-install msttcorefonts
bash: apt-get-install: command not found
chouaibe@chouaibe-desktop:~$ cd ~/.wine/drive_c/windows
bash: cd: /home/chouaibe/.wine/drive_c/windows: No such file or directory
chouaibe@chouaibe-desktop:~$ mc Fonts Gonts.old
The program 'mc' is currently not installed.  You can install it by typing:
sudo apt-get install mc
bash: mc: command not found
chouaibe@chouaibe-desktop:~$ sudo apt-get install mc
[sudo] password for chouaibe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqca2 libqt4-core libvncserver0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  arj xpdf dbview
The following NEW packages will be installed:
  mc
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2178kB of archives.
After this operation, 6492kB of additional disk space will be used.
Get:1 [http://mu.archive.ubuntu.com](http://mu.archive.ubuntu.com) jaunty/universe mc 2:4.6.2~git20080311-4ubuntu1 [2178kB]
Fetched 2178kB in 36s (59.1kB/s)                                                           s
Selecting previously deselected package mc.
(Reading database ... 141037 files and directories currently installed.)
Unpacking mc (from .../mc_2%3a4.6.2~git20080311-4ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mc (2:4.6.2~git20080311-4ubuntu1) ...

chouaibe@chouaibe-desktop:~$ ln -s /usr/share/fonts/truetype/msttcorefonts/ Fonts
chouaibe@chouaibe-desktop:~$ apt-get install msttcorfonts
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
chouaibe@chouaibe-desktop:~$ 



I have the IMAP ports but I do't know how to set it up on Evolution.  Or rather the option is not given to me to set it up accordingly.

---

### Post by matthewjames on 2009-06-13
run each command seperately, not copy and paste the whole thing.

and its not apt-get-install, its apt-get install

Before doing all of this, you need to type sudo -s and enter your admin password. Then you can do this, anymore questions just ask.

---

