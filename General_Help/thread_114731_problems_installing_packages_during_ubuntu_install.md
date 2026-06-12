---
title: "problems installing packages during ubuntu installation"
date: 2006-01-09
forum: General Help
---

### Post by holr on 2006-01-09
hi,
i have tried both kubuntu and ubuntu breezy and get his message after the system restards and installs a couple more packages:

"ata1: BUG: timeout without command" this occurs when the progress bar is at 5%. How can i get ubuntu installed? What am i doing wrong?

---

### Post by BathroomNinja on 2006-01-09
OK.  Boot up to the Live CD.  Then go to Administrator > Gparted.
Manually format your drive into 3, EXT3 partitions.  Make 1 partition about 10 gigs, make another about 2 gigs, use up the rest of the drive for the third.  This is not a great way to install Ubuntu.  I'm just testing out a theory here that Ubuntu is having problems trying to format your hard drive during installation.  

Then, reboot with the Install CD.  Try installing now

---

### Post by renzokuken on 2006-01-09
i had a very similar problem but it froze at 25%

the solution i used was to install the server base by typing "server" at the initial installation screen. once installed, at the sonsole screen (cos thats all u get anyway, simply type

# sudo apt-get update
# sudo apt-get install ubuntu-desktop gdm

this of course assumes u have a working internet connection, i.e. an ethernet based lan connection

---

### Post by holr on 2006-01-10
[QUOTE=renzokuken]i had a very similar problem but it froze at 25%

the solution i used was to install the server base by typing "server" at the initial installation screen. once installed, at the sonsole screen (cos thats all u get anyway, simply type

# sudo apt-get update
# sudo apt-get install ubuntu-desktop gdm

this of course assumes u have a working internet connection, i.e. an ethernet based lan connection[/QUOTE]

I tried this, everything was going smoothly, till it was setting up the base system. Then the same "ata1: BUG: timeout without command" error! 

I tried installing mandriva a while back and it told me the exact name of my sata controller (before itself crashing also). Do you know if this SATA controller is supported by ubuntu / linux in general?

It is a "intel 82801FBM ICH6M SATA" at least, that was what mandriva was saying. Weird, as various linux distros Ive tried all recognise I havea drive, just will not install. Tried kubuntu, ubuntu, suse 10, suse 9.3, mandriva, the only one that worked was fedora core 4, but I prefer ubuntu.

---

### Post by holr on 2006-01-10
[QUOTE=BathroomNinja]OK.  Boot up to the Live CD.  Then go to Administrator > Gparted.
Manually format your drive into 3, EXT3 partitions.  Make 1 partition about 10 gigs, make another about 2 gigs, use up the rest of the drive for the third.  This is not a great way to install Ubuntu.  I'm just testing out a theory here that Ubuntu is having problems trying to format your hard drive during installation.  

Then, reboot with the Install CD.  Try installing now[/QUOTE]

hi again! I tried this, it seemed to format the partitions ok. It installed the system again, but still failed with the ata1: bug: timeout without command. darn! Any other suggestions? I remember reading that you could put the hacked mac osx onto an ibm-compatible by first booting with a live ubuntu cd then copying the image across or something. Could I do this for ubuntu, to force the bugger onto my system?

---

