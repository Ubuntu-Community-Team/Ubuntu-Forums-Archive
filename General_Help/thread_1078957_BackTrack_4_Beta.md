---
title: "BackTrack 4 Beta"
date: 2009-02-23
forum: General Help
---

### Post by brianheard on 2009-02-23
Im very new to Linux. I just now got my Broadcom BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller working with ndiswrapper.Now what I want to do is to install and use the program BackTrack 4 but like I said I'm new to Linux and my brain is still windows programmed, pun intended, so anytime I cant just double click on something I get a little lost. I have the file that I downloaded from utorrent sitting on my hard drive but I don't know how to make it a part of my system so I can use it.As far as I know there's not just an exe. file that I can just double click on and have the program loaded onto my computer, is there? If not then do I need to copy the files: boot and BT4 somewhere to make them work. I won't even get into the fact that I have no idea what to do with BackTrack when I do have it running!

---

### Post by pbotros1234 on 2009-02-23
What's the extension on the BT4 file you downloaded from uTorrent?

---

### Post by cpyarger on 2009-03-10
BackTrack is the result of merging the two innovative penetration testing live linux distributions Auditor and Whax. Backtrack provides a thorough pentesting environment which is bootable via CD, USB or the network (PXE). And is downloaded from there site as an ISO image 

First you must burn the ISO to a dvd, 

Refer to here on how to do this,

[URL="https://help.ubuntu.com/community/BurningIsoHowto"]https://help.ubuntu.com/community/BurningIsoHowto
[/URL]
after this you can simply place the DVD into your drive and reboot the computer, tada BT4 up and running

the default user info is as follows:

Username -- root
Password -- toor

after you have the live cd up and running you are offered the choices of which GUI desktop you wish to use,
for the KDE use the command

     startx

or to use the FVWM desktop type
     
     bt4-crystal

to simply use the command line interface, type in

     /etc/init.d/networking start


To install to a Hard Drive refer to here

[http://forums.remote-exploit.org/showthread.php?t=20126]("http://forums.remote-exploit.org/showthread.php?t=20126")


Warning BT4 is still in Beta and does not yet have a graphical installer, to simplify the install you may want to use a separate hard drive and disconnect any other Hard Drives from you computer as to lower your risk of choosing the wrong drive while installing from the command line

Warmest regards,

Chris

---

### Post by cpyarger on 2009-08-23
a little not the newest backtrack 4 release does have an installer script placed on the desktop :) just in case anyone is still following:lolflag:

---

### Post by d3v1150m471c on 2009-12-20
why don't you just run backtrack 4 through virtualbox? you could also run it using vmware but virtualbox is much easier to obtain and it works just fine on my system. I have one side of my 3d desktop dedicated to backtrack, when i am using it, so i am simultaneously in my host and guest os. If you want to install it on virtualbox, boot from the .iso and install it. when backtrack starts up it may or may not be logged into root. if not login as root and use the password "toor". you can then access the kde interface by typing startx and then there will be an icon on the desktop to install it to the dedicated hard drive space specified on vmware. if you don't like it you can always just go back and delete it.

Note : i am using the pre final version of backtrack 4

---

### Post by cpyarger on 2009-12-20
why not just have a script for autologin and startx? after installing to a virtualbox HD? it wouldnt take that much to write that then you dont have to worrry about if its logged in or not

---

### Post by teage3 on 2010-01-31
> **cpyarger said:**
> BackTrack is the result of merging the two innovative penetration testing live linux distributions Auditor and Whax. Backtrack provides a thorough pentesting environment which is bootable via CD, USB or the network (PXE). And is downloaded from there site as an ISO image 

First you must burn the ISO to a dvd, 

Refer to here on how to do this,

[URL="https://help.ubuntu.com/community/BurningIsoHowto"]https://help.ubuntu.com/community/BurningIsoHowto
[/URL]
after this you can simply place the DVD into your drive and reboot the computer, tada BT4 up and running

the default user info is as follows:

Username -- root
Password -- toor

after you have the live cd up and running you are offered the choices of which GUI desktop you wish to use,
for the KDE use the command

     startx

or to use the FVWM desktop type
     
     bt4-crystal

to simply use the command line interface, type in

     /etc/init.d/networking start


To install to a Hard Drive refer to here

[http://forums.remote-exploit.org/showthread.php?t=20126](http://forums.remote-exploit.org/showthread.php?t=20126)


Warning BT4 is still in Beta and does not yet have a graphical installer, to simplify the install you may want to use a separate hard drive and disconnect any other Hard Drives from you computer as to lower your risk of choosing the wrong drive while installing from the command line

Warmest regards,

Chris


There are issues with the install of backtrack to the hard drive... I have successfully installed the tools Under Ubuntu karmic, Yet there where issues there too. I did some digging and with a lot of reading and trial and error, I have now successfully install the tools within Kubuntu 9.10 complete with the backtrack menu and so far, everything is working mint. I am in the middle of writing the "HOW I DID IT" so if you are interested i will post it when i am finished.

---

### Post by cpyarger on 2010-01-31
yes i would be quite interested please keep me posted

---

### Post by teage3 on 2010-02-05
Installing backtrack in Kubuntu (with backtrack menu)..I did this with kubuntu 9.10 on my netbook. my how to is too large to post.
   
   I followed many tutorials and learned alot from this. This was all trial and error mostly as i could not find anything covering a kde install. However, I managed it and will have posted what i have learned in the text only version. The original had pics but i had to edit them out to fit the file size required in order to post. You can find the post in tutorials of he forum under Install backtrack in Kubuntu 9.10.

---

