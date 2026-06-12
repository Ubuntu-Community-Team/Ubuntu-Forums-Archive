---
title: "Whoa, man..."
date: 2008-12-04
forum: General Help
---

### Post by ciananh on 2008-12-04
i'm a new ubuntu user. new, as in, i formated my hard drive less than 20 hours ago and installed linux's ubuntu 7.04 OS. whoa, man... is this a change. i used window's OS for a good solid 8 years. windows is all i know, and this is definatly a 'culture shock' to say the least.

i have absolutely no clue as to what i'm doing. how would a 'noob' to linux go about a OS like this? i try to download programs, but i can't extract the .exe files. are there even .exe files in linux? i googled a tutorial on how to extract programs and what not, but all i got was abunch of code. something  like this:

~s/kajsdhfk/asdlhf.akjsdhfk/kjashdf   - what do i do with this code?

i just have no clue how to get around on this bad boy. i definatly love the change, i would just like some input on what things i should do to optimize this OS. and, like, where is the controller panel, and 'program files' and stuff.

):P

thanks abunch

---

### Post by kostkon on 2008-12-04
> **ciananh said:**
> i'm a new ubuntu user. new, as in, i formated my hard drive less than 20 hours ago and installed linux's ubuntu 7.04 OS. whoa, man... is this a change. i used window's OS for a good solid 8 years. windows is all i know, and this is definatly a 'culture shock' to say the least.

i have absolutely no clue as to what i'm doing. how would a 'noob' to linux go about a OS like this? i try to download programs, but i can't extract the .exe files. are there even .exe files in linux? i googled a tutorial on how to extract programs and what not, but all i got was abunch of code. something  like this:

~s/kajsdhfk/asdlhf.akjsdhfk/kjashdf   - what do i do with this code?

i just have no clue how to get around on this bad boy. i definatly love the change, i would just like some input on what things i should do to optimize this OS. and, like, where is the controller panel, and 'program files' and stuff.

):P

thanks abunch

Here is [a good guide]("http://www.psychocats.net/ubuntu/installingsoftware") explaining the way you install software in Ubuntu.

Hope that helps.

Although, are you sure you have installed 7.04 and not 8.04? Because 7.04 is not supported anymore.

---

### Post by fedex1993 on 2008-12-04
Either this is a joke or in the wrong section.

---

### Post by billgoldberg on 2008-12-04
> **ciananh said:**
> i'm a new ubuntu user. new, as in, i formated my hard drive less than 20 hours ago and installed linux's ubuntu 7.04 OS. whoa, man... is this a change. i used window's OS for a good solid 8 years. windows is all i know, and this is definatly a 'culture shock' to say the least.

i have absolutely no clue as to what i'm doing. how would a 'noob' to linux go about a OS like this? i try to download programs, but i can't extract the .exe files. are there even .exe files in linux? i googled a tutorial on how to extract programs and what not, but all i got was abunch of code. something  like this:

~s/kajsdhfk/asdlhf.akjsdhfk/kjashdf   - what do i do with this code?

i just have no clue how to get around on this bad boy. i definatly love the change, i would just like some input on what things i should do to optimize this OS. and, like, where is the controller panel, and 'program files' and stuff.

):P

thanks abunch

I'll start by saying that you'll want Ubuntu 8.04.

1 year in linux is 5 years in windows time.

I think you should give my absolute beginners guide a try:

[http://linuxowns.wordpress.com/2008/11/11/ubuntu-the-absolute-beginners-guide/](http://linuxowns.wordpress.com/2008/11/11/ubuntu-the-absolute-beginners-guide/)

---

### Post by ciananh on 2008-12-04
> **fedex1993 said:**
> Either this is a joke or in the wrong section.

no, this isn't a joke. i'm serious, i have not a clue what i'm doing with this OS. i also have no idea where to post in the forums. i figured a 'general chat' forum would be appropriate.

yes, i have version 7.04. i've gone to system>administration>update manager, and tried to update to a more recent version of ubuntu, but i keep getting a network error. i'm apparently going from 7.04 to 7.10.

---

### Post by billgoldberg on 2008-12-04
> **ciananh said:**
> i'm a new ubuntu user. new, as in, i formated my hard drive less than 20 hours ago and installed linux's ubuntu 7.04 OS. whoa, man... is this a change. i used window's OS for a good solid 8 years. windows is all i know, and this is definatly a 'culture shock' to say the least.

i have absolutely no clue as to what i'm doing. how would a 'noob' to linux go about a OS like this? i try to download programs, but i can't extract the .exe files. are there even .exe files in linux? i googled a tutorial on how to extract programs and what not, but all i got was abunch of code. something  like this:

~s/kajsdhfk/asdlhf.akjsdhfk/kjashdf   - what do i do with this code?

i just have no clue how to get around on this bad boy. i definatly love the change, i would just like some input on what things i should do to optimize this OS. and, like, where is the controller panel, and 'program files' and stuff.

):P

thanks abunch

If you don't care to read the link I have posted, I'll try to explain the basics very briefly.

If you have questions, ask them.

Installing exe's is a windows thing. 

Ubuntu uses software repositories to download and install software.

Just go to "applications -> add/remove" to install applications (make sure you search in all available applications).

A more advanced way to install programs is by going to "system -> administration -> synaptic package manager".

Some website will give you a new repository you can download software from.

The good thing about this is that Ubuntu's system updates will include updates for the software you installed from that new repo.

There are also .deb file some websites offer (opera.com, frostwire.com), think of those as the .exe installer in Ubuntu.

Windows programs don't run in Linux. 

But most likely any app you had on Windows will have an equally good or better (or worse) Linux counterpart.


--

Unlike in Windows, you aren't the root (admin is the windows term) in Ubuntu.

You can get root privilages by using sudo or gksudo if you want.

This is a security feature (think Vista UAC done right).

This means installing software will require you to enter your password, but it also means you can't edit the system files without becoming root.

This off course also means any potential thread can't really hurt your system that bad.

--

The code you gave is complete gibberish.

---

### Post by billgoldberg on 2008-12-04
> **ciananh said:**
> no, this isn't a joke. i'm serious, i have not a clue what i'm doing with this OS. i also have no idea where to post in the forums. i figured a 'general chat' forum would be appropriate.

yes, i have version 7.04. i've gone to system>administration>update manager, and tried to update to a more recent version of ubuntu, but i keep getting a network error. i'm apparently going from 7.04 to 7.10.

Just download the new iso, burn it to cd and install it.

It will be alot faster than update your OS 3 times.

---

### Post by ciananh on 2008-12-04
> **billgoldberg said:**
> The code you gave is complete gibberish.

i was giving an example of what i saw. i'm sure it didn't say all the gibberish i typed, but god bless if it didn't look like it to my eyes.. ;)


i've been reading your "ubuntu's ultimate beginners guide". i've already caught on to a small hand full of things. i guess this will just take AWHILE to grasp and get ahold of. kind of like relearning to ride a bicycle, eh?


-------edit-------

i went to, uhmmm, this:

[http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&mirror=http%3A%2F%2Fubuntu-releases.cs.umn.edu%2F&arch=i386](http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&mirror=http%3A%2F%2Fubuntu-releases.cs.umn.edu%2F&arch=i386)

and got this:

[IMG]http://img.photobucket.com/albums/v648/x9ez6nc/Screenshot.png[/IMG]

at about 15%...

what is the "source file"? should i just try redownloading it, or do i need to activate something on the OS.

---

### Post by chris4585 on 2008-12-04
by the error message I'd try again later

---

### Post by lemuriaX on 2008-12-05
I really like Aysiu's site - [http://www.psychocats.net/](http://www.psychocats.net/) 
Very informative for people just getting started.

---

### Post by Nathan Sweeney on 2008-12-05
> **ciananh said:**
> i was giving an example of what i saw. i'm sure it didn't say all the gibberish i typed, but god bless if it didn't look like it to my eyes.. ;)


i've been reading your "ubuntu's ultimate beginners guide". i've already caught on to a small hand full of things. i guess this will just take AWHILE to grasp and get ahold of. kind of like relearning to ride a bicycle, eh?


-------edit-------

i went to, uhmmm, this:

[http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&mirror=http%3A%2F%2Fubuntu-releases.cs.umn.edu%2F&arch=i386](http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&mirror=http%3A%2F%2Fubuntu-releases.cs.umn.edu%2F&arch=i386)

and got this:

[IMG]http://img.photobucket.com/albums/v648/x9ez6nc/Screenshot.png[/IMG]

at about 15%...

what is the "source file"? should i just try redownloading it, or do i need to activate something on the OS.


I'd recommend downloading via one of the torrents.  Despite what some people think, there are many legal uses for bittorrent, and since Ubuntu is free, downloading via bittorrent is 100% legal, and in fact better than downloading directly from the server:
-Saves Ubuntu servers bandwidth (you are downloading from other users)
-Downloads can pause and resume
-Built in error checking.  If you download from the server, you'll need to check that the md5sums match to be sure that your download didn't get corrupted.

The current version of Ubuntu is 8.10 "Intrepid Ibex" (supported until 2010) while 8.04 "Hardy Heron" is a LTS (Long Term Support) release (it will be supported until April 2011).  You have 7.04 "Feisty Fawn", which is no longer supported.

Also, what are the specs on your computer?  There are 32 bit and 64 bit versions.  The 32 bit version would be fine on any machine, while if you have a 64 bit machine, the 64 bit version supports more RAM (32 bit will only recognise ~3.5 GB, so if you have 4 or more, go with 64 bit)

It might take a while to get used to ubuntu and linux in general, but it is a great OS.  If you are coming from windows, you may want to check out Kubuntu, which is affiliated with ubuntu and is the same basic OS, but uses the KDE desktop instead of Ubuntu's gnome (or Xubuntu's lighter-weight Xfce).  You can always get Ubuntu, and change to the kubuntu or xubuntu desktop with the commands
```
sudo apt-get install kubuntu-desktop
or
sudo apt-get install xubuntu-desktop

```

Good luck, and have fun.

---

### Post by Sorivenul on 2008-12-05
A couple of other helpful links:
[Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm") - A great article for those making the switch.
[LinuxCommand.org]("http://linuxcommand.org/") - Helping decipher the command-line "gibberish".

---

### Post by sofasurfer on 2008-12-05
A great beginners guide...
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

And of coarse [http://www.ubuntu.com/](http://www.ubuntu.com/) for downloading latest versions of Ubuntu (currently Intrepid Ibex otherwise known as Ubuntu 8.10) and documentation, etc.

---

### Post by jsprz8382 on 2008-12-05
-------edit-------

i went to, uhmmm, this:

[http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&mirror=http%3A%2F%2Fubuntu-releases.cs.umn.edu%2F&arch=i386](http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&mirror=http%3A%2F%2Fubuntu-releases.cs.umn.edu%2F&arch=i386)

and got this:

[IMG]http://img.photobucket.com/albums/v648/x9ez6nc/Screenshot.png[/IMG]

at about 15%...

same happened to me the first 2 times I tried installing it via CD I used wubi instead.

what is the "source file"? should i just try redownloading it, or do i need to activate something on the OS.[/QUOTE]

---

### Post by ciananh on 2008-12-09
thanks for the tutorials and links guys...:p

---

### Post by abhilashm86 on 2008-12-09
> **ciananh said:**
> i'm a new ubuntu user. new, as in, i formated my hard drive less than 20 hours ago and installed linux's ubuntu 7.04 OS. whoa, man... is this a change. i used window's OS for a good solid 8 years. windows is all i know, and this is definatly a 'culture shock' to say the least.

i have absolutely no clue as to what i'm doing. how would a 'noob' to linux go about a OS like this? i try to download programs, but i can't extract the .exe files. are there even .exe files in linux? i googled a tutorial on how to extract programs and what not, but all i got was abunch of code. something  like this:

~s/kajsdhfk/asdlhf.akjsdhfk/kjashdf   - what do i do with this code?

i just have no clue how to get around on this bad boy. i definatly love the change, i would just like some input on what things i should do to optimize this OS. and, like, where is the controller panel, and 'program files' and stuff.

):P

thanks abunch

basically .exe files from windows cannot be ran in ubuntu directly,download wine,using wine u can run all the .exe files
procedure is-in applications->wine->browse c: drive, u mount the required .exe files and wine automatically runs the program for u
reply after u give a try

---

### Post by BobSutan on 2008-12-15
Great thread. This is exactly the sort of thing I've been looking for.

---

### Post by nordmichael29 on 2008-12-16
Ok first off download and install ubuntu 8.04 or 8.10, your choice, both work quite well. to install programs in ubuntu all you have to do is in the top bar, go to Applications and then click Add/Remove (instructions like this are usualy presented in the Application/Add/Remove format.). that one took me a bit of time to figure out, .exe's won't work in ubuntu because /exe is a windowz only executable, to download and install software for linux look for the .deb extension (or just go to applications). all of the 'program files' like things are found in the application bar somewhere, (top left hand corner by default). if you have questions about changing themes, or anything else I recommend you first do a google search, and then if don't find anything useful to you post something on the forums. learning a new OS is hard for the first couple of weeks, stick with it and it's very rewarding.
Michael.

---

### Post by samden on 2008-12-16
If you're having that much trouble downloading the .iso, download BitTorrent (the Windows app is here):
[http://www.bittorrent.com/btusers/download/?](http://www.bittorrent.com/btusers/download/?)

Then download the bittorrent "seed" file for the .iso that you want from here:
[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)
You want either the 8.04 or 8.10 "desktop-i386.iso.torrent" file.

The bittorrent program can then download the .iso file for you using that seed file. This will be faster than downloading it from the central server and will be more reliable too, you shouldn't get the error you've been getting.

---

### Post by samden on 2008-12-16
By the way, forget everything you think you know about computers (such as .exe files) based on using that inferior product Windows! It's a steep curve initially from Windows to Linux but well worth it. 

Once you get used to it you'll find things (in general!) easier to do on Linux than Windows. In Windows, if you want to install software, you have to hunt all over the net for the right .exe file, download it, and install it manually. In Ubuntu you just open up "Add/Remove Applications", select the application you want and click ok. It is much simpler - but different.

---

### Post by poebae on 2008-12-16
> **ciananh said:**
> 
i went to, uhmmm, this:

[http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&mirror=http%3A%2F%2Fubuntu-releases.cs.umn.edu%2F&arch=i386](http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&mirror=http%3A%2F%2Fubuntu-releases.cs.umn.edu%2F&arch=i386)

and got this:

[IMG]http://img.photobucket.com/albums/v648/x9ez6nc/Screenshot.png[/IMG]

at about 15%...

That's simply a matter of the communication between your communication and the file server going bung during your download.

You can either try downloading the file again, or maybe find a different mirror from which to download the ISO.

Good luck!

---

### Post by Slim Odds on 2008-12-16
> **jsprz8382 said:**
> -------edit-------

i went to, uhmmm, this:

[http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&mirror=http%3A%2F%2Fubuntu-releases.cs.umn.edu%2F&arch=i386](http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&mirror=http%3A%2F%2Fubuntu-releases.cs.umn.edu%2F&arch=i386)

and got this:

[IMG]http://img.photobucket.com/albums/v648/x9ez6nc/Screenshot.png[/IMG]

at about 15%...

same happened to me the first 2 times I tried installing it via CD I used wubi instead.

what is the "source file"? should i just try redownloading it, or do i need to activate something on the OS.

More likely, you're out of space on one of the partitions. If it keeps stopping in the same place all of the time.

---

### Post by ripsometime on 2008-12-19
how did i get here, by the way i have ubuntu installed alongside windows xp on the same hard drive, but i don't even know how i got to this forum but it has been a great help, i seriously just appeared here and didn't know if i had an account, i tried a random account name and pass that i normally use and it worked and i was like WTF, anyway great topic, covers a lot of beginners questions, the only reason i have windows is that i cant be bothered getting my windows games to work with wine, anyway thanks for the help.:lolflag:

---

### Post by go_beep_yourself on 2008-12-24
> **ciananh said:**
> i'm a new ubuntu user. new, as in, i formated my hard drive less than 20 hours ago and installed linux's ubuntu 7.04 OS. whoa, man... is this a change. i used window's OS for a good solid 8 years. windows is all i know, and this is definatly a 'culture shock' to say the least.

i have absolutely no clue as to what i'm doing. how would a 'noob' to linux go about a OS like this? i try to download programs, but i can't extract the .exe files. are there even .exe files in linux? i googled a tutorial on how to extract programs and what not, but all i got was abunch of code. something  like this:

~s/kajsdhfk/asdlhf.akjsdhfk/kjashdf   - what do i do with this code?

i just have no clue how to get around on this bad boy. i definatly love the change, i would just like some input on what things i should do to optimize this OS. and, like, where is the controller panel, and 'program files' and stuff.

):P

thanks abunch

.exe files are windows executable file. They are made for Winblows. Your only chance of getting them work work is running them wine, and that may or may not work or run buggy. I have utorrent a few others working flawlessly under wine. If you go to the utorrent download page and read, it says utorrent works in wine. However, you do not need utorrent in Wine because Linux has its own torrent clients. The same with most other windows software. They have Linux equivalents that usually do it better than the windows software. What programs are you needed? I can tell you which good Linux apps do the same in Linux. Recently I started to use newsgroups instead of torrents, but Ktorrent has always worked good, full of great features and newer versions of Deluge are looking good. Another way if you have at lease 1 gb ram, the more the better, you can use VMware workstation with Unity. It will run all windows software flawlessly except for newer games because vmware emulates a weeks graphic card. Wine and Cedga are your best bet for getting windows games running under linux. Check the winehq website for their application database to see if your game will run. Cedega has something similar. BTW, why are you using Ubuntu 7.04. You should be using the latest stable release 8.10. Each release usually gets better.

---

### Post by go_beep_yourself on 2008-12-24
There's a few things you can do to clear up space on your drive.

1) add a new hard drive of course

2) sudo apt-get clean

3) delete the files in /tmp

4) use 7za without highest compression ratio to compress your files

---

### Post by j@am1 on 2008-12-28
A couple of things to say:
bill- gj on that little page.and ty for even bothering. That's how a how-to/tutorial SHOULD be written for beginners. Few things are more frustrating for folks wanting to switch over to Linux (any distro) than discovering that they now need to spend days or even weeks scouring the net for vague,obscure "documentation" on how to do some of the simplest of tasks in Linux. Developers really should spend another few minutes including documtentation or how-to's for thier apps,that assume the user is new,and provide an "ok,start from here" point.
Of the gazillion such items a new person finds,they almost all assume some level of existing Linux experience,if not the assumption that user is already some kind of command-line guru.

Further,they should include WHERE to enter a given command,and how to start or get into the needed directory to execute it. 90% of the time,the documentations simply say "enter: -fgigtmrtotrtty", or whatever the heck. Provided the new user even figures out or locates a terminal to enter the command into,he usually ends up with a slew of errors,or "no such commands" crap. And even if he succeeds in doing it correctly somehow,the output usually looks-to a new user-like it might as well be written in Martian for all the good it does them.

This single aspect of Linux alone is the biggest hurdle for new users (once they work thier way past figuring out which distro to try to use).And,frankly,99% of your average computer-users lack the time,patience or inclination to sit through hours or days of pulling thier hair out searching for how-to's or deciphering command-line geekdom. They just want to turn the thing on,open and app and begin doing thier thing. And that really shouldnt be too much to ask for....

As for installing apps,sure it's come a long long way from a few years ago,but... 

"By the way, forget everything you think you know about computers (such as .exe files) based on using that inferior product Windows! It's a steep curve initially from Windows to Linux but well worth it. 

Once you get used to it you'll find things (in general!) easier to do on Linux than Windows. In Windows, if you want to install software, you have to hunt all over the net for the right .exe file, download it, and install it manually. In Ubuntu you just open up "Add/Remove Applications", select the application you want and click ok. It is much simpler - but different."


um....yes and no. And here's a silly,but personal and frustrating example. I wanted to mess with Second Life in Linux on one of my Ubuntu boxes,since it runs like complete crap in Windows. So,I go to the Add/Remove,Synaptic,all of them, and cannot find it anywhere. So I go instead to the SL site and download the the game from there. Now,looking at the readme file for it,and posts about installing it on various forums,etc. It tells you u simply extract it into a folder, then either click on it (while failing to mention exactly what "it" is,when there are about 2.5 million folders and files the come out)or perform a command on a command-line from within the directory.(um...there's no terminal or option to open one in some of the file managers) 
Because none of the 2.5 million files or folders indicate anything that actually "launches" the app,and since the included Icon doesnt actually open it either-(it just opens in an image viewer),there's no way for the new user to know how to start the darned thing short of going down the list and clicking every single thing until something launches...This method of installing outside of using one of the package managers does NOT place an applet or icon or any such thing in any of the applications menus. 

So his question-as a new user-is very valid. Why can Linux not make some kind of common executable or some icon with a link to such an executable to make so simple a task as this...well..simple? Really,now, it doesnt seem like too much to ask...

---

### Post by Nathan Sweeney on 2008-12-28
> **j@am1 said:**
> 
So his question-as a new user-is very valid. Why can Linux not make some kind of common executable or some icon with a link to such an executable to make so simple a task as this...well..simple? Really,now, it doesnt seem like too much to ask...

I may get flamed on this point, but I really like the way that Mac OS X handles the installation of applications.  On the Mac, you just download the dmg file (a compressed disk image), and open it.  Inside is your application, a *.app file.  Just drag the file and drop it into the Applications directory.  That's it.  To open it, you just double click the .app file, and you can drag it onto the dock for quick and easy access, or the way I launch apps is to type command (apple key) space, which activates spotlight search.  Type in the first few letters, and hit enter, and it launches.  To uninstall, you just drag the .app to the trash and empty it.

Where it gets really cool, in my mind, is when you look at what exactly the .app file is.  It's not an executable, rather it's just a folder with the .app suffix appended to the end of the name.  If you right click and explore the file, you see all the little files like you describe with second life.  You just don't have to deal with them if you don't want to, but they are there if you so desire.

OS X is a unix based system, so I don't see why something like this couldn't be implemented within a given linux distro.  Don't get me wrong, I love apt and it is a great tool, but it can be frustrating if you want something that is not available in the repos, then trying to install it manually can be a pain.

---

### Post by steveneddy on 2008-12-28
I didn't read the entire thread, but I will offer this advise.

First of all, please install version 8.04 if it is possible because it gives the most up to date software available that is supported for at least three years.

Version 8.04 is called the Long Term Support version. It is called Hardy by name.

Ok - check out the first two links in my sig. They will help you a lot.

.exe files cannot be launched or installed in Linux. 

Remember that Linux is not Windows. By using Linux you have entered the world of computers where you will realize the actual power of your PC and your knowledge of computers will increase. Linux has power that Windows users only think they have.

The first thing after upgrading to 8.04 I would suggest lurking in the forums and reading lots of threads so help you understand more of the new OS that you are using.

Please only post one thread for one issue.

Good Luck. Hope you find it enjoyable.

---

### Post by j@am1 on 2008-12-28
Yes,we get all that. And is even one of the reasons many of us come over from the Dark Side (Ages).BUT...that is exactly the kind of answer that isnt helping new folks who are interested and willing to give this a shot. Yes,eventually, a lot of us will end up delving deeper into the workings of our new OS. But why blow off/scare off/run off all newcomers with a mind-boggling array of such things from the outset? 
It's all well and good if folks have all kinds of spare time to invest in doing so,and many will end up becomming interested enough to learn as much as they can anyway. But why not make the transition a bit less daunting,and a LOT more inviting-to let them sort of wade in first,before having to dive off the deep end from minute one?

---

### Post by duds2008 on 2008-12-30
In my experience no matter what you do in this world, if you do it for a long time, you tend to get good at it. You have already started solving your problem by searching through these forums. Good luck!:D

---

### Post by Slim Odds on 2008-12-30
> **Nathan Sweeney said:**
> I may get flamed on this point, but I really like the way that Mac OS X handles the installation of applications.  On the Mac, you just download the dmg file (a compressed disk image), and open it.  Inside is your application, a *.app file.  Just drag the file and drop it into the Applications directory.  That's it.  To open it, you just double click the .app file, and you can drag it onto the dock for quick and easy access, or the way I launch apps is to type command (apple key) space, which activates spotlight search.  Type in the first few letters, and hit enter, and it launches.  To uninstall, you just drag the .app to the trash and empty it.

What is it that you find difficult with .deb files? They package the entire application as a single file. You can install and uninstall them very easily.

Every OS has it's own way to doing things. Ubuntu is actually one of the best since it's based on the debian packaging system, which is pretty solid.

---

### Post by psychomichael on 2008-12-31
> **nordmichael29 said:**
> Ok first off download and install ubuntu 8.04 or 8.10, your choice, both work quite well.

That's quite a bit misleading, isn't it when you consider these threads:

[http://ubuntuforums.org/showthread.php?t=963853](http://ubuntuforums.org/showthread.php?t=963853)
and
[http://ubuntuforums.org/showthread.php?t=768200](http://ubuntuforums.org/showthread.php?t=768200)

I would suggest using 7.10 which has overwhelmingly been accepted as the best Ubuntu available, even if it's not going to be "supported" soon.

Why fix what isn't broken?

---

### Post by hatboysam on 2008-12-31
I know the feeling, Linux is intimidating and in the past year I'm only starting to really get the hang of everything.

For starters:  .exe is Windows only
For Linux applications, check out synaptic package manager
In linux programs are installed through packages that come from repositories

Also do your best to learn how to use the command prompt early (that's Terminal) it can do anything in Linux and will be a part of any tutorial you read

---

