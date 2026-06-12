---
title: "Ncurse problems"
date: 2005-12-15
forum: General Help
---

### Post by locutus24 on 2005-12-15
Edit: Please move this forum to the proper area if i am posting in the wrong section
Ok so well trying to compile Xawtv, after a 20min battle to get g++-4.0 going thought it was going to work afterwards. Not really though sorta just didnt work, im now getting this odd error that if synaptic is right then i shouldnt be having this problem 
[http://locutus25.selfip.org/22.png](http://locutus25.selfip.org/22.png)
Sorry about the screencap gimp was being a problem too :???: 
Anyways though Synaptic says i have what i need, but xawtv ./configure says other wise. Not sure what to say besides can anybody tell me what to do, cause i got some vhs vids i want to watch and i dont believe in tvs.  
Also post a note if that pic doesnt come up my apache server has been going crazy too, but i think i have port 80 forwarded to that server and it registered at the proper IP so it should work. 
Please if anybody could point out a solution i would truly be grateful

---

### Post by amohanty on 2005-12-16
I think you need the libncurses5-dev package installed too.

HTH
AM

---

### Post by RAOF on 2005-12-16
Since xawtv is in the repositories, the first step to compiling it should be to get all the build-dependencies with "sudo apt-get build-dep xawtv".  That should install all the packages you need to build it.

---

### Post by locutus24 on 2005-12-16
Nevermind i cant install it anyways cause the dependencies for xawtv, and tvtime remove everything all my gnome stuff everything. Dagn't well now what to do, thank you anways though much appreciated

---

### Post by RAOF on 2005-12-16
[QUOTE=locutus24]Nevermind i cant install it anyways cause the dependencies for xawtv, and tvtime remove everything all my gnome stuff everything. Dagn't well now what to do, thank you anways though much appreciated[/QUOTE]
That should absolutely not happen.  Do you have any sort of crazy unofficial repositories in your sources.list?

Update: I can apt-get build-dep xawtv just fine.  It doesn't want to remove anything for me.

---

### Post by locutus24 on 2005-12-16
[http://locutus25.selfip.org/LOL.png](http://locutus25.selfip.org/LOL.png)
Would those be considered crazy

---

### Post by RAOF on 2005-12-16
**Yes, those are crazy.  The last 11/12 lines are totally nuts.**  Remove all the debian stuff.  That's why getting the dependencies for xawtv is removing all your gnome stuff.

---

### Post by locutus24 on 2005-12-16
Reverted to my original /etc/apt/sources.list file still getting the problem

---

### Post by RAOF on 2005-12-16
Ok, now it's time for some cut'n'paste.

Could you run:
```
sudo apt-get update
sudo apt-get build-dep xawtv
```
and post the result of the second command?

---

### Post by locutus24 on 2005-12-16
```
root@cabaret:/home/nickoli/Tar/mythtv-0.18.1# apt-get build-dep xawtv
Reading package lists... Done
Building dependency tree... Done
Note, selecting libjpeg62-dev instead of libjpeg-dev
Note, selecting libxft-dev instead of libxft2-dev
E: Build-dependencies for xawtv could not be satisfied
```
Well then seems i may have an irreversible problem

---

### Post by amohanty on 2005-12-16
Can you post the contents of your reverted sources.list

AM

---

### Post by locutus24 on 2005-12-16
[http://locutus25.selfip.org/files/sources.png](http://locutus25.selfip.org/files/sources.png)
Thats my /etc/apt/sources.bak file

---

### Post by amohanty on 2005-12-16
I am not sure if you need to do it but try enabling universe, ie, uncomment the following lines (remove # from the front):

deb [http://us.archive.ub..../ubuntu](http://us.archive.ub..../ubuntu) breezy universe
and the line following it.

HTH

PS: the actual text contents cut and paste here would be better than a screen shot.

---

### Post by locutus24 on 2005-12-16
Doesnt do anything, I think now its cause i installed some packages from the Debian site so now i got some random packages on my box. Now no matter what i do it still wants to tear out the entire box just to install one package
Thank you much though, your help was appreciated

---

### Post by amohanty on 2005-12-16
Did you run
> sudo apt-get update
after uncommenting those lines?
The debian pkgs would have to have some other worldly dependencies to cause that kind of situation.

---

### Post by locutus24 on 2005-12-16
Well found a solution, change the OS  reformat everything. Went to slackware 10.2 since it has a bunch of the C++ G++ CXX and other compiling libraries. Maybe it will work now but never know, again thank you i appreciate your help. In the end though i think it was that i installed broken debian packages onto my system which then wreaked some serious havok

---

