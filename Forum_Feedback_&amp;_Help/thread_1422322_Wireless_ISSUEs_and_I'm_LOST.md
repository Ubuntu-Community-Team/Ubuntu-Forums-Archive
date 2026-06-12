---
title: "Wireless ISSUEs and I'm LOST"
date: 2010-03-05
forum: Forum Feedback &amp; Help
---

### Post by JFAWCETT on 2010-03-05
I'm sorry, I just joined this site and I'm very far from knowing where I should POST this, so I'll try it here.
I have a DELL MINI 9 with Ubuntu 8.04 loaded on it. I LOST(forgot) my ADMIN Password. I tried and tried to get DELL support to help me, no luck even getting through. I came to the conclusion I needed to reinstall the OS. I don't have a CD-ROM for the Disk. I did however get my hands on a USB memory stick with Ubuntu 9.1 on it. So I loaded it...I could NOT for the life of me get my wireless to work. I tried everything( I think). In addition to that problem I was getting HARDRIVE ERROR messages. I searched all these forums for answers without any success. So, I went to the local Office Supply and purchased a "stand alone" CD-ROM so I could reload the original OS. My HARDDRIVE errors have vanished(that's a good thing). Now, I still can't get the Wireless to work??? It worked fine before I messed with the computer?
It "finds" my wireless network just fine, shows I have a very strong signal. It asks me to input my "passphrase", I do, as I have for all my wireless computers,etc. It tries to log-on, it always comes right back to asking me to enter my passphrase....and endless loop.
What am I doing wrong????? I'm clearly not a computer expert.
Thank you in advance for your help.
John

---

### Post by undecim on 2010-03-05
This should have been posted in Absolute Beginner Talk, General Help, or Networking & Wireless. Don't worry though, a moderator will come by soon and move it for you.

In most cases, you will need to update your system and install hardware drivers if your wireless card doesn't work out-of-the-box.

To do this, you will have to connect to the internet via an ethernet cable, and open the Update Manager from System -> Administration -> Update Manager. You don't have to install the updates just yet, but if you see a list of updates, that means that your package list has been refreshed, which is all we need at the moment.

After that, you should see a wireless driver available in System -> Administration -> Hardware Drivers. Install that, reboot, and you should be able to use your wireless connection.

If that doesn't fix your connection, I can help you diagnose the problem further, but I need some information on your wireless card. If you open a terminal and type "lspci | grep Wireless", then post the output here, that will tell me what kind of wireless card you have.

---

### Post by Elfy on 2010-03-05
I see you started a thread in ABT - I will close this one.

In future you can use the Report Abuse button to alert staff and ask for it to be moved.

---

