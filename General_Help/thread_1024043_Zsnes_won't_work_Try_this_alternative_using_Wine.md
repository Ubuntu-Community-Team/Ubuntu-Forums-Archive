---
title: "Zsnes won't work? Try this alternative using Wine"
date: 2008-12-28
forum: General Help
---

### Post by gdbutcher on 2008-12-28
If like me, your a Noob to Ubuntu and you can't get Zsnes working using sudo apt-get install Zsnes or Applications Menu > Add/Remove, Zsnes then try this alternative: (it's not pretty but it worked for me)

1. Install Wine: goto Applications Menu > Add/Remove. Search for Wine, select and apply changes.
2. Download Zsnes for Windows and save it to your home folder. You can download the file zsnesw151.zip from from here: [http://www.zsnes.com/index.php?page=files](http://www.zsnes.com/index.php?page=files)]
3. Open your home folder, Right click on the file zsnesw151.zip, select Extract Here
4. Go into the zsnesw151 folder, Right click on zsnesw151.exe > then Properties, Select 'Open With' Tab, and then choose 'Wine Windows Program Loader' from the list and click close. 
5. Zsnes should now work simply by double clicking on zsnesw151.exe

Create a menu item for it by going to System >  Preferences > Main Menu. Then Select Games > then '+ New Item'
In the Create launcher box input the following: Name: Zsnes  Command: /home/fred(or whatever your username is)/zsnesw151/zsnesw.exe and click Ok to Finish.

I simply could not get Zsnes working through the repos, so I hope this helps!  

This worked on both my AMD64 machine running Ubuntu 8.10 (64 bit) and my NX9005 Laptop running Ubuntu 8.10 (32 Bit)

Any comments, corrections, or suggestions on how to make this easier are more than welcome.

---

### Post by gdbutcher on 2009-01-18
After a lot of searching I came across this. Its a much better way of Installing Zsnes than mine: (Many Thanks to eltoozero for it)

> **eltoozero said:**
> Sweet, yes in fact installing the Gutsy package for zsnes works.

Package download here: [http://packages.ubuntu.com/gutsy/i386/zsnes/download]("http://packages.ubuntu.com/gutsy/i386/zsnes/download")

You should freeze the package version using Synaptic so you're not stuck with software update killing your newly working zsnes.

System->Administration->Synaptic->
Select the packages you don't want to update
From packages menu -> select "Lock Version"
~or~
aptitude hold pkgname

Instructions stolen from: [http://ubuntuforums.org/showthread.php?p=1324502]("http://ubuntuforums.org/showthread.php?p=1324502")

:)

---

