---
title: "Neverwinter Nights Platinum Install Instructions: CD Version"
date: 2009-05-10
forum: Gaming &amp; Leisure
---

### Post by cprofitt on 2009-05-10
After attempting to piece together instructions for various resources I have found an install process that worked for my version. These instructions were made for folks with the CD version of the Platinum Neverwinter Nights game.

```

** 64 Bit Install Preparation Step:
sudo aptitude install ia32-libs


Step One:
mkdir ~/.Games
mkdir ~/.Games/nwn
cd ~/.Games/nwn

** You will unzip all the files to this directory.

Step Two:
Insert Disk Two:
Unzip "disk2.zip"

Step Three:
Insert Disk Three:
Unzip "disk3.zip"
Unzip "language_data.zip"

Step Four:
Insert Disk Four:
Unzip "disk4.zip"
Unzip "xp1.zip"
Unzip "xp1_data.zip"

Step 5:
Insert Disk One:
Unzip "Data_Shared.zip"
Unzip "Language_data.zip"
Unzip "Language_update.zip"

** the above "Language_data.zip" is ddifferent from the one on Disk Three and both are needed

Step 6:
Insert Disk Three(again):
Unzip "Data_Linux.zip"

Step 7:
cd ~/Desktop
wget http://files.bioware.com/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz
tar zxfv ~/Desktop/English_linuxclient169_xp2.tar.gz -C ~/.Games/nwn

Step 8:
cd ~/.Games/nwn
./fixinstall

Step 9:
Insert Disk One(again):
Open a terminal and Run:
./nwn

```

I hope this helps anyone who was finding Diamond or Platinum DVD instructions.

---

### Post by Manigoldo on 2009-05-12
You are my savior! Thanks a bunch for this gonna try it out later on tonight

---

### Post by Cuthbeorht on 2009-05-31
I as well have been having problems installing this game.  I'm trying these instructions as we speak.  I hope it works!!

---

