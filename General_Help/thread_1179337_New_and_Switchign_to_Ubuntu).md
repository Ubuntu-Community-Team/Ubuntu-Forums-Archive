---
title: "New and Switchign to Ubuntu:)"
date: 2009-06-05
forum: General Help
---

### Post by noob707 on 2009-06-05
i was never able to try or even give ubuntu a chance because i am using family computers at the moment and installing a new os on a family computer isn't too smart. So i am getting my own personal laptop soon and i just had enough of vista already and since microsoft discontinued XP, this is my chance to try out ubuntu. I am gonna try ubuntu as a Virtual Machine first to get the feel of it. i have a few questions about ubuntu and some reviews on certain linux applications/programs. By the way, my laptop is comign with a 64-bit processor intel(i cant give the model number yet because i haven't decided which model i am getting yet), 6GB of RAM and vista ultimate 64-bit. so i will be installing the 64-bit of ubuntu.

-i am a gamer(World of Warcraft) and i was wondering how Wine is with WoW and other windows programs? Also how is Wine on a performance level?

-How do you guys critic Samba for accessing windows computers for file sharing?

-Will Ubuntu support and use all of my 6GB of RAM?(64-bit edition)

-CAn i run 32-bit software on a 64-bit ubuntu without a Virtual Machine?

-Is there an anti-virus for linux that you guys like(Free)

-i still need to see if my hardware(Video card) has a linux driver

-Will Wine be able to run 32-bit software in a 64-bit machine

-does ubuntu run programs in the background like windows

Thats about it for now and it woudl help a lot if you guys can give me any extra info about ubuntu. Thanks!!

---

### Post by Legace on 2009-06-05
[B]-i am a gamer(World of Warcraft) and i was wondering how Wine is with WoW and other windows programs? Also how is Wine on a performance level?
[/B]You can use the WINE AppDB to search for your app, and see how it works under WINE:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

**-Will Ubuntu support and use all of my 6GB of RAM?(64-bit edition)**
Yes

**-CAn i run 32-bit software on a 64-bit ubuntu without a Virtual Machine?**
Yes, but you will need the **ia32-libs** package. You can install it via Synaptic Package Manager.

**-Is there an anti-virus for linux that you guys like(Free)**
You can use Avast, but Ubuntu does NOT need an antivirus :) There are no viruses for Ubuntu.

**-Will Wine be able to run 32-bit software in a 64-bit machine**
Yes.

**-does ubuntu run programs in the background like windows**
Yes.

---

### Post by noob707 on 2009-06-05
thank you for the quick response and i just have 1 more questios that came into my head but your help was awsome.

-Ubuntu is a debian based linux distro right. so if a program for linux doesn;t contain a ubuntu installler, can i install and download the debian installer.

---

### Post by cdenley on 2009-06-05
> **noob707 said:**
> thank you for the quick response and i just have 1 more questios that came into my head but your help was awsome.

-Ubuntu is a debian based linux distro right. so if a program for linux doesn;t contain a ubuntu installler, can i install and download the debian installer.

It uses the same package format, so you should be able to unless the package you are installing depends on package versions which are not available in the ubuntu repos. Ideally, you shouldn't be installing third-party software, though. One reason linux is more secure than windows is that all the software comes from a trusted source, the repos.

[https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html)

---

### Post by solidsnake204 on 2009-06-05
> -Is there an anti-virus for linux that you guys like(Free)

For an open source AV there's ClamAV.
For non open-source, I use BitDefender (BitDefender Antivirus Scanner for Unices)

There's not much in Linux viruses, these are more of stopping your Windows's getting infected by a download you did through Linux.


> -i still need to see if my hardware(Video card) has a linux driver

What video card do you have?

---

### Post by blueridgedog on 2009-06-05
> **noob707 said:**
> 
-i am a gamer(World of Warcraft) and i was wondering how Wine is with WoW and other windows programs? Also how is Wine on a performance level?


Well, there is some info here:

[http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)

However, you may find enough to engage you in the Linux/GNU/Ubuntu world that you spend your PC time doing other things.  WOW is pretty cool, but leveling you human character through learning a new OS, shell scripting, perl, python, web page creation, mastering the gimp and exploring a new world of global computing my interest you more.  I wish you luck with your new computer!

---

### Post by noob707 on 2009-06-05
ya, i bought a C++ book not to long ago and i was reading and learning from sites and psp hacking every day. With a family computer, you cant always hog it all the time, so C++ is slowing down but once i get my laptop, it will be back up again. I was thinking of using Code::Blocks which i ahve always been using with the GCC compiler.

For the Graphics card, i still don't knwo which model it is cause the laptop i will be getting has amny different models each with a different GPU, so i don't knwo yet. I know that it is a Nvidia. Should i download the Nvidia drivers for it through Ubuntu(found a tutorial on it on the forums) or through the Nvidia site.

---

### Post by blueridgedog on 2009-06-05
> **noob707 said:**
>  I know that it is a Nvidia. Should i download the Nvidia drivers for it through Ubuntu(found a tutorial on it on the forums) or through the Nvidia site.

Good...great platform for Linux.  I recommend you wait until you get it and see how the install goes.  The drive that comes with Ubuntu works for most.

---

### Post by TheForumTroll on 2009-06-05
Ubuntu should prompt you with a driver install box so no need to download anything.

Oh and welcome btw. ):P

---

### Post by nickcollie on 2009-06-05
Just a quick message from someone who isn't an expert.

Vista drove me crazy an I dumped it about a year ago.  I have to say that none of the issues I thought were going to be a problem turned out to be. 

I have easily found good software for all the tasks I need.  And some of the software I really thought were going to be hard to replace.  But there is a huge stash of stuff on the repositories and best of all it is free and legal.  

As far as drivers go I had much more problems changing windows editions on machines (eg from 2000 to XP ) than I had moving to linux.  More often than not I have looked a bit dumb and said 'Oh it works already'

I use wine and most of the time I don't have a problem.  I don't know much about WoW but I can't see why it wouldn't be fine. 

Out of interest the only things I haven't really found a replacement for are:
The Napster Client
Irfanview ( a beautifully simple graphics editor)
That's it.

And you can run in dual-boot very easily to start with so my advice would be just to give it a try.  It took me six months to realise that I hadn't started up windows once :-)

Nik

---

### Post by TheForumTroll on 2009-06-05
> **nickcollie said:**
> 
...
Irfanview ( a beautifully simple graphics editor)
...


According to the FAQ on their site it should work in Wine:
[http://www.irfanview.com/faq.htm#Q45](http://www.irfanview.com/faq.htm#Q45)  ;)

---

### Post by albinootje on 2009-06-05
> **noob707 said:**
> 
-i still need to see if my hardware(Video card) has a linux driver


Which video card do you have ?

Imho the best would be to boot from an Ubuntu installation cdrom or usb stick and then choose "Try without making changes", and then in the desktop open up a terminal (alt-F2, and type : gnome-terminal), and post here the output of this command :
```

lspci

```
That output can make it much easier for us to find out whether your video card and other hardware will be well supported or not.

---

### Post by albinootje on 2009-06-05
> **noob707 said:**
>  -Ubuntu is a debian based linux distro right. so if a program for linux doesn;t contain a ubuntu installler, can i install and download the debian installer.

You should try to stick to the Ubuntu repositories, and not mix it with Debian repositories.

For Ubuntu there's also [http://getdeb.net](http://getdeb.net), and the PPA at [https://code.launchpad.net/](https://code.launchpad.net/) :
e.g. : [https://launchpad.net/~jonabeck/+archive/ppa/](https://launchpad.net/~jonabeck/+archive/ppa/)

If you want to play with Debian, and have the newest software, I recommend reading about apt-pinning and backporting, and play with Debian stable and Debian testing, with backports from Debian unstable.

But remember, if you're not interesting in helping out at all with testing Debian Unstable and coming with feedbacks, and make regular backups, and you still want to use a lot of Debian Unstable packages and update frequently, and then.. your system breaks..you get to keep all the pieces ;-)

---

### Post by noob707 on 2009-06-05
thank you all for the comments. i look at the wine site for wow and there was a post for wow on 64-bit unbuntu 9.04 whihc is what im going to be installing and the guy said that it works perfectly except for the high quality shadow option which i dont use anyways. And that review was for patch 3.1.x(latest patch) and he rated it a gold. Which is the second highest rank and that means that it works flawlessly.

i heard a lot about ubuntu and linux and how great it is. I even convinced my uncle to switch cause he is fed up with windows. It is like microsoft doesn't even care anymore about their customers. I think that even windows 7 was still a let down too. Their only good program is microsoft word, ms visual studio and some others but man windows is a let down. Microsoft looks like they don't care about the people who want to customize their desktop and i like how linux offers that. I like how ubuntu comes with so many features where as windows you would have to download many little programs to just do one of those features. Like how ubuntu comes with a md5 hash checker in the command line. From what i have heard so far, installing programs seems to be easy and more secure.

---

### Post by albinootje on 2009-06-05
> **noob707 said:**
> Like how ubuntu comes with a md5 hash checker in the command line. 

Nice that you mention that :) I never thought about that, I'm so used to all these little tools that come with Linux after a default installation.
> 
From what i have heard so far, installing programs seems to be easy and more secure.

If you stick to the repositories, it is pretty easy, imho much easier than in MS-Windows.
Here's more information on that : [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

And.. it is important to either know which video card you have (because there are some issues in the newest Ubuntu with Intel and ATI cards), or.. you test drive it yourself with a bootable Ubuntu cdrom, dvd or usb-stick.

See here how to make a bootable Ubuntu usb-stick :
[http://lifehacker.com/5042630/unetbootin-creates-usb+bootable-linux-the-easy-way](http://lifehacker.com/5042630/unetbootin-creates-usb+bootable-linux-the-easy-way)  (You'll need an usb stick of at least 1 Gb).

What I like about bootable Ubuntu installation usb-sticks compared to the cdrom versions is that the installation is ... faster! :)

---

### Post by blueridgedog on 2009-06-05
> **albinootje said:**
> 

What I like about bootable Ubuntu installation usb-sticks compared to the cdrom versions is that the installation is ... faster! :)

I like the fact that you don't have to carry around a disk anymore.  I am no longer the dork with a pack of CD's, but the cool dude with a few USB keys in his pocket that do almost anything.  

I second the "test before you buy" approach,

---

### Post by oldos2er on 2009-06-05
"man windows is a let down"

 ann@ann-desktop:~$ [B]man windows
No manual entry for windows[/B]

 Yes, I suppose it is.

---

### Post by albinootje on 2009-06-05
> **oldos2er said:**
> 
 ann@ann-desktop:~$ [B]man windows
No manual entry for windows[/B]

 Yes, I suppose it is.

A few months ago (while trying to study for the LPI exam) I learned a new command, see here the manual page of it :
```

man cancel

```
And .. look at the copyright in there.

---

### Post by oldos2er on 2009-06-07
> **albinootje said:**
> A few months ago (while trying to study for the LPI exam) I learned a new command, see here the manual page of it :
```

man cancel

```And .. look at the copyright in there.

 So shouldn't I see **copyright cancel taints kernel** when I boot up?

 Seriously, i wonder how many other commands are copyrighted other than GPL.

---

### Post by albinootje on 2009-06-07
> **oldos2er said:**
> So shouldn't I see **copyright cancel taints kernel** when I boot up?

 Seriously, i wonder how many other commands are copyrighted other than GPL.

I just found it funny to see the name Apple there, and I actually like the name cancel for cancelling jobs..

> 
SEE ALSO
       lp(1), lpmove(8), lpstat(1),
       [http://localhost:631/help](http://localhost:631/help)

COPYRIGHT
       Copyright 2007 by Apple Inc.

20 March 2006   Common UNIX Printing System   cancel(1)


Oh.. well.. Apple bought CUPS.  [http://en.wikipedia.org/wiki/Common_Unix_Printing_System](http://en.wikipedia.org/wiki/Common_Unix_Printing_System)
And CUPS is GPL and GLGPL licensed.

---

