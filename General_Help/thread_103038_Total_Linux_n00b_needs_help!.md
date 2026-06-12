---
title: "Total Linux n00b needs help!"
date: 2005-12-13
forum: General Help
---

### Post by galvatron1983 on 2005-12-13
Hiya, 

Im a mac user whos been curious about linux for a while and Ive finally decided to give it go. 

I just installed Ubuntu 5.10 onto my dads PC on a seperate partition on the hard drive. I think its awesome, all the best things about Mac OS X but its free and even more secure! I have few questions tho as Im still learning the ropes, if anyone could help that would be great. Apologies if Im asking too many in one thread...

1. An archive manager came with the installation but Ive tried to use it to open a .deb file but all I got was an error message, saying that the file type is not supported. Do I need a seperate piece of unarchiver software for this kind of file? 

2. The .deb file is actually the firmware for a Speedtouch 330 USB modem, is is true that I need to go into the command line (Terminal) to connect to my ISP. 

3. Are any video codecs included with the basic unbuntu install eg. Xvid, DivX, 3ivx etc... 

4. Does anyone recommend a good linux book to read?

Thanks....

---

### Post by infoseeker on 2005-12-13
This site has some useful info

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by carlosqueso on 2005-12-13
Welcome to Ubuntu!

1. .deb files are installed with dpkg.  You need to install them with ```
sudo dpkg -i <packagename>
```

2.  You will probably need to work in the command line to set up your USB modem, search the threads for more information on that (I believe I've seen them.  The thing about linux, is that it's fairly command-line heavy and most people using it prefer the command line.

3. There are very few codecs with the regular install, since they are not free and put the ubuntuites into a sketchy legal situation.  [http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs](http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs) contains the information you need to install them.

4.  For Ubuntu, try reading the rest of that starter guide.  Other than that, I don't know.

Hope this helps.

---

### Post by Zonkle on 2005-12-13
I'm still new to Linux too, but I will try my best :)

1. An archive manager came with the installation but Ive tried to use it to open a .deb file but all I got was an error message, saying that the file type is not supported. Do I need a seperate piece of unarchiver software for this kind of file? 
**A:** .DEB file is like an installation file. To install, go to Application -> Accessories -> Terminal, then go to the folder where you have .DEB file using the cd command and then type:

*sudo dpkg -i **yourrfilename***

Then it will ask you for your password.

2. The .deb file is actually the firmware for a Speedtouch 330 USB modem, is is true that I need to go into the command line (Terminal) to connect to my ISP. 
**A:** You can connect using the Terminal but it is not a most. Do you have dial up? Then try going to the Administration -> Networking, and look for the modem.

3. Are any video codecs included with the basic unbuntu install eg. Xvid, DivX, 3ivx etc... 
**A:** I don't think so. You have to download something called w32codec. But I heard it is not legal every where :?
Look in the forum for the w32codec.

4. Does anyone recommend a good linux book to read?
**A:** I dunno :? .... 


Good luck ;)

---

### Post by NotJustANewbie on 2005-12-13
Good archive manager = ark

Speedtouch = crap (sorry but I had one of those frog like modems and got myself an ethernet router with no regrets)

Book = The internet is where I learned about Linux. Priceless... don't pay for free information.
**EDIT: I want a mac for Christmas... as one dies, one is born... lol**

---

### Post by phi on 2005-12-13
Well, &#187;standard&#171; cocecs (avi, mpeg2) are usually supported, but for quicktime and the like you should preferably install some of the win32codecs flying around the web.

---

### Post by tabinin on 2005-12-13
[Running Linux]("http://www.amazon.com/gp/product/0596002726/qid=1134493963/sr=8-2/ref=pd_bbs_2/103-8735790-4223044?n=507846&s=books&v=glance") is a great book if you are looking for something to hold in your hand.  It was very helpful for me to understand what's "under the hood" of all distros.  It won't be a great help for Gnome/KDE etc.  

I also went through a stage where I was downloading HOWTOs from [The Linux Documentation Project]("http://www.tldp.org/") and printing them to read on the train on the way to work.

As said above, the internet is the best resource.  Pick a problem to solve and use/search the forums or google to find the answer.

---

