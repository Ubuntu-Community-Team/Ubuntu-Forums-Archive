---
title: "Would like to have Mate"
date: 2012-02-06
forum: Desktop Environments
---

### Post by Randymanme on 2012-02-06
Hello,  
 

 I'm presently at  [http://www.noobslab.com/2011/11/install-linux-mint-mate-desktop-on.html](http://www.noobslab.com/2011/11/install-linux-mint-mate-desktop-on.html)
 

 The problem I'm having is highlighted with larger font below:
 

 randyman@randyman-EL1358G:~$ sudo apt-get -f install  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Correcting dependencies... Done  
 .
 .
 .
 The following extra packages will be installed:  
   python-mate-desktop  
 The following NEW packages will be installed:  
   python-mate-desktop  
 0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.  
 150 not fully installed or removed.  
 Need to get 0 B/83.9 kB of archives.  
 After this operation, 422 kB of additional disk space will be used.  
 Do you want to continue [Y/n]? y  
 (Reading database ... 268222 files and directories currently installed.)  
 Unpacking python-mate-desktop (from .../python-mate-desktop_1.0.2-1_amd64.deb) ...  
 [SIZE=4]dpkg: error processing /var/cache/apt/archives/python-mate-desktop_1.0.2-1_amd64.deb (--unpack): [/SIZE] 
  [SIZE=4]trying to overwrite '/usr/lib/python2.7/dist-packages/gtk-2.0/evolution/ecal.la', which is also in package python-evolution 2.32.0-0ubuntu6 [/SIZE] 
 Errors were encountered while processing:  
  /var/cache/apt/archives/python-mate-desktop_1.0.2-1_amd64.deb  
 E: Sub-process /usr/bin/dpkg returned an error code (1)  
 randyman@randyman-EL1358G:~$  
 

 [SIZE=1]So here's my question: what command may I use to force dpkg to overwrite '/usr/lib/python2.7/dist-packages/gtk-2.0/evolution/ecal.la'? [/SIZE] 
 [SIZE=1]
[/SIZE] 
 [SIZE=1]I don't use Evolution anyway (never have).  [/SIZE] 
 [SIZE=1]
[/SIZE] 
 [SIZE=1]Any help or alternative suggestions would be much appreciated.  Thank you.[/SIZE]

---

### Post by satanselbow on 2012-02-06
Have you looked at the solution provided in the comment thread you are following?

---

### Post by Myrddin Emrys on 2012-02-06
There's a much cleaner and easier way to install MATE than that! See: [http://wiki.mate-desktop.org/download#ubuntu](http://wiki.mate-desktop.org/download#ubuntu)

---

### Post by Randymanme on 2012-02-06
> **satanselbow said:**
> Have you looked at the solution provided in the comment thread you are following?

__________________
                     Code:
     cd /fridge/beer | drink && fallover 
-----------------------------------------------------------------
I've no idea what that means except, maybe, "go get some beer."  :guitar:

I did attempt to follow a solution proffered in the comments section at   [http://www.noobslab.com/2011/11/inst...esktop-on.html]("http://www.noobslab.com/2011/11/install-linux-mint-mate-desktop-on.html") (see screenshot).  It was my downloading and attempting to install 
[ftp://tridex.net/repo/ubuntu/pool/main/p/python-mate-desktop/](ftp://tridex.net/repo/ubuntu/pool/main/p/python-mate-desktop/) that got me here.

Moving on.  I do, in fact, have Mate installed and am posting with it now.  But I have to admit that I'm a little hazy on precisedly how that occurred 
cd /fridge/beer | drink && falloverMy first idea was to remove Evolution (since I don't use it anyway), but that would have entailed the accompanying removal of a lot of other packages that I needed to keep in order to retain a functioning os.  Next, I thought to just give up getting Mate on Ubuntu and just "sudo apt-get remove

---

### Post by Randymanme on 2012-02-06
> **satanselbow said:**
> Have you looked at the solution provided in the comment thread you are following?

__________________
				 	Code:
 	cd /fridge/beer | drink && fallover 
I've no idea what that means except, maybe, "go get some beer."

I did attempt to follow a solution proffered in the comments section at   [http://www.noobslab.com/2011/11/inst...esktop-on.html]("http://www.noobslab.com/2011/11/install-linux-mint-mate-desktop-on.html") (see screenshot).  It was my downloading and attempting to install 
[ftp://tridex.net/repo/ubuntu/pool/main/p/python-mate-desktop/](ftp://tridex.net/repo/ubuntu/pool/main/p/python-mate-desktop/) that got me here.

Moving on.  I do, in fact, have Mate installed and am posting with it now.  But I have to admit that I'm a little hazy on precisedly how that occurred 
cd /fridge/beer | drink && falloverMy first idea was to remove Evolution (since I don't use it anyway), but that would have entailed the accompanying removal of a lot of other packages that I needed to keep in order to retain a functioning os.  Next, I thought to just give up getting Mate on Ubuntu and just "sudo apt-get remove

---

### Post by Randymanme on 2012-02-06
Next, I thought to just give up getting Mate on Ubuntu and just "sudo apt-get remove  python-mate-desktop" since it seemed to me to be only partially installed, but the terminal wanted to install it.

So next, I decided to go to synaptic package manager and untick the python-mate-desktop box to either unmark or remove, whichever the case might have been.  But I couldn't get anything done there because of broken packages (i.e., unmet dependencies relating to python-mate-desktop). Whenever I clicked on "Fix Broken Packages" under the Edit tab, Synaptic would that the unmet dependencies were resolved, but when I clicked on "Apply," I'd be told to Fix Broken Packages first.

So then I decided to go repositories and uncheck the Linux Mint repositories, reload, and hope that all the Mate packages would have disappeared.  So I did that. 

 After I had another beer, I was distracted and went to close synaptic but was met with the message box wanting to know if I really wanted to quit and discard unapplied  changes?  Well, no (although I didn't quite recall exactly what those changes were).  So I clicked on "Apply," and viola!  a lot of Mate packages were being installed!

I logged out and logged back in to Mate.

To tell you the truth, finally getting Mate installed was rather anti-climactic.  However, there is one good thing: I can drag and drop from the home folder to the terminal without the terminal disappearing when I click on the package I want to drag and drop.  Can't do that with Unity.  Nor Gnome Shell.

Thank you very much for all the responses.
:guitar:

---

