---
title: "Cinelerra, no link or no run with 3 different versions"
date: 2006-06-09
forum: Desktop Environments
---

### Post by mrshawn on 2006-06-09
Hey all, 
I'm pretty new at running the newest Kubuntu under the Ubuntu (Dapper Drake 6.06 LTS) desktop, trying to get cinelerra to work with no luck! I love the Ubuntu/Kubuntu OS, just need apps to replace Sony Vegas and DVD Architect for serious video production. Then I may have my long awaited chance to ditch the Evil-Empire-OS. So far Cinelerra seems to be the best lead.  

I've tried installing 3 versions and have the following problems with each...
1. Seemingly the most promising...
cinelerra_2.0-2_i386.deb from 
[http://skulboxx.com/Ubuntu/sbx/](http://skulboxx.com/Ubuntu/sbx/)
Installs fine and smooth, get the notice that it's done. If I go to reinstall it says the same version is already installed. It even shows up fine in Synaptic PM. I simply can't find a link to it in the applications menu. I do a search in the File Browser, in all places and nothing comes up except the files I downloaded. Just want to know how to start it up. 
Tried 2 more...
2. cinelerra-2.0-1.x86_64.rpm taken from 
[http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3)
It unpacks fine. I go to the folder where I unpacked it, then... usr/bin/ double click the Cinelerra icon, absolutely nothing happens, no reaction to the double click at all. K, try one more...
1. cinelerra_2.0.0-3svn20060606_i386.deb received from 
[http://www.kiberpipa.org/~minmax/cinelerra/builds/pentium4/](http://www.kiberpipa.org/~minmax/cinelerra/builds/pentium4/)
problem: keep getting error before install: "Error: Dependency is not satisfyable: libasound2". I went to Synaptic and installed all files related to libasound2, 4 of them. Still same problem. Tried installing all lib[xxxx] from that site and all other versions too.

Been searching for hours and the above 3 are the only ones I could remotely get to work. I've read other ways to do it through command lines but I know pretty much nothing about using command lines. 

Help! :confused:

---

### Post by franck.galbrun on 2006-06-10
Try this one:

[http://www.kiberpipa.org/~gandalf/blog/?p=47](http://www.kiberpipa.org/~gandalf/blog/?p=47)

Works fine, as long as you don't have the original dapper mjpegtools package installed. If so, just uninstall it (hoping you don't use any dependent package). I pointed this out to the author of the package, he said he would fix it.

---

### Post by mrshawn on 2006-06-12
Franck, 
I will do this as soon as I get a chance then post results here.

I really appreciate your time and help. 
-Shawn :)

---

### Post by franck.galbrun on 2006-06-13
Go ahead, the guy has just updated the packages so that everything's ok now.

All the credit goes to Jure Cuhalev, the author of these packages!

Regards

---

### Post by mrshawn on 2006-06-14
Franck,
Arghhhh, total newbie problems I guess...

I have a P4 so I do this...
Load Konsole, type 
sudo nano /etc/apt/sources.list

I get this...
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted uni$
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted$

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Then I add the following lines at the end and save...

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main universe multiverse restricted
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./

...go back into fresh command line and type...

apt-get install cinelerra

Then I get this...

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Any ideas on what I'm doing wrong?

---

### Post by Mr.Auer on 2006-06-15
Did you save AND close the sources.list file before trying to use Synaptic? If its still open in the editor, synaptic cant get a lock on the sources.list file and cannot work.

---

### Post by mrshawn on 2006-06-15
I tried last time right from Konsole. 

Tried today from Synaptic, after install got...
E: /var/cache/apt/archives/libiec61883-0_1.0.0-0.1_i386.deb: trying to overwrite `/usr/lib/libiec61883.so.0.0.0', which is also in package libiec61883

BUT... Cinelerra FINALLY showed up in my apps menu AND it actually started up. I haven't messed with it yet but it looks like it will work. 

I know credit for the app build goes to Jure. But, with my being pretty new to Unix/Linux you've helped me a lot and I really appreciate it. Learned more about command lines, etc.

---

### Post by mrshawn on 2006-06-15
Hmmm, now it broke something to do with all software updates, installers, etc. Had to uninstall Cinelerra for things to go back to normal. 

You've done a lot to help. I think for now I'll just wait 'till the new Ubuntu is more wide-spread and packages like Cinelerra are more effecient. Maybe Jure will fix some things soon.

---

### Post by jacob01 on 2007-07-01
stay away from cinelerra i have tried to get it running reliably and have had no sucess every time i load a vid clip the program crashes and i have done research and im not alone it may have some good features but it is so un reliable it is nearly imposable to edit any thing and eaven if you do make progress with with a video you are working on it still wont be worth geting so frustrated

but if you still want it heres a link were you can read a tutorial about haw to install it

[http://ubuntuforums.org/showthread.php?t=464223&highlight=how+to+install+Cinelerra](http://ubuntuforums.org/showthread.php?t=464223&highlight=how+to+install+Cinelerra)

---

