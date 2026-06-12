---
title: "Download packages then install on other machine??"
date: 2005-06-28
forum: Desktop Environments
---

### Post by spedsta on 2005-06-28
Hi 
I am currently on the verge of installing either **suse 9.3 or ubuntu**(hoary).
But I need to clarify a few things before making my decision because I have only a 
dialup internet connection at home. 
so here are my questions:

1) I have a broadband connection at work but run windows there, is it possible to select an
   application for install on ubuntu, but download it and its dependancies in windows at work    then put it on cd or local folder and install from there?

2) Use these packages on a cd to install to other machines who don't have internet connections,    so they can't even get a list of possible packages to install?

3) to uninstall then maybe one day later reinstall these packages without having to download the    packages again. So the question is rather: Does ubuntu delete uninstalled packages from the    local drive so that one has to re download the packages when you want to reinstall again?

Between Suse and Ubuntu I really want Ubuntu to be my OS, mostly because its designed to be for the community and not actually making someone else richer, and secondly its just got so many great reviews that its almost impossiblie to not to want to use.
But i don't want to spend a fortune on downloading packages, my connection is really slooooow. 

I have read other posts here on the forums concerning issues like this but they are mostly talking about upgrading existing packages, and were a bit over my head  :?

---

### Post by jcooper on 2005-06-28
> I am currently on the verge of installing either suse 9.3 or ubuntu(hoary). 
First off, welcome to the Ubuntu community. Enjoy your stay :)

> 1) I have a broadband connection at work but run windows there, is it possible to select an 
You are probably aware of "apt-get" to install software in Ubuntu. This basically installs .deb files on your machine. You can also use the command "dpkg -i filename.deb" to install an application.

First, you need to [download the packages you're after](http://packages.ubuntu.com/hoary/) you're after (alternatively get them elsewhere). You then have two options. 

1. Configure apt to use the CD you burned the packages to as a source. Follow the instructions in [this discussion](http://ubuntuforums.org/showthread.php?t=7455).

2. Open a terminal, change to the directory containing the downloaded packages, and type "dpkg -i *.deb" to install them all.


> Does ubuntu delete uninstalled packages from the local drive so that one has to re download the packages when you want to reinstall again? 

Apt stores packages in a cache until they are deleted, so you can use these at your leisure. See the above linked discussion for details.

> Between Suse and Ubuntu I really want Ubuntu to be my OS, mostly because its designed to be for the community and not actually making someone else richer 

I personally prefer Ubuntu and its community, but Suse appears to bundle a lot of emerging technology (beagle, mono, customised OpenOffice.org 2 beta etc) that is otherwise unsupported and somewhat out of date in Ubuntu.

Having said that, Ubuntu Rocks!  :D

---

### Post by MaX on 2005-06-28
[QUOTE=spedsta]1) I have a broadband connection at work but run windows there, is it possible to select an
   application for install on ubuntu, but download it and its dependancies in windows at work    then put it on cd or local folder and install from there?

2) Use these packages on a cd to install to other machines who don't have internet connections,    so they can't even get a list of possible packages to install?

[/quote]

Yes, edit your repositories to point at hoary instead of warty (if you don't have warty order the hoary CD and you'll be set).
Anyway, reload the repository list in synaptic, mark all upgrades, choose smart upgrade.but don't apply! Then there's an option to save what you have marked.
Do this, then you get a file that you can download the packages in that file.

Do this at work, move them to /var/cache/apt/archives/ on your warty and start synaptic again, load the list again, choose apply and off you go!


My last advice, is to order 10 CD's for you and your friends from Canonical.

---

### Post by spedsta on 2005-06-29
Thanks for the advice guys, I am almost clear on my probs except two things,

a) when you say mark for upgrade, does that mean mark for install, say for example, after a fresh install i wanna install "bluefish" , then i activate the extra repositories start up synaptic and refresh the list, locate the app and say install. Then 
"get a file that you can download the packages in that file" . take that to work , download the packages and then, come back home , add cd as a repository and install app?( :roll: )

b) if i download a deb package , will its depencies be included in that download?( (probably not),  if not , how will I know what its depencies are?

 ](*,) 
thanks

---

### Post by Navin_Johnson on 2005-06-29
I have the same setup as you (fast connection at work / modem at home).  Although I've not yet done it I would think the way to go would be the following:

1 at home select the app you want in Synaptic (or apt-get), take note of the dependencies (I think apt-get just lists them, in Synaptic you have to click on "details" or some such thing)

2  at work download the files (including the dependency files you took note of)

3 if you burn to a cd then use the instructions already posted for that route.  

4  Or, if you are using another method (I would likely use the SD card in my palm pilot) it may work to copy the deb files to /var/apt/cache (you'll have to double check where apt/Synaptic keeps the cached files.  After you copied the files you should be able to proceed and Synaptic will find the files in the cache directory.  [I could be wrong about this since I've not yet tried it:  but it seems like it should work]

Navin Johnson

---

### Post by jiyuu0 on 2005-06-29
this has many of the common packages
[http://ubuntuforums.org/showthread.php?t=30147&highlight=add-on-cd](http://ubuntuforums.org/showthread.php?t=30147&highlight=add-on-cd)

may not be all the ones you are looking for, but should be sufficient to make your ubuntu box rock

---

### Post by Alexandr on 2005-06-29
Hint:

```
sudo apt-get --print-uris install <name-of-application>
```

prints links for application  package and **all its dependancies**.

Copy hyperlinks, download all packages "in windows at work then put it on cd or local folder". Copy to Ubuntu home mashine.

Hint:

```
sudo dpkg -i -R <your-folder-with-downloaded-packages>
```

installs **ALL** packages from <your-folder-with-downloaded-packages> recursivelly.
 :)

---

### Post by spedsta on 2005-06-30
Okay, THATS IT!!!

 i have decided to definitely **install Ubuntu**, 

 \\:D/ You Guys are the best Linux support forum i have ever come across, and i have been running mandrake for the last year and 10 months about, I have posted a few posts to know this.

This is the way that linux and all software should be, 

"the true spirit of Ubuntu"

Thanks to all who helped cleared up my problems  :grin:

---

### Post by codejunkie on 2005-06-30
just a thought if you have a dvd burner at work you might wan't to download the dvd version of ubuntu it comes with ubuntu+kubuntu and a lot of extra packages that are in the universe/multiverse repositories plus you can use it as a live-cd like knoppix and install from it, that is if you have a dvd drive on your home computer to.

---

