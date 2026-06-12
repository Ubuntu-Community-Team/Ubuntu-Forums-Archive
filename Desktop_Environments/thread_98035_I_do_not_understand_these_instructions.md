---
title: "I do not understand these instructions"
date: 2005-12-02
forum: Desktop Environments
---

### Post by Totally_Lost on 2005-12-02
Hello! I am using Konstruct to install KDE 3.5 onto my Ubuntu 5.10 install. I installed KDE via synaptic a while back and it just worked. Well I couldn't figure out how to install KDE 3.5 via apt-get so I decided to use Konstruct. Sounded safe enough! But alas my Linux ignorance is my achilles heel. Below are the instructions from the README file for Konstruct, but I have no idea what or where to make these changes! For the record I have been using Linux for about 7 months and have an awful lot to learn... like this!

Thanks for helping a confused brother out!

After installation
==================
After installation you have to set some variables allowing your system to find
KDE binaries and libraries and KDE to allow to find its own files, for Bash:

  export QTDIR=~/kde3.5
  export KDEDIR=~/kde3.5
  export KDEDIRS=~/kde3.5

  export LD_LIBRARY_PATH=~/kde3.5/lib
  export PATH=~/kde3.5/bin:$PATH

Setting KDEHOME too, e.g. "export KDEHOME=~/.kdetest", will tell KDE to save
your settings to this directory and leave default ~/.kde directory unaffected.

On shadow password systems you have to set $(prefix)/bin/kcheckpass SUID root
or SGID shadow - otherwise you will not be able to unlock a locked desktop.

The complete KDE desktop is started with "startkde", most distributions start
it if you set it to the WINDOWMANAGER variable in your shell initializations.

---

### Post by GeneralZod on 2005-12-02
There are repositories for this; the repository which you'll need to add to your /etc/apt/sources.list is available here:

[http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

I hope this makes you Less_Lost :)

It sounds a little buggy, though, so you might want to make some backups before attempting this!

---

### Post by lerrup on 2005-12-02
Out of interest why did you do it the "interesting" way?

I would suggest that you visit [www.kubuntu.org](www.kubuntu.org), put the repository for 3.5 from their in your list and use synaptic or adept to update your packages (presuming you have a working 3.4 at present).

If you don't add the address (you can use synaptic) and use:
sudo apt-get install kubuntu-desktop 
or use synaptic and click on kubuntu-desktop and this will install 3.5.

Good luck!

---

### Post by Totally_Lost on 2005-12-02
Thanks! I was using the wrong commands for apt-get! It looks like it's working now. I will post my success or failure when it's done. I am really trying to learn Linux but it's hard to give much time when you have 3 kids and are a widowed Father! But I do what I can when I can!

---

### Post by Totally_Lost on 2005-12-02
So it seems I made an error, I am using 5.04 not 5.10! Gee! Anyhow I have one more issue, and that is when I try to install Skype via Synaptic I get this error:

Depends: libqt3c102-mt (>=3:3.3.3.2) but 3:3.3.3-7ubuntu3 is to be installed

How do I get around this?

---

### Post by teaker1s on 2005-12-02
it's a dependency you will need to install, synaptic is an easier method if you tick preferences option to see recommended packages as dependencies.
:KS

---

### Post by lerrup on 2005-12-02
Good luck!

The wiki (see link at the top) is a good source of info on things for commands and stuff.

When did you install your system -how is is 5.04?

---

### Post by Totally_Lost on 2005-12-02
I installed the system about 6 months ago, the disk 5.04 Hoary Hedghog was given to me by my old Navy buddy, LinuxUser147560 (I think he is registered here, and I know he is over at JustLinux.com) anyhow, LU is off in New Zealand and I am here with questions!

The error for Skype is telling me that the lib I have installed is too new... i.e. I have to downgrade, but if I do that then I lose the KDE3.4 install that I have (everything seems to be linked to this particular file!) I know there is a way to install an older version then manually compile an application to point to where the older version is without messing with the installed newer version... but I haven't a clue!!

Also using Synaptic to update to KDE 3.5 didn't work. But the Konstruct installer seems to have worked, but as with my original posting, I have no idea how to implement the instructions! I am not very good with the system layout and still haven't a clue what files to edit to do what!. Total newb.

Thing is Hoary installed and just worked like LU147560 said it would. And I used Synaptic to update and maintain. Now all I want is to get Skype to work and install KDE 3.5 so I can enjoy the newer features. But my lack of knowladge and skill (plus time!) are making it a very slow and painful process.

I appretiate the help that is offered though!!! Very much! Well, gotta jet, last of the kids is off to school and I am heading out to work.

---

