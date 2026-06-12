---
title: "Need help installing KDE 4.3 final release!"
date: 2009-08-05
forum: Desktop Environments
---

### Post by NinjaNumberNine on 2009-08-05
Hi, I just found out that the newest stable version of KDE was out, and I naturally was aching to try it, but now my problem: I don't know how to install! All I find on the site is a bunch of download links that bring me to websites like [**_this one_**]("ftp://kde.mirrors.tds.net/pub/kde/stable/4.3.0/src/"). How do I use these mirrors? I am obviously missing something. I would be glad of any help. I can't wait to try this thing!

P.S. running Kubuntu 9.04 with KDE 4.2.

---

### Post by azwar on 2009-08-05
> **NinjaNumberNine said:**
> Hi, I just found out that the newest stable version of KDE was out, and I naturally was aching to try it, but now my problem: I don't know how to install! All I find on the site is a bunch of download links that bring me to websites like [**_this one_**]("ftp://kde.mirrors.tds.net/pub/kde/stable/4.3.0/src/"). How do I use these mirrors? I am obviously missing something. I would be glad of any help. I can't wait to try this thing!

P.S. running Kubuntu 9.04 with KDE 4.2.

add this to your repo. 

deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main

then grab the public key here [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x2836CB0A8AC93F7A]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x2836CB0A8AC93F7A")

Refresh Kpackage Kit the do a full upgrade

---

### Post by bobbob1016 on 2009-08-06
I needed the staging repo too:

deb [http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu) jaunty main

---

### Post by iamah on 2009-08-06
This is looking awesome, thanks for the info... 

I had Ubuntu updated, added these to /etc/apt/sources.list :

deb [http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu) jaunty main
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main

Then copied the key above to a blank file, and added in Synaptic, options->authentication... funny, this method only worked including the comments delimiting the key...

sudo apt-get update
sudo apt-get install kubuntu-desktop

Choose GDM as default, istallation finished ok with a small warning about a doc package...

logged out, choose options > session > KDE,  got in KDE, wow! It's the most good looking desktop I ever used...:KS

---

### Post by PGHammer on 2009-08-06
> **iamah said:**
> This is looking awesome, thanks for the info... 

I had Ubuntu updated, added these to /etc/apt/sources.list :

deb [http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu) jaunty main
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main

Then copied the key above to a blank file, and added in Synaptic, options->authentication... funny, this method only worked including the comments delimiting the key...

sudo apt-get update
sudo apt-get install kubuntu-desktop

Choose GDM as default, istallation finished ok with a small warning about a doc package...

logged out, choose options > session > KDE,  got in KDE, wow! It's the most good looking desktop I ever used...:KS

And if you are able to use the compositing, prepare to get blown away.

(I'm curious; what does the default Kubuntu-desktop use for compositing?  I'm using OpenGL with the ATI Catalyst driver in the Jaunty repos for x64, despite having a wimpee-shirimpee of a GPU known as the HD3450.  Should I consider switching to another (read faster) compositing option?)

---

### Post by NinjaNumberNine on 2009-08-06
> deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main Sorry, forgot to say; complete linux nOOb here :D (but loving it) 
Question: How DO you add this to the repos?

---

### Post by NinjaNumberNine on 2009-08-06
Okay, I take back the question about the repositories, got that part done. Now, how exactly to I save the pgp key? (I got that far last time I tried)
You see, I just copied the text on the link azwar gave me into a text file and saved it, bu then in software sources it was not recognized as a valid pgp key (.pgp)
 Anyhow, thanks for all the replies! :D

---

### Post by Raboch on 2009-08-06
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
```
In Konsole should get you the key. Btw, I installed 4.3 sucessfully with just the backports repo without the staging repo, as now suggested on kubuntu.org itself.

Oh, and also use sudo apt-get dist-upgrade to do the upgrade. As there probably will be "blocked updates" in the graphical update manager, but that command will get all of them.

---

### Post by NinjaNumberNine on 2009-08-06
OK, it is upgrading. In about thirty minutes I should have the AWESOMEST desktop environment possible! (apologies to gnome users :D)

---

### Post by NinjaNumberNine on 2009-08-11
Sorry for the long delay between posts- I got it installed, restarted the computer, fell in love with[FONT=Palatino Linotype][SIZE=7][COLOR=Blue]KDE 4.3[/COLOR][/SIZE][/FONT] instantly, :lolflag: but then when I restarted again, my monitor showed NO PICTURE, (not even the motherboard logo) so I think I must have damaged the motherboard monitor outlet (yeah, I checked and made sure the cables were all connected.)

Anyway, I could not think of anything to do so I am using a different computer lol and it works okay, but my old one was FAST and had 3D graphics...:cry:  Now I have Kubuntu 9.0.4 installed again with KDE 4.3. The help you all gave me really helped. Thanks![IMG]http://kde.org/announcements/4.3/[/IMG]

---

### Post by NinjaNumberNine on 2009-08-11
Sorry for the long delay between posts- I got it installed, restarted the computer, fell in love with [IMG]http://kde.org/announcements/4.3/images/kde430-inspired.png[/IMG] instantly, :lolflag: but then when I restarted again, my monitor showed NO PICTURE, (not even the motherboard logo) so I think I must have damaged the motherboard monitor outlet (yeah, I checked and made sure the cables were all connected.)

Anyway, I could not think of anything to do so I bought a new computer lol and it works okay, but my old one was FAST and COOL...:cry:  Now I have Kubuntu 9.0.4 installed again with KDE 4.3. The help you guys gave me really helped. Thanks!

---

