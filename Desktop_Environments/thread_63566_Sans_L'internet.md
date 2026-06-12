---
title: "Sans L'internet"
date: 2005-09-08
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-09-08
Has anyone ever tried to install something without the internet? 

RPMs need dependancies and APT needs access to a repository

Autopackage only has a few things available at the mo, and openpackage is a rubbish way of instaling things.

Sources don't complie without the right compilers and dependencies, and that would be ok if they said what they were but they don't. 

The GNU Source Installer looks good, but it fails on point 3 of the install (something begining with a T wont compile)

I have the complete debian repository for 3.0 i386, but it's out of date.

I would like to install GRAMPS (despite being one of the world's worst and most desperate acronym). I have all the dependancies for it. It wont compile tho. Something about python headers. Infact the only thing that has installed since going offline is Meld and it's lovely. 

I could rant that linux is crap at all this, but that wouldn't be very productive and the GNU is already on it. So, who knows how to install say, GRAMPS (or Inkscape or scribus) on an offline system. 

"You'll have to get all the dependancies seperately" - I have them for GRAMPS, and note that dependencies should be listed in something like 'dependencies.txt' in each tar archive. 

"You'll have to get comliler programs" - I have some.. dunno what. Note that an OS that requires everything to be compiled should come with tools for compiling (just an observation)

NB: Totally run linux for 4 months (and bugger all works PROPPERLY)

---

### Post by az on 2005-09-08
[QUOTE=Dave_is_sexy]Has anyone ever tried to install something without the internet? 

RPMs need dependancies and APT needs access to a repository

Autopackage only has a few things available at the mo, and openpackage is a rubbish way of instaling things.

Sources don't complie without the right compilers and dependencies, and that would be ok if they said what they were but they don't. 

The GNU Source Installer looks good, but it fails on point 3 of the install (something begining with a T wont compile)

I have the complete debian repository for 3.0 i386, but it's out of date.

I would like to install GRAMPS (despite being one of the world's worst and most desperate acronym). I have all the dependancies for it. It wont compile tho. Something about python headers. Infact the only thing that has installed since going offline is Meld and it's lovely. 

I could rant that linux is crap at all this, but that wouldn't be very productive and the GNU is already on it. So, who knows how to install say, GRAMPS (or Inkscape or scribus) on an offline system. 

"You'll have to get all the dependancies seperately" - I have them for GRAMPS, and note that dependencies should be listed in something like 'dependencies.txt' in each tar archive. 

"You'll have to get comliler programs" - I have some.. dunno what. Note that an OS that requires everything to be compiled should come with tools for compiling (just an observation)

NB: Totally run linux for 4 months (and bugger all works PROPPERLY)[/QUOTE]

dpkg --info (file.deb)
will print out the control file which will list the dependancies.

You can do 
sudo dpkg -i (file.deb) to install the file if you have all the dependancies.

sudo apt-get -f install to get the dependancies if they are in your repositories (just your cd, in your case) or remove the package if the dependancies are not present.

Install build-essential and you are mostly good to go to compile stuff.  You will still need the header files for the libraries you will use, like libgtk2-0-dev and so forth (the -dev packages)

---

### Post by Dave_is_sexy on 2005-09-12
[QUOTE=azz]dpkg --info (file.deb)
will print out the control file which will list the dependancies.

You can do 
sudo dpkg -i (file.deb) to install the file if you have all the dependancies.

sudo apt-get -f install to get the dependancies if they are in your repositories (just your cd, in your case) or remove the package if the dependancies are not present.

Install build-essential and you are mostly good to go to compile stuff.  You will still need the header files for the libraries you will use, like libgtk2-0-dev and so forth (the -dev packages)[/QUOTE]

That's interesting thanks, i didn't know that stuff about dpkg. But if build-essential is essential, it should be with the OS.. or at very least mentioned in an entry in the manual. 

Unfortunately, my cds don't have what I need, or if they do it is not conveyed and if no-one can be bothered to convey that stuff, then I'm not going to stress out over it - I'd rather go swimming.

**So question still stands how to install something without the internet???**

---

### Post by daveisadork on 2005-09-12
[QUOTE=Dave_is_sexy]That's interesting thanks, i didn't know that stuff about dpkg. But if build-essential is essential, it should be with the OS.. or at very least mentioned in an entry in the manual. 

Unfortunately, my cds don't have what I need, or if they do it is not conveyed and if no-one can be bothered to convey that stuff, then I'm not going to stress out over it - I'd rather go swimming.

**So question still stands how to install something without the internet???**[/QUOTE]

First of all, nice user name  :wink: Secondly, I think Ubuntu was designed to be used either as an internet OS for the advanced user, or a very small, self-contained OS for the new user. If you're looking for a huge library of software available for offline install, perhaps you should look into running Debian in all of its gigabytes of glory.

---

