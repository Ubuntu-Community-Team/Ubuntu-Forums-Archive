---
title: "How to update to Xfce 4.4 beta2?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by SlugO on 2006-07-11
I just noticed that Xfce released beta2 of its upcoming 4.4 desktop.
> **2006/07/10 - Xfce 4.4 beta 2 (4.3.90.2) released** 

Xfce 4.4 beta2 (4.3.90.2) is now available for download. Besides Mousepad and Thunar, this release also includes the new Xfce archive manager Xarchiver. Other than that a large number of bugs were fixed, and several core components were improved. A detailed overview of the changes between 4.4 beta1 and 4.4 beta2 is available [here]("http://www.xfce.org/release_notes/4.4beta2_changelog.txt"). Please help us making Xfce 4.4 the best Xfce release ever, download it, try it, help us fixing it! Get it from [this page]("http://www.xfce.org/index.php?page=download&lang=en").
Is it coming to repositories anytime soon? Since default Xubuntu installation is using 4.4 beta1 at the moment I don't think it would be too risky to move to beta2.

Or has someone managed to build it or install successfully from the .bin? I have built programs from source before but I have to admit that I'm a bit hesitant when it comes to manually updating your whole desktop environment.

---

### Post by dolby on 2006-07-12
[this](http://www.os-works.com/documentation/xfce-installers/4.2.1/xfce-installer/) might help u

---

### Post by vrecan on 2006-07-21
umm that is 4.2 not even close but good try!

---

### Post by gurgle on 2006-07-21
id like to know this as well.

---

### Post by tseliot on 2006-07-21
I doubt we will see the new release of Xfce on Dapper since it's a beta release and it might add new bugs, etc.

Stabiliy is the main concern of Ubuntu developers once a version of Ubuntu is released.

Just my 2 cents

---

### Post by dolby on 2006-07-22
> umm that is 4.2 not even close but good try!

thats the way used to install the new one thats available on the xfce page

if u are lookin for a deb wait til october/november

---

### Post by videodrome on 2006-07-24
"thats the way used to install the new one thats available on the xfce page"

Tis true! I am running the beta as we speak. I was running straight xubuntu to begin with. Then I downloaded the 4.4 beta2 installer from here:

[http://www.xfce.org/archive/xfce-4.3.90.2/installers/](http://www.xfce.org/archive/xfce-4.3.90.2/installers/)


Then I used synaptic to install a few things:

libgtk2.0-dev
libxml2-dev
libvte-dev
libxpm-dev
libdbh1.0-dev
libxfce4mcs-dev

Then "sudo apt-get build-dep libxfce4mcs" (necessary?)

Then I ran the installer. 

Loomis

---

### Post by SlugO on 2006-07-25
I did the same steps as you videodrome but I'm not sure if I got it working right. The About window is saying that the version I'm using is **4.3.90.2 (Xfce 4.4 BETA1)**. 4.3.90.2 actually *is* the version number of BETA2 but I think the window might have said that before so I'm probably still using BETA1. Also Thunar and Xarchiver don't seem to be updated.

Where am I supposed to install Xfce? I just put it in ~/.Xfce but that might be the wrong location... Should I put it over the old Xfce? Anyone know where to find it?

---

### Post by videodrome on 2006-07-25
Ooh I forgot that the installer asks you where you want to install it, and that is probably where you erred if you are still showing "beta1" after installation. Someone else can back me up here, as I don't remember exactly, but I believe that you install it to /usr/bin. I believe that I installed right over top of the old one while the old one was running. I now have Xfce 4 Desktop Environment version 4.3.90.2 (Xfce 4.4 BETA2).

Thanks

---

### Post by SlugO on 2006-07-26
[QUOTE=videodrome]Someone else can back me up here, as I don't remember exactly, but I believe that you install it to /usr/bin.[/QUOTE]
Or could it be the folder **/usr** since Xfce installation creates the directories:[LIST]
[*]bin[*]etc[*]include[*]lib[*]libexec[*]man[*]sbin[*]share
[/LIST]and /usr has them all except for etc.

---

### Post by SlugO on 2006-07-26
Well I installed it in /usr/local which is the default directory it suggests when you run it with sudo. And it works :D

The old Xfce actually seems to be in /usr since its executables are in /usr/bin but that probably doesn't matter since Beta2 is running fine from /usr/local :)

---

### Post by SlugO on 2006-07-26
Well this is kinda strange. I successfully installed it from Ubuntu on my newer computer but the older one keeps giving errors while I'm installing from Xubuntu. Here's what it says:```
appending configuration tag "F77" to libtool
checking for perl5... no
checking for perl... perl
checking for perl module URI::Escape... no
checking for perl module URI::file... no
checking for perl module URI::URL... no
configure: error: Atleast one of the required Perl modules (URI::Escape, URI::file and URI::URL) was not found on your system
!! Failed to configure exo, see the errors above
!! for details on the problem.
```I tried installing a couple of perl packages, libgnome2-perl and libperl-dev, but it didn't help. The basic perl stuff has already been installed by default of course.

Any idea what's wrong?

[EDIT]
Damn, now the system is a bit messed up ](*,)
It's still Beta1 but the installer obviously messed all the window decorations, screen resolution (claims that can't find "display" anymore) and the desktop only has an icon for the Opera after I started it. Wish I could successfully complete the installation, and that it would get things running properly again...

[EDIT2]
I got it working!
I installed libCGI-perl which also added libwww-perl and liburi-perl. The last one is probably the one that is most needed in this case.

Later on the installation stopped again during mousepad configuration. This time it was missing libxml-parser-perl. Also added libxml-perl to be on the safe side.

Now if I'd just know all the other packages that a fresh Ubuntu installation needs (besides build-essential) to build Beta2 I could turn this into a HOWTO...

Btw, feels like I'm talking to myself here :D

---

### Post by videodrome on 2006-07-26
Hey you aren't talking to yourself. Let's figure this out and write a Howto. I'll start with what I know, and you can add to it and fix it and whatnot.

Ok. Xubuntu 6.06 to Xfce 4.4 beta 2.

1) Download the 4.4 beta2 installer from here:

[http://www.xfce.org/archive/xfce-4.3.90.2/installers/](http://www.xfce.org/archive/xfce-4.3.90.2/installers/)

2) Install these packages in Synaptic:

libxml-parser-perl
libgtk2.0-dev
libxml2-dev
libvte-dev
libxpm-dev
libdbh1.0-dev
libxfce4mcs-dev

3) Then "sudo apt-get build-dep libxfce4mcs" (necessary?)

4) chmod +x xfce4-4.3.90.2-installer.bin

5) sudo ./xfce4-4.3.90.2-installer.bin

6) At some point the installer will ask you where you want to install it, and you should select /usr/local which is the default directory it suggests.

And be sure to read this: [http://www.os-works.com/documentation/xfce-installers/4.2.1/xfce-installe](http://www.os-works.com/documentation/xfce-installers/4.2.1/xfce-installe)

Loomis

---

### Post by SlugO on 2006-07-26
And you need to install atleast liburi-perl and libxml-parser-perl.
Not sure about libCGI-perl, libwww-perl and libxml-perl. Maybe, maybe not.

Also what are good options to select in the installer?
*Maybe not composition manager for older machines.
*Extra optimizations seem to work, atleast during my short testing no crashes.
*Gotta configure the display manager.
*What sound system does Xubuntu use by default? It says that Xfce has OSS as the default even though force ALSA is ticked by default on the installer. I just tested briefly but in my newer computer with ALSA option on I couldn't change the volume from the taskbar thingy anymore. Worked fine on the older computer where I didn't choose ALSA. So I'm assuming that it's better to leave this thing unselected.

---

### Post by llamakc on 2006-07-26
programs installed outside of the apt-get dpkg system usually are installed to /usr/local or /opt. Either one will allow you to run the Ubuntu version of a program and the manually checked-out version also.

---

### Post by dsyates on 2006-07-26
Here's how I did it:
Fisrt uninstall dapper's xfce:
sudo apt-get remove libthunar-vfs-1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 mousepad orage thunar thunar-media-tags-plugin xarchiver xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfmedia xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs<o>
Second, just to be on the safe side do the following:
sudo apt-get install libgtk2.0-dev libxml2-dev libvte-dev libxpm-dev libdbh1.0-dev
Then download the installer
[http://prdownloads.sourceforge.net/xfce/xfce4-4.2.3.2-installer.bin](http://prdownloads.sourceforge.net/xfce/xfce4-4.2.3.2-installer.bin) from xfce. Do a chmod a+x on it, then install (be sure not to uncheck the alsa option or the build will fail)
For the record beta 2 is much better than the default xubuntu beta 1.

---

### Post by videodrome on 2006-07-27
For the record, I did not do any of the uninstalls that dsyates's mentioned. 

I also unchecked ALSA and my installer did not fail and I have sound.

I did check the composite manager but it does not work and I do not have a special tab to control it under advanced desktop settings or wherever it's supposed to be located at.

I have now successfully installed it this way on 2 vanilla xubuntu machines, an Inspiron 8000 and an Inspiron 5000. 

The only time the machines crash is a glitch that seems to be in xfce where sometimes clicking at the screen edges causes the mouse cursor to become a permanent resizing arrow and then the machine is just stuck. I tried killing processes with no luck determining who locked up so I have had to restart X. This has happened a few times in the past week.

Also, I do have parser-perl listed in my most recent post a few posts ago.

Thanks

---

### Post by avalan on 2006-07-28
> **SlugO said:**
> 
Not sure about libCGI-perl, libwww-perl and libxml-perl. Maybe, maybe not...


You need it to compile XFCE :P I tested so i know :)

---

### Post by SlugO on 2006-09-05
Xfce 4.4rc1 is out! Thought I'd just continue this thread if ppl happen to have some of the same problems installing it. Get it [here]("http://www.xfce.org/index.php?page=download&lang=en").

For some reason Xubuntu can't decide whether to use the new Thunar 0.4.0 (which has Trash) or the older 0.3.1svn-r21789 that's listed in Synaptic. Usually it starts 0.4.0 on the first couple of times and then the older one. How can I get it to use only the new one? Should I just install one from svn or something..?

---

### Post by Neo40 on 2006-09-05
I'm using Xubuntu Dapper and I would like to upgrade xfce 4.4-RC1.
Can someone knows how to to it? Should I remove my current xfce first? How to proceed?
Thanks!

---

### Post by SlugO on 2006-09-05
> **Neo40 said:**
> I'm using Xubuntu Dapper and I would like to upgrade xfce 4.4-RC1.
Can someone knows how to to it? Should I remove my current xfce first? How to proceed?
Thanks!I finally completed the HOWTO on upgrading to Xfce 4.4rc1. Read it [here]("http://ubuntuforums.org/showthread.php?p=1465799").

---

