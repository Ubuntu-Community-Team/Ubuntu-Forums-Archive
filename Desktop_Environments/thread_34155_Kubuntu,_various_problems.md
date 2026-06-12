---
title: "Kubuntu, various problems"
date: 2005-05-13
forum: Desktop Environments
---

### Post by themelvin on 2005-05-13
Hello,

first of all, i would like to know, why do I have to set up the sound everytime i restart my computer. The sound comes only from the right speaker, so I have to enable Sound Mixer and split the first channel. How can I save this setting?

Second thing, I can't install any software, It always says that gtklib is missing, but I don't know where to get this file

I also can't adjust the clock. When i click on the time and chose the set up it shows the winow with the root password, I enter the password and nothing happens. How can I change the clock to my real time?

How do I install java SDK? I have a *.bin file downloaded fform java.sun.com

EDIT: A silly question, how can i make a screenshot?

Thanks for the help.

---

### Post by engos on 2005-05-13
install libgtk

use NTP to set your clock

add this line:
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
to your /etc/apt/sources.list
run:
apt-get update
apt-get install sun-j2sdk1.5

---

### Post by themelvin on 2005-05-13
But, how do i install libgtk?

---

### Post by GeneralZod on 2005-05-13
[QUOTE=themelvin]But, how do i install libgtk?[/QUOTE]

How are you attempting to install the software? Kynaptic, Synaptic etc? Which repositories have you added?

> 
EDIT: A silly question, how can i make a screenshot?


I'm not at my Kubuntu machine right now, but I think the following is correct:

Press Print Screen (whole screen) or Alt-Print Screen (current window only).  Open KolourPaint.  Paste.  Save your new screenshot where you want it :) Alternatively, you might want to play around with ksnapshot.

---

### Post by Maestro23 on 2005-05-13
[QUOTE=themelvin]But, how do i install libgtk?[/QUOTE]


You can use Synaptic (Gui) or apt-get (command line) from a terminal to install programs.  If you are new to linux, I would follow the starter guide provided here in the forums to get your system up and running and learn how to do a few things.  You can find the link in my signature.

---

### Post by themelvin on 2005-05-13
I tried this:

sudo apt-cache search libgtk
But nothing hapens,

tried this:
sudo apt-get install libgtk2.0-0
And nothing happens

I downloaded a a file large 15MB libgtk2.0_2.6.4.orig.tar.gz but don't know what to do with it.

i tried with ./config but it says that can't find some path. /home/themelvin/gtk+-2.6.4 here are all the files.

What is kynaptic and synaptic?

EDIT: where do I have to put the file so the apt-get command work?

---

### Post by Maestro23 on 2005-05-13
[QUOTE=themelvin]I tried this:

sudo apt-cache search libgtk
But nothing hapens,

tried this:
sudo apt-get install libgtk2.0-0
And nothing happens

I downloaded a a file large 15MB libgtk2.0_2.6.4.orig.tar.gz but don't know what to do with it.

i tried with ./config but it says that can't find some path. /home/themelvin/gtk+-2.6.4 here are all the files.

What is kynaptic and synaptic?[/QUOTE]

Kynaptic and Synaptic are GUI package managers for installing Ubuntu/Kubuntu software packages.  Again, I suggest you start with that Ubuntu starter's guide as it will help you a great deal.

---

### Post by themelvin on 2005-05-19
The guide didn't help me a bit.

Nothing works for me from the guide.

For example:
It says that you have to write this to install thunderbird: "sudo apt-get install mozilla-thunderbird" but when i do this it says: "Couldn' t find package mozilla-thunderbird" and also for other things in the guide, mozilla, kino,...

I tried the Kynaptic the package manager, but there are not listed the packages that i want. I downloaded a lot of software but is on my desktop and don' t know how to put them in the Kynaptic list, or how to install. Whenever i want to install something it says that i don't have the libgtk or gtklib...

When i download something manually, where do i have to put it to make the apt-get command work? 
Or do i have to get special packages so the apt-get works? But where do I faind this packages?

---

### Post by GeneralZod on 2005-05-19
> **themelvin]The guide didn't help me a bit.

Nothing works for me from the guide.

For example:
It says that you have to write this to install thunderbird: "sudo apt-get install mozilla-thunderbird" but when i do this it says: "Couldn' t find package mozilla-thunderbird" and also for other things in the guide, mozilla, kino,...
[/QUOTE]

Sounds like you do not have the correct repositories enabled said:**
> 
I tried the Kynaptic the package manager, but there are not listed the packages that i want. I downloaded a lot of software but is on my desktop and don' t know how to put them in the Kynaptic list, or how to install. Whenever i want to install something it says that i don't have the libgtk or gtklib...


Try Synaptic instead (sudo apt-get install synaptic - this is assuming your sources.list is set up correctly, so you might want to post that here so we can take a look before trying it out) - it's far, far easier to use.  Can you explain a bit more about how you are trying to install software? It sounds like you are downloading .tar.gz/.bz2 files manually - is this correct? If so, this won't work, but you'll be pleased to see that the Synaptic way is much, much more convenient :) For reference, here is what should happen if your /etc/apt/sources.list is set up correctly and synaptic is installed:

1) Click on "K"-menu, choose System->Synaptic package manager.
2) Enter password when asked.
3) Click on the Search button in synaptic, and search for thunderbird.  
4) A bunch of matching software will appear.  Right-click on the one you want, and click Mark for Installation.
5) Search & select anything else you want installed.
6) Once you've selected all the software you want installed, click Apply.  Assuming everything goes well, all of the packages you want will be automatically downloaded and installed, so you can go and have a cup of tea, or something :)

Again, this is assuming sources.list is correct, so you might not want to try this until you've posted that.  The key point here is that you never have to manually track down a file and download it yourself - Synaptic will do all this for you.  It's great :)

Hope this helps,
Simon

---

### Post by themelvin on 2005-05-19
Sources.list content:

```

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://si.archive.ubuntu.com/ubuntu hoary main restricted
# deb-src http://si.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://si.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://si.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://si.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://si.archive.ubuntu.com/ubuntu hoary universe

# deb http://security.ubuntu.com/ubuntu hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security unive

```



Yes, i download the software manually and try to install it manually from archive files (.tar.gz,...).

I don't have the Synaptic in System, there are only these options:
KCron, KinfoCenter, Konsole, KSysGuard, KUser and Kynaptic.

When I enter "sudo apt-get install synaptic" in Terminal it says this:

```

melvin@senthx:~$ sudo apt-get install synaptic
Password:
Reading package lists... Done
Building dependency tree... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate
melvin@senthx:~$

```

Hope, that you can help me.

---

### Post by GeneralZod on 2005-05-19
[QUOTE=themelvin]Sources.list content:
[/QUOTE]

Yep, there's your problem, and rest assured, it's very easily fixed :)

Synaptic won't be on your system just yet, and won't be installed until you have your sources.list set up properly.  

Unfortunately, I dn't have access to my Ubuntu machine as I'm at work at the moment, so I can't provide you with a working sources.list.  Can anyone else here give themelvin him a decent sample of one?

If you want to have a stab at it yourself, try this part of the Ubuntu guide:

[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

and follow the instructions.  Then try 

sudo apt-get install synaptic

Should work this time, I think.  Then load up Synaptic and install any other software you want via the nice GUI :)

I know that at least one of the repositories has j2sdk and j2re, so if you add that repository, you can install the Java SDK with just a couple of clicks.  I can't remember which one it is, though, but can find out in a few hours' time.

---

### Post by tikal26 on 2005-05-19
in your list you must take out the # sign at the beggining of the list that would enable ou to dowload more software. I am new too so I am seinding you a snapshot of synaptic it is the easier way to do it for all of us that do not like the terminal or are coming from windows.
go to settings and then go to repositories then you shoul be able to fill in the blanks following the formatt  shown in the snapshot

---

### Post by themelvin on 2005-05-19
OMG, thank you very much, i think that works, now I am installing synaptic... yes it works, now I have the Synaptic under System :)

Wow it's so easy now, i just selected Mozilla from the menu and it's already in installation process it's even easyer than in Windows.

Thank you very much again :)

When i use synaptic, are the packages downloaded still on my HD after the installation or they get erased after the installation? If they are still on my HD, how do i find them, where do they get downloaded to?

Mozilla is installed :)

---

### Post by themelvin on 2005-05-19
I can't believe what is happening. I am downloading wine and opening a homepage, the download is 125kB/s (the limit is 128kB/s) and the homepage is opening very fast, in Windows XP i only dream this...

BTW, does anybody know how to solve my problem with sound? Everytime I close the AmaroK or restart the computer i have to set the settings back. It wouldn't bother me so much but the left speaker is not working, unless i split the channel, that it starts working probperly. How do I save this setting?

---

### Post by GeneralZod on 2005-05-19
[QUOTE=themelvin]OMG, thank you very much, i think that works, now I am installing synaptic... yes it works, now I have the Synaptic under System :)

Wow it's so easy now, i just selected Mozilla from the menu and it's already in installation process it's even easyer than in Windows.

Thank you very much again :)

When i use synaptic, are the packages downloaded still on my HD after the installation or they get erased after the installation? If they are still on my HD, how do i find them, where do they get downloaded to?

Mozilla is installed :)[/QUOTE]

Glad you got it all sorted :) It's weird - installation of software under Linux *always* gets a lot of flack, but I actually find it far superior to Windows.  Yes, the packages (.deb files) are stored - I think they're in /var/cache/apt/archives, but can't quite remember.  I'm afraid I can't help you with the sound, though :(

---

### Post by fluideye on 2005-05-19
> BTW, does anybody know how to solve my problem with sound? Everytime I close the AmaroK or restart the computer i have to set the settings back. It wouldn't bother me so much but the left speaker is not working, unless i split the channel, that it starts working probperly. How do I save this setting? 

How are you changining your settings?

---

### Post by themelvin on 2005-05-19
In the tray, i select the application and mixer than it appears in tray and i split the channel and then close the sound mixer.

---

### Post by buildid on 2005-05-20
> ## Uncomment the following two lines to fetch updated software from the network
# deb [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) hoary main restricted 

i believe you have to delete the "#"

so :
# deb [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) hoary main restricted

will be :
deb [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) hoary main restricted

if you do that with the other lines also you will have more / find more packages ....

---

