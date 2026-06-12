---
title: "Beyond the Red Line (Game With Linux Version) Based on Battlestar Galactica"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by mtn on 2007-04-19
Edit: i am moving this here (from here [http://ubuntuforums.org/showthread.php?t=413564](http://ubuntuforums.org/showthread.php?t=413564))  as it does not seem to being done by the mods.

I came across a new community developed game today, Beyond the Red Line, based on the new (rather than original) Battlestar Galactica TV series. This was exciting as there is a Linux (as well as Windows and Apple) version. I did have a problem running the game tho (on my Toshiba A120 running Ubuntu Feisty Fawn beta - fully updated), so I have documented the solution here for future reference.

Installing the game was easy. Download the Linux install to the desktop (took about 30mins). Then change the permissions of the file so that it is executable - right click on the file, choose the permissions tab and click the “allow executing file as program” check box, and then click close. Then run the install - double click the install file (BtRLDemoInstaller.run) and click “run”. After checking the files integrity the install box pops up, then click through the couple of options. install completed.

To run the game pop up Nautilus file manager and navigate to home-directory~/btrl_demo, double click the btrl_demo file (I might have had to make this executable as well!). The game starts - excellent. The problem was when I click on the “Briefing” option the game crashed with the error [Linux] ERROR: “Could not load ABexp04 anim file” at fireball/fireballs.cpp:697. This was solved by checking out the BtRL forums, and following this thread.

Download the file libtxc_dxtn060508.tar.gz (from the bottom of the s3tc page) on to the desktop. Unpacked it with archive manager - double click it and click extract. Then install libtxc_dxtn - pop up a terminal using Ubuntu’s main menu Applications>Accessories>Terminal and navigate to the libtxc_dxtn dircetory by typing… cd Desktop/libtxc_dxtn …and then hit the enter key. Then type the two commands below, hitting enter after each command, to install libtxc_dxtn.

make

make install

That got things going for me. I still have a problem with garbled sound, but I’m working on this but any help would be appreciated!

---

### Post by Perfect Storm on 2007-04-20
Already been two posted about it.

[http://ubuntuforums.org/showthread.php?t=409505&highlight=BSG](http://ubuntuforums.org/showthread.php?t=409505&highlight=BSG)

---

