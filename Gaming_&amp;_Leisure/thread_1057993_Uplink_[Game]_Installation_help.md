---
title: "Uplink [Game] Installation help"
date: 2009-02-02
forum: Gaming &amp; Leisure
---

### Post by CodaNull on 2009-02-02
Hello everyone.

I'm relatively new to linux - i've been messing around with it whenever i have a computer that becomes "old" since about 98, but i'm by no means an expert. For example, if someone said "chmod such and such" i'd be relatively comofortable, but beyond that level of technical knowledge i'm stuck. 

Here's my problem. I have a CD for a game called Uplink. I bought it, paid for it, all that fun stuff. I have the DEMO of Uplink installed on this linux machine and it works fine. I have been following this guide to try to get the full version running:

[http://ubuntuforums.org/showthread.php?p=3396009](http://ubuntuforums.org/showthread.php?p=3396009)

Now, that's fine with one problem. There is no such thing on the CD (unless i'm doing something wrong) called "Uplink.zip". Could someone help me out, with as clear and step by step a set of instructions as possible? Thank you, very very VERY much.

---

### Post by willbe1kenobi on 2009-02-02
Try looking in the 'linux' folder in the root directory of the cd. It will most propably be there

---

### Post by CodaNull on 2009-02-02
I tried doing that, but the only zip file in that directory is one that is labeled "patch"; and that doesn't work.

---

### Post by willbe1kenobi on 2009-02-02
I may have just figured it out your problem. this is what I have done on my  64 bit version. If you have a 32 bit ubuntu o.s then just follow steps 3 and 9 from below

1. install 'getlibs' ([http://www.boundlesssupremacy.com/Ca...etlibs-all.deb](http://www.boundlesssupremacy.com/Ca...etlibs-all.deb). Download and then double click the file to install

2. enable all of the repositories.

3. download the linux patch from here ([http://www.introversion.co.uk/cgi-bin/countdown.cgi?linuxpatch1.54.tar.gz](http://www.introversion.co.uk/cgi-bin/countdown.cgi?linuxpatch1.54.tar.gz))

4. open terminal and type in 'sudo getlibs -w [http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb)'

5. do a search on the ubuntu package database ([http://packages.ubuntu.com](http://packages.ubuntu.com)) for libglib1.2, but select ALL distrobutions, select for the newest distobution then follow the onscreen instructions. Remember you need the 32bit version.

6, in a terminal go to where you downloaded the file libglib1.2_1.2.10-17build1_i386.deb (in step 5) and type in sudo getlibs -i /<WHERE_YOU_DOWNLOADED_FILE/libglib1.2_1.2.10-17build1_i386.deb

7. go to where you downloaded patch in step 3

8. type in 'sudo linux32 uplink-patch-1.54.sh' then press enter. this should install the binary files (ones just to start the game). If it gives an error stating that linux32 is not installed, open up synaptic and install 'util-linux'. It should work.

9. Then just copy following files to the 'lib' subfolder of where you installed uplink (you will most probably find them in the windows folder):

fonts.dat
graphics.dat
loading.dat
music.dat
sounds.dat (I am not 100% sure if this is one that will already be there)

Now you may start uplink by going to where you installed it and typing in 'sh uplink.sh' and then you will be on your way.

---

### Post by CodaNull on 2009-02-02
Thank you very much; i'll try all that and post how it went here

---

