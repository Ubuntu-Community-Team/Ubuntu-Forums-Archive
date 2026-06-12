---
title: "need help with wine please"
date: 2006-10-21
forum: Gaming &amp; Leisure
---

### Post by darkchyldebwar on 2006-10-21
this is my first time usuing anything other then windows and its pretty kewl but im haveing some difficulties installing wine so i can play counter strike or wow.  I'm using the ubuntu dapper drake for X64 processors. I have tried to get it using the synaptic and i also added the repository for it.  

I get the following errors-

Wine is not available in any software channel
 the application might not support your system architecture.

Then i check the repositories 

        Could not download all repository indexes

        The repository might be no longer available or could not be                                     contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

Then the following error

[http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:) 404 Not Found
[http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:) 404 Not Found

I try the sudo apt-get install wine

and this error fallows

Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


So i go and find a d/l for the newest version of wine 
so i d/l wine-0.9.23.tar.bz2

so i extract it to a folder
then run ./tools/wineinstall

so then i try to run the exe with the wine command and it says 

wine steaminstall.exe
bash: wine: command not found

maybe im doing something wrong?

well i then try winetools

sudo apt-get install libgtk1.2  since it needs this

wget [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz)

tar -xf winetools*

cd winetools*
sudo ./install

so everthing is fine up till now 

then when i try the wt command

/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


i would appreciate any and all help thanks in advance

---

### Post by Jarn on 2006-10-21
> **darkchyldebwar said:**
> 
I try the sudo apt-get install wine

and this error fallows

Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidateDid you add the wine repository? And did you type 'apt-get update' after you did?

> **darkchyldebwar said:**
> 
So i go and find a d/l for the newest version of wine 
so i d/l wine-0.9.23.tar.bz2

so i extract it to a folder
then run ./tools/wineinstall

so then i try to run the exe with the wine command and it says 

wine steaminstall.exe
bash: wine: command not found
You most likely downloaded the wine source there, not a binary. You need to compile it. If it is a binary, you would have to move it to somewhere that was in your path.

---

### Post by Somniis on 2006-10-21
Not sure if this will help you or not.  I had the same problem with downloading wine via the terminal and synaptic.

Go to System->Administration->Software Properties

Click on Add, then check the boxes beside Community maintained (universe) and Non-free (multiverse), and click Add.  Then try 'sudo apt-get install wine' in the terminal.

This let me download wine fine afterwards. :)

---

### Post by Syock on 2006-11-23
"/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

Did you manage to solve this problem? I wonder where it`s looking for libgtk-1.2.so.0 in. I have it installed, and I`m sure it actually comes with the default Ubuntu installation. What went wrong?

---

