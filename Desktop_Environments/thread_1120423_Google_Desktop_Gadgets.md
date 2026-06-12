---
title: "Google Desktop Gadgets"
date: 2009-04-09
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2009-04-09
Hi, I was just wondering if Gadgets are supported for Google Desktop for Linux? I installed Google Desktop and was looking for a way to install Gadgets with it. I found a source code for something running gadgets on linux, but wasn't too sure on what to do for it.

Is there an easy way to run gadgets for Google on Linux?

---

### Post by andrea000 on 2009-04-09
Google gadgets run as a stand alone app so you do not 
need Google desktop installed unless you want it.
gadgets are in synaptic but not by default.add this to 
the third party software sources.

Go to System -Administration- Software Sources click on 
the Third-Party tab then Add and paste the following line

_deb [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main_


Install Google Gadgets using the following command from terminal

sudo aptitude install google-gadgets
 
If you would like them to auto start go to sessions preferences 
startup programs click add type google gadgets and for the command 
type in google gadgets.

Done

---

### Post by Tim Sharitt on 2009-04-09
It appears that there are a few google gadgets packages in the repositories(universe) including google-gadgets-gtk google-gadgets-qt and google-gadgets-xul depending on your desktop environment.

They can be installed via apt-get, Synaptic, or which ever package manager you prefer :)

---

### Post by TheIdiotThatIsMe on 2009-04-09
Thanks a bunch! I run Hardy, so I had to add the ppa as mentioned by andrea, but I got them up and running and it was a lot simpler than I thought...

I didn't realize they were seperate, but I ended up using them both. Thanks a lot for your help!

---

### Post by gonzomalan on 2009-04-28
thanks to the OP and andrea, i had the same question. i also found this page, if anyone is interested

[http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/](http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/)

---

