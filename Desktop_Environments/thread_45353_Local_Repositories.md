---
title: "Local Repositories?"
date: 2005-06-29
forum: Desktop Environments
---

### Post by freedomandjustjuice on 2005-06-29
I am a relative linux newbie and i'm not entirely familiar with the directory structures etc yet so excuse me if this seems like a bit of a dull question but i have created a local directory on my hard disk to store downloaded binary install files which i would like to set up as a local repository for synaptic/kynaptic.

So first question is is this possible? Second question is is it worth doing? and third question is how the hell do the APT lines work? I have looked at the CD repositories and the net repositories to see how the structure works and understand that most (probably all) of my packages will be of the deb type and in binary format its just the location i can't work out, the folder i wish to use is located at /home/maxine/Software, how would i tell synaptic that i want it to look here for packages to install? i'm afraid i'm completely baffled at the moment.

I am familiar with the workings and structure of the Mac OS X but have never really understood the command line or any of the unix tools so i'm totally confused by the comands used etc so can anyone point me in the direction of a good beginners guide too?

I am using Ubuntu but have installed KDE as i prefer the way it looks and feels.

Ok i think thats it guys thanks (in advance).

TTFN

---

### Post by gil-galad on 2005-06-29
Why do you need a local repository?  If you want to install a deb file that is not on an internet repository, you type in **sudo dpkg -i <filename>** and it will install. 

\\//_

---

### Post by Terracotta on 2005-06-29
I don't know if it works, but you need to add the location of the repository in /etc/apt/sources.list  in which you can see there how a repository is created, maybe you need to add something like a name or so.
To gil-galad: what's wrong with this way of working, portage works the same way, and it's a nice one :-). Good idea, everyone's got his/her way of working, it's something I've thought of myself, but I never got to do it this time (never tried).

Will you inform us if you succeed in doing so?
Tx

---

### Post by gil-galad on 2005-06-29
Portage just puts the scripts on your hard drive, not all the files.  Thats a BIG difference.  Debian already puts the LOCATIONS of the packages on your hard drive, thats what apt-get update does, and its basically all portage does.  Having the entire repository stored on your hard drive would take many GIGS of data.  There is also no  real advantage to having the whole repository unless you are running a network with MANY ubuntu machines that can use your local repository.  When you download something with apt, it is also cached on your hard drive, so next time you install  the package it will be installed from the hard drive.  

What makes more sense along the same lines is having a couple dvds of the repository.  That way you have a local source of all the packages that you can use on multiple machines.  That is why you can download the whole debian distribution (the whole repository!) on several cds or a couple dvds.

---

### Post by Terracotta on 2005-06-29
I ment: there is a location where you can download the (source) files to you'ld like to have installed, if it's there you can ask portage to compile and install the package. it's what portage does itself: it first downloads the thing and then compiles it, you can even ask to download it without installing and install it afterwards. It's just a way of installing everything in the same way, if it's not in the repository you can download the file into one folder and then use apt-get to install it, the way you do it with all the rest, or even with synaptics. It's just a way of thinking, if it can be done like this, it's easy and simple. since I always somehow seem to have forgotten how to install a single .deb file I always need to go find somewhere the line with the correct 'spelling'. Yup I know, lazy guy here ;-), since I don't want to go look somewhere over and over again.

---

### Post by oliwally on 2005-06-30
I agree with Terracotta

I would love to know how to have Synaptic install something that I have downloaded. There seems to be an option in Synaptic to just download but not compile. Having those files available (either in a folder or CD) would be great. Why so ? Because on those occasions when I seriosly stuff up my Ubuntu installation, and I then need to re-install the whole thing (I'm not good enough to fix up all my stuff-ups), I would then have programs & utilities I want to add already on a CD, and I don't have to download them of the net again. Some of us still have download limits with our ISP you know !

So, when pointing Synaptic to a CD with the saved files (taken from  /var/cache/apt/archives ? or where does it save them to?) I get the message "this is not a debian CD" or something on those lines. How do I make a CD that will be accepted by Synaptic?

If I install off the CD, will it also recognize dependencies and look for them - even if they are not on the CD? Will  Synaptic get them from the net, or just simply tell me that there are files missing on the CD and call it quits?

---

### Post by freedomandjustjuice on 2005-06-30
hello agin thanks for the help so far, I just want to clarify what i intend to do with this repository, i don't want to have to remember all of the apt commands etc each time i want to install a file. Not to offend any of the linux purists but i find using things like the command line to perform functions a bit 1980s, i like a to have a gui because i can!! i know the command line is more powerfull blah blah but i'm all about ease of use so all i want is a directory i can place a few deb packages in temporarily so that synaptic will search in there and i can install them all in one easy move,

for example, i want to install amsn, and netatalk (i have an apple network i wish to connect to) both of the binaries are in the directory /home/maxine/software this is what i to make into a repository i just don't know how to point to it.

I thiink oliwally has the right idea about what i'm after from this - I don't intend to store gigs and gigs of data here or an entire install dvd just a few apps that i want to install without the fuss of using the command line each time.

cheers guys

---

### Post by oliwally on 2005-06-30
> Not to offend any of the linux purists but i find using things like the command line to perform functions a bit 1980s, i like a to have a gui because i can!! 
That's exactly how I feel about linux at present. Ubuntu has come closest so far (and I love playing with it), but there is still way to much mucking around to get things happening. In windows, I have never, ever used the command line, and when installing programs, they just work. No need to worry about dependencies etc. Ok, someone is going to stone me here and now for comparing linux with windows, and I have probably just demonstrated my ignorance about how complex it is to build a free os, but let's be real - If linux is ever going to be a n attractive option for soho users, then what we need is an easy to use operating system where you don't have to work in the shell to make things go the way they should. 

Sorry, I know it's a bit off topic. Glad to get it off my chest though.

Anyway, can anyone help with the synaptic thingo?

---

### Post by elsewhere on 2005-07-01
I understand what you're trying to accomplish, but I don't think it's as straight forward as pointing synaptic at a directory.  apt repositories have specific structures and index files (ie. try browsing [http://archive.ubuntu.com](http://archive.ubuntu.com) and you'll see what I mean).  No doubt you could set it up to work, but I suspect it may be a bit of a hassle.

On a side note, if you're looking for ease of use for installing packages etc., why not take a look at [Kubuntu Package Menu](http://www.kde-apps.org/content/show.php?content=23981) on kde-apps.org ?  It adds a service menu that allows you to right-click a .deb file and install it or view package info.

Cheers,
KV

---

### Post by jromer on 2005-07-01
Yes, here's how I did it...

I created a directory "/home/mylogin/local_packages" and
downloaded the files I wanted to install into the directory
then...cd to that directory and run... 

sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
(Note the "." and the capital "P")

This creates the Packages.gz file which Synaptic uses. (a directory of the files in the folder)

And then I added the following line to /etc/apt/sources.list:
 deb file:/home/mylogin/local_packages ./

After this I started Synaptic and reloaded and the files are now incorporated.

---

### Post by oliwally on 2005-07-10
Fantastic. Thanks for posting a usable solution ! 

Would this mean that the Packages.gz file has to be updated when new files are added to the directory?

I suppose once the Packages.gz file is created, the directory could then be saved to a CD, and Synaptic pointec to the CD drive as well?

---

### Post by Terracotta on 2005-07-10
Does one have to recreate that package.gz file every time you download a new .deb package, or does update itself automatically?.
Tx for the nice solution btw.

---

### Post by AndyAWS on 2005-07-22
Yes, you must re-run 
```
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
```
every time you add debs.
and reload the package info in Synaptic (or do apt-get -update)

---

