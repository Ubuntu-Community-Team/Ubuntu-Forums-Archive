---
title: "installing bittorrent on ubuntu 7.10"
date: 2007-12-13
forum: Gaming &amp; Leisure
---

### Post by kylethesir on 2007-12-13
I just recently (as in 2 days ago) installed Ubuntu 7.10 Gutsy and I am having hard times installing files.  I just downloaded bittorrent and I can't get past extracting the folder.  Please help and sorry...i'm trying hard to learn :).

thanks

---

### Post by rsambuca on 2007-12-13
There is a bittorrent client installed by default.  Just click on the torrent you want to download and it should open up automatically.

---

### Post by Beren Camlost on 2007-12-13
> **kylethesir said:**
> I just recently (as in 2 days ago) installed Ubuntu 7.10 Gutsy and I am having hard times installing files.  I just downloaded bittorrent and I can't get past extracting the folder.  Please help and sorry...i'm trying hard to learn :).

thanks

Where did you download Bittorrent, how did you try to install it, and most importantly, the filename of the package you are trying to install?

Also, like rsambuca mentioned, there is a standard torrent client that comes installed with Ubuntu as default.

---

### Post by kylethesir on 2007-12-13
tar.gz was the extension i believe and thanks i found it in synaptic, but i am having a problem in general installing programs i download them to the desktop and extract them to the desktop...what should be my next step? if i try to run the exe file nothing happens.

---

### Post by rsambuca on 2007-12-13
exe files are windows format, and installing tar files is usually a last resort.  Ubuntu has a repository of 20,000+ packages, all of which install with the click of a button.  I suggest you search in there for what you need.

You can open Synaptic from the top menu bar:  System -> Administration -> Synaptic Package Manager.

What type of programs are you looking for in general?  Perhaps we can give you some options.

---

### Post by kylethesir on 2007-12-13
ok in synaptic i have found warsow, however it is version 0.31 and the newest is 0.32 how can i patch this?  and thanks for your replies by the way

---

### Post by rsambuca on 2007-12-13
Personally I would just go with what is in the repos.  For the most part, the repos are pretty much set for each version of Ubuntu.  Newer versions of programs usually aren't updated until the next release of Ubuntu (next April, in this case).

Honestly, if you are the type of person that wants to have the latest versions of programs immediately and can't wait for a maximum of six months, then probably Ubuntu isn't the best distro for you to be using.

---

### Post by kylethesir on 2007-12-13
i dont mind not having the latest version it's just that the current warsow version installed wouldn't let me play online :(

---

### Post by kylethesir on 2007-12-13
thanks for your help though i will just stick with synaptic

---

### Post by kylethesir on 2007-12-13
i can't find bittorrent anywhere in the applications menu though...how do i run the program? thanks

---

### Post by rsambuca on 2007-12-13
Isn't it in your Applications - Internet menu from the top panel?

---

### Post by kylethesir on 2007-12-13
no its not azereus was there...but it wouldn't even run so I uninstalled it.  bittorrent is installed on my computer but I dont know how to run it.

---

### Post by sloggerkhan on 2007-12-13
Don't go with the repos for FPS games. A lot of them are too old and you will not be able to connect to multiplayer.

I'd just make a folder in your /home/$username/ called /srcnbin or something.
Then, when there's a game you want the latest version of, download the *.tar.gz and extract in that folder. There will be a binary file you can run in the resulting folder.

In warsow's case, the file you want to run is probably warsow.i386. (from [http://www.warsow.net/?page=download](http://www.warsow.net/?page=download) )
I suggest you then make a launcher and put it on one of your panels.

Now for bit torrents, I suggest either using the transmission client from the repos or using deluge from deluge-torrent.org (the have a *.deb in the repos, but the newer versions are 20x better). Just drag the torrent file in, choose where to download, and you're off, though you will probably want to adjust connection and bandwidth usage. Deluge has more features, transmission is very usable and simple.

---

### Post by kylethesir on 2007-12-13
THANK YOU so much slogger thats the info I was looking for I will try that now

---

### Post by kylethesir on 2007-12-13
sorry i'm a really big noob. I extracted it to the folder like you said however i try to open warsow.x86_64 and nothing happens, what should I do? by the way my GPU is AMD 64bit too.

---

### Post by rsambuca on 2007-12-13
> **kylethesir said:**
> sorry i'm a really big noob. I extracted it to the folder like you said however i try to open warsow.x86_64 and nothing happens, what should I do? by the way my GPU is AMD 64bit too.

That package is for a 64bit operating system.  Eventhough you have a 64bit processor, you may have installed a 32bit OS.  To find out, open a terminal and type:

uname -a

---

### Post by kylethesir on 2007-12-13
Linux kyle-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

I have 64 bit OS I think

---

### Post by rsambuca on 2007-12-13
Yup, you do.  Just checkin!

---

### Post by kylethesir on 2007-12-13
thanks man :) learnin more about ubuntu by the minute haha. any answer to why I can't run warsow.x86_64? is there a command I need to type in terminal??

thanks

---

### Post by sloggerkhan on 2007-12-13
Basically, it sounds like you have 32 bit ubuntu. Have you tried the i386 version?

---

### Post by rsambuca on 2007-12-13
> **sloggerkhan said:**
> Basically, it sounds like you have 32 bit ubuntu. Have you tried the i386 version?

No, he has the 64bit version (x86_64 GNU/Linux)

---

### Post by sloggerkhan on 2007-12-13
> **rsambuca said:**
> No, he has the 64bit version (x86_64 GNU/Linux)

I need to read more carefully.

---

### Post by kylethesir on 2007-12-13
i right click both files and click open, however nothing happens...not sure what to do...is there anything i must type in the terminal?

---

### Post by sloggerkhan on 2007-12-13
The terminal can help troubleshoot the problem. Open one in the directory and  run ./warsow.x86_84 
The output will probably have an error message that will be helpful.

---

### Post by sloggerkhan on 2007-12-13
looks like you went offline. Hopefully not a crash?

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=libcurl&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=libcurl&sourceid=mozilla-search)

try installing the libcurl3 package if it's not already.

sudo aptitude install libcurl3 or use synaptic.

---

### Post by kylethesir on 2007-12-13
slogger I thank you so much for helping me solve my problem :)

---

### Post by sloggerkhan on 2007-12-13
Is it working now?

---

### Post by kylethesir on 2007-12-13
yep, i just connected to a server and played around a bit, thank you so much sir. I greatly appreciate it...is there anyway that I can boost your rating?

---

### Post by sloggerkhan on 2007-12-13
lol.... rating? we have ratings?

Well, you're welcome, in any case.

---

### Post by kylethesir on 2007-12-13
haha guess not, but thank you very much for your time and effort

---

