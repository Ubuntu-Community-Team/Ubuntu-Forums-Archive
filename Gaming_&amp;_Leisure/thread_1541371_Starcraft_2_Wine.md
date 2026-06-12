---
title: "Starcraft 2 Wine"
date: 2010-07-29
forum: Gaming &amp; Leisure
---

### Post by ChrisEiffel on 2010-07-29
Hi 

I have wine 1.2 installed and I am running 64 bit Ubuntu 10.04 and I followed the directions here.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

I have the cd version of Starcraft II and I was under the impression once wine was updated to version 1.2 I should be able to right click on the installer and click

"Open with WINE windows program loader"

However every time i try to use wine to open the installer with wine a message pops up

 "No installer data could be found. If this problem persists, please contact Blizzard Technical Support."

Assuming my wine is properly configured how can I get the installer to run?

Thanks

---

### Post by foxmulder881 on 2010-07-29
Try navigating to the .exe launcher in the root directory of the media and running it with Wine from terminal.

---

### Post by ChrisEiffel on 2010-07-29
I tried that and got this message form the terminal.

chris@Starace:/media/SC2-L100-D1$ ls -l
total 2450
-rwx------ 1 chris chris 2505256 2010-05-24 18:56 Installer.exe
drwx------ 3 chris chris      88 2010-05-24 18:56 StarCraft II Installer.app

chris@Starace:/media/SC2-L100-D1$ wine Installer.exe
fixme:ole:OleCreateStaticFromData (not shown), stub!

The box still pops up that says 

No installer data could be found. If this problem persists, please contact Blizzard Technical Support.

Also if I try sudo

chris@Starace:/media/SC2-L100-D1$ sudo wine Installer.exe
[sudo] password for chris: 
wine: /home/chris/.wine is not owned by you

But I don't think wine is supposed to run off of sudo anyways.

---

### Post by foxmulder881 on 2010-07-29
> **ChrisEiffel said:**
> wine: /home/chris/.wine is not owned by you

You should not be getting this when running as sudo. How did you install wine?

Wine should not have to be run off sudo, you're right. But I'm glad you tried anyway.

---

### Post by ChrisEiffel on 2010-07-29
[FONT=Courier New]I had a previous installation of wine. I decided to remove the existing version and compile the newest source to make sure I had everything.

sudo aptitude install git

git clone  git://source.winehq.org/git/wine.git ~/wine-git && cd  ~/wine-git[/FONT]   
[FONT=Courier New]sudo  aptitude install build-essential[/FONT]   
[FONT=Courier New]sudo  apt-get build-dep wine

wget [http://downloads.sourceforge.net/project/wine/Source/wine-1.2.tar.bz](http://downloads.sourceforge.net/project/wine/Source/wine-1.2.tar.bz)

tar -xvf wine-1.2.tar.bz

cd wine-1.2
[/FONT]   
[FONT=Courier New]./configure  && make depend && make -j[/FONT][FONT=Courier New]5

sudo  aptitude remove wine[/FONT]   
[FONT=Courier New]sudo make  install


similar to the approach here 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19376) 
(note that was for the sc2 beta)
[/FONT]

---

