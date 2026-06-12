---
title: "I need a picture/photo management program"
date: 2009-05-27
forum: General Help
---

### Post by Hansmc on 2009-05-27
I need a picture/photo management program for Ubuntu

My requirements are modest (I thought):
(1) No import or anything like that (just browse and manipulate my pictures where ever they are. This is important, because I am often working with pictures on an external disk or that are part of another project so need to be stored with them).
(2) Let me access the printer settings (all of them, so I can turn on auto duplexing, etc). (Why is there so many Ubuntu programs that do not let you access the printer settings?)

Some other things would be nice but these are the things that I have not been able to find in one program. I have tried quite a few different ones, but nothing has worked for me yet. On windows I have used FastStone and XnView. Both work great.

Any ideas? Thanks.

---

### Post by albinootje on 2009-05-27
> **Hansmc said:**
> On windows I have used FastStone and XnView.

There's f-spot included in Ubuntu, and there's the closed-source Google Picasa, but see here :

[http://newsgroup.xnview.com/viewtopic.php?t=16416](http://newsgroup.xnview.com/viewtopic.php?t=16416)

Download it, extract it into your home directory, open a terminal, cd into the extracted directory and run "./xnview.sh".
It's an early version, but looks much better than the older Linux version of it. See attached screenshot.
You might want to join the development of the Linux version by giving feedback to the author(s).

---

### Post by albinootje on 2009-05-27
And see the right column of this page : [http://photobuntu.wordpress.com/category/ubuntu/](http://photobuntu.wordpress.com/category/ubuntu/)
Did you try all of those already ?

---

### Post by philcamlin on 2009-05-27
gimp and f spot are both included in ubuntu

---

### Post by albinootje on 2009-05-27
See also this thread : [http://ubuntuforums.org/showthread.php?t=337213](http://ubuntuforums.org/showthread.php?t=337213)

This one looks interesting : [http://mapivi.sourceforge.net/mapivi.shtml](http://mapivi.sourceforge.net/mapivi.shtml)
I'm curious about this topic, because a colleague asked me to install jbrout because f-spot was not good enough, and installing/using jbrout was not so easy on Ubuntu. So.. keep me updated :)

---

### Post by Hansmc on 2009-05-27
It has been awhile since I tried digiKam. Do you have to import photos to use it, or can you just browse photos in your file system?

I think I will check out that xnview for Linux.

I use gimp all the time. F-spot does not meet requirement number one.

---

### Post by albinootje on 2009-05-27
> **Hansmc said:**
> It has been awhile since I tried digiKam. Do you have to import photos to use it, or can you just browse photos in your file system?

I just tried digiKam 0.10 in Jaunty. You need to import photos into albums from folders, I didn't see a way to just browse folders. (Gqview is my fav. image viewer by the way).

---

### Post by Hansmc on 2009-05-27
Found this [http://ubuntuforums.org/showthread.php?t=71530](http://ubuntuforums.org/showthread.php?t=71530), but need more help installing mapivi.

Gqview is a nice little application, only does not meet requirement number two.

---

### Post by ronparent on 2009-05-27
You also can get picasa for linux from google. It handles most picture format including raw. Besides having modest but decent editing capabilties it also does a decent job of organizing. What I like is that the picture can be edited while making no actual changes to the original picture file.

---

### Post by cdude on 2009-05-27
_[gthumb]("http://gthumb.sourceforge.net/")_ is probably what you need. no import.

for more gnome apps go to _[gnomefiles]("http://www.gnomefiles.org/index.php")_ "Graphics & Design chatogory"

---

### Post by Hansmc on 2009-05-27
gthumb does not meet requirement number two.

To install mapivi:
Open Synaptic package manager and search for it. (Simple)
To Run: Open terminal and type mapivi.

It does not work! I can browse my file system but can not see any thing in them.


PS I found out if I double click on a file with pictures in it, it will say "there are 5 non-JPEG pictures in directory [name] Should I convert these to JPEG format?" How nice it ask. But no, do not touch my files!

Thanks for your help

---

### Post by spcwingo on 2009-05-27
If you have Wine installed I would recommend Irfanview.  If you want to try Irfanview just use version 4.10 as that is the last version I have been able to get going in Wine.

---

### Post by fuzzmo on 2009-05-28
> **spcwingo said:**
> If you have Wine installed I would recommend Irfanview.  If you want to try Irfanview just use version 4.10 as that is the last version I have been able to get going in Wine.

I have got the latest version (4.23) working fine in Wine - you need mfc42.dll in your system32 directory and then you need to edit the .ini file in the Irfanview directory and comment out everything in the toolbar section.  Works like a charm!

Check out below (post number 2 which links to the Wine thread) for the proper details:

[http://en.irfanview-forum.de/vb/showthread.php?t=3959](http://en.irfanview-forum.de/vb/showthread.php?t=3959)

---

### Post by spcwingo on 2009-05-28
> **fuzzmo said:**
> I have got the latest version (4.23) working fine in Wine - you need mfc42.dll in your system32 directory and then you need to edit the .ini file in the Irfanview directory and comment out everything in the toolbar section.  Works like a charm!

Check out below (post number 2 which links to the Wine thread) for the proper details:

[http://en.irfanview-forum.de/vb/showthread.php?t=3959](http://en.irfanview-forum.de/vb/showthread.php?t=3959)

Thanks fuzzmo, it worked like a charm.  :biggrin:

---

### Post by Hansmc on 2009-06-03
What I have found so far. 

Requirements:
(1) No import (directory browsing)
(2) Let me access the printer settings

Applications I tested and the results:
f-spot - does not meet req. 1
digiKam - does not meet req. 1
mapivi - could not get to work
GThumb Image Viewer - does not meet req. 2
Mirage - does not meet req. 1 & 2
Geeqie - does not meet req. 2
Phatch Photo Batch Processor - does not meet req. 1 & 2
GQview - does not meet req. 2
XnView for linux - could not get to work
XnView portable in wine - does not meet req. 2 (it lets me access the printer settings but they do not seem to have any affect on what is actually printed.)
gimp - not a photo management tool

Not Tested:
KPotoAlbum
jBrout
picasa

Right now I am using XnView portable in wine, just have to boot to windows every time I want to print something with duplexing (which is most of the time). Linux did a bad thing letting programs control there own printer settings. I will keep working at testing a few more programs, but it takes a long time. I have come to the conclusion, if a program is not in the "Add/Remove..." thing or package manager you might as well plain on 5 to 8 hours of searching and reading forms, to try and make it work. But as you can see, even that has not been very successful for me. Thanks for your help.

---

### Post by Mirge on 2009-06-03
> **Hansmc said:**
> What I have found so far. 

Requirements:
(1) No import (directory browsing)
(2) Let me access the printer settings

Applications I tested and the results:
f-spot - does not meet req. 1
digiKam - does not meet req. 1
mapivi - could not get to work
GThumb Image Viewer - does not meet req. 2
Mirage - does not meet req. 1 & 2
Geeqie - does not meet req. 2
Phatch Photo Batch Processor - does not meet req. 1 & 2
GQview - does not meet req. 2
XnView for linux - could not get to work
XnView portable in wine - does not meet req. 2 (it lets me access the printer settings but they do not seem to have any affect on what is actually printed.)
gimp - not a photo management tool

Not Tested:
KPotoAlbum
jBrout
picasa

Right now I am using XnView portable in wine, just have to boot to windows every time I want to print something with duplexing (which is most of the time). Linux did a bad thing letting programs control there own printer settings. I will keep working at testing a few more programs, but it takes a long time. I have come to the conclusion, if a program is not in the "Add/Remove..." thing or package manager you might as well plain on 5 to 8 hours of searching and reading forms, to try and make it work. But as you can see, even that has not been very successful for me. Thanks for your help.

5-8 hours to install a program because it isn't in repositories? I haven't run into that yet. Launchpad is also worth checking if not in repositories. And Linux did a bad thing by letting programs have control? C'mon.

---

### Post by Hansmc on 2009-06-03
> **Mirge said:**
> 5-8 hours to install a program because it isn't in repositories?

Sorry, not just install, but to install and try to get it to work. I do not have a lot of experience at compiling and finding out what else needs to be installed, so I have to look up every step of the way and then it usually does not work in the end. If there is a package all made up for Ubuntu this is not true. Would you please make one with xnview for us?

> **Mirge said:**
> Launchpad is also worth checking if not in repositories.

Thanks, I will keep that in mind for when I have time to learn something new. (I have a few other things to try and figure out how to fix on Ubuntu first, like losing all usb devices on wake)

> **Mirge said:**
> And Linux did a bad thing by letting programs have control? C'mon.

Sorry, that is not true, BUT all programs should let you open the printer settings dialogue box and adjust any printer settings that you want there. However, most just let you adjust a few things (like margins and page size) in a custom tab or dialogue box. So if your printer has other settings that you would like to change you are just out of luck. If they would all use the same dialogue box made by/for the printer, that would have saved me all this problem and would save the programmers having to make there own. I am not a programmer so maybe this is all not true, but that is how it looks from a user prospective.

---

### Post by Mirge on 2009-06-03
> **Hansmc said:**
> Sorry, not just install, but to install and try to get it to work. I do not have a lot of experience at compiling and finding out what else needs to be installed, so I have to look up every step of the way and then it usually does not work in the end. If there is a package all made up for Ubuntu this is not true. Would you please make one with xnview for us?



Thanks, I will keep that in mind for when I have time to learn something new. (I have a few other things to try and figure out how to fix on Ubuntu first, like losing all usb devices on wake)



Sorry, that is not true, BUT all programs should let you open the printer settings dialogue box and adjust any printer settings that you want there. However, most just let you adjust a few things (like margins and page size) in a custom tab or dialogue box. So if your printer has other settings that you would like to change you are just out of luck. If they would all use the same dialogue box made by/for the printer, that would have saved me all this problem and would save the programmers having to make there own. I am not a programmer so maybe this is all not true, but that is how it looks from a user prospective.

I can certainly understand your frustration, I just haven't run into those same frustrations you have, but I guess we don't exactly do the same things either.

I forgot to include the URL to launchpad, it's [https://launchpad.net/](https://launchpad.net/).

Example, I use geany for writing software in C, PHP, HTML/CSS, Javascript, etc. There was a new version released (0.17)... I grabbed 0.16 from Ubuntu repositories. I wanted 0.17... and I also wanted the "Addons" plugin. I tried compiling both from source and I couldn't get it to work. Then I slapped myself for not thinking about Launchpad first... went there & found both Addons AND Geany 0.17 for AMD64 binaries available in .deb format. Couple clicks later & I had both installed automagically. Flawless in that case.

---

### Post by Hansmc on 2009-06-03
Thanks, I will check launchpad.net out more. I added it to my bookmarks.

---

### Post by albinootje on 2009-06-03
> **Hansmc said:**
> Sorry, not just install, but to install and try to get it to work. I do not have a lot of experience at compiling and finding out what else needs to be installed, so I have to look up every step of the way and then it usually does not work in the end. If there is a package all made up for Ubuntu this is not true. Would you please make one with xnview for us?

Earlier in this thread I've described to you how to install Xnview. 

I've done this for you and other users, even though I prefer not to have closed source software on my own machines.

You didn't respond to that, you didn't come back with questions about it, and now... you're asking for a package.

Did you miss that comment, or what happened ?

---

### Post by Hansmc on 2009-06-03
> **albinootje said:**
> Earlier in this thread I've described to you how to install Xnview. 

I've done this for you and other users, even though I prefer not to have closed source software on my own machines.

You didn't respond to that, you didn't come back with questions about it, and now... you're asking for a package.

Did you miss that comment, or what happened ?

Thanks, I did get it installed by changing the latest rpm to a deb package. See [http://ubuntuforums.org/showthread.php?t=1172243](http://ubuntuforums.org/showthread.php?t=1172243). But it did not work. I tried a few things but gave up. I also downloaded the file you gave me the link to and extracted it but when I saw how old it was, I went to [http://www.xnview.com/en/downloadunix.html](http://www.xnview.com/en/downloadunix.html) and got the latest zip there. It that different then this? I figured there should be a lot of things fixed in the latest version so it should work better. I will give that another try and let you know what happens.

---

### Post by Hansmc on 2009-06-03
> **albinootje said:**
> Earlier in this thread I've described to you how to install Xnview. 

I've done this for you and other users, even though I prefer not to have closed source software on my own machines.

You didn't respond to that, you didn't come back with questions about it, and now... you're asking for a package.

Did you miss that comment, or what happened ?

It works, but there is no print option so does not help me out much. Also it is version 0.12. Could you make a new one with version 1.7? One other thing, will I always have to run "./xnview.sh" to start it? It looks so great, I am going to keep it and use it. Thanks

---

### Post by Mirge on 2009-06-03
You can create a launcher so you can point & click rather than open a terminal window & type it out

---

### Post by albinootje on 2009-06-03
> **Hansmc said:**
> It works, but there is no print option so does not help me out much. Also it is version 0.12. Could you make a new one with version 1.7? One other thing, will I always have to run "./xnview.sh" to start it? It looks so great, I am going to keep it and use it. Thanks

There's two different things here. The XnView MP is kind of a new project, or at least a rewrite of XnView.

The new project is in development.
[http://newsgroup.xnview.com/viewforum.php?f=60](http://newsgroup.xnview.com/viewforum.php?f=60)

And I've just tried XnView 1.70 again in Ubuntu, and now I remember why I wrote down instructions for the other (newer) one.

That old XnView version (from 2005) is build on Lesstif, and Lesstif was a nice toolkit to have many years ago, [when there were not that many open source (and free-of-charge) toolkits around], but.. it doesn't really give you the nicest interface to work with...

Also, I looked for the printer options in the menus and there's none.
I'm attaching a screenshot to show the printer interface. Perhaps you can look up commandline options to do what you want but.. it's not very "user-friendly" let's say.

Installation instructions, open a terminal and type or copy&paste the following :

```

cd ~/Desktop
wget -c http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz
tar xzvf XnView-x86-unknown-linux2.x-static-fc4.tgz
cd XnView-1.70-x86-unknown-linux2.x-static-fc4/
chmod +x install 
sudo sh ./install 
(ignore the errors about manual pages)
xnview 

```

---

### Post by blueridgedog on 2009-06-03
> **Hansmc said:**
> Linux did a bad thing letting programs control there own printer settings

I feel your pain.  Printing and sound in Linux is the least mature in my opinion.  However, they are WAY ahead of where they were just a few years ago.

---

### Post by albinootje on 2009-06-03
> **Hansmc said:**
>  On windows I have used FastStone and XnView. Both work great.

I just tried FastStone with Wine, the installation went fine, and so far it hasn't crashed.
Can you try it, and test the printer settings in there ?

And.. have you configured Ubuntu for printing duplex ? 

A few weeks ago a colleague used a program in Wine in Ubuntu, complained about not being able to print in duplex mode, and then it turned out the duplex mode was not set in the printing settings in Ubuntu.

---

### Post by albinootje on 2009-06-03
> **Hansmc said:**
>  Sorry, that is not true, BUT all programs should let you open the printer settings dialogue box and adjust any printer settings that you want there. 

I think you're being too harsh about Wine. 

Wine is a volunteer project which is more than 15 years old now, and has release Wine 1.0 only several months ago after working very hard all those years.

And what do you expect from a program-loader (Wine is not a PC-emulator like VMware,VirtualBox,Qemu etc.) which tries to load programs originally made for ... a proprietary OS.
 
See also here for some more information :
[http://wiki.winehq.org/Printing](http://wiki.winehq.org/Printing)
[http://en.wikipedia.org/wiki/Wine_(software](http://en.wikipedia.org/wiki/Wine_(software))

---

### Post by Hansmc on 2009-06-03
> **albinootje said:**
> There's two different things here. The XnView MP is kind of a new project, or at least a rewrite of XnView.

The new project is in development.
[http://newsgroup.xnview.com/viewforum.php?f=60](http://newsgroup.xnview.com/viewforum.php?f=60)

And I've just tried XnView 1.70 again in Ubuntu, and now I remember why I wrote down instructions for the other (newer) one.

That old XnView version (from 2005) is build on Lesstif, and Lesstif was a nice toolkit to have many years ago, [when there were not that many open source (and free-of-charge) toolkits around], but.. it doesn't really give you the nicest interface to work with...

Also, I looked for the printer options in the menus and there's none.
I'm attaching a screenshot to show the printer interface. Perhaps you can look up commandline options to do what you want but.. it's not very "user-friendly" let's say.

Installation instructions, open a terminal and type or copy&paste the following :

```

cd ~/Desktop
wget -c http://download.xnview.com/XnView-x86-unknown-linux2.x-static-fc4.tgz
tar xzvf XnView-x86-unknown-linux2.x-static-fc4.tgz
cd XnView-1.70-x86-unknown-linux2.x-static-fc4/
chmod +x install 
sudo sh ./install 
(ignore the errors about manual pages)
xnview 

```

I think I get it. XnView MP 0.12 is a different from XnView 1.7 so it has restarted numbering. Thanks

---

### Post by Hansmc on 2009-06-03
> **albinootje said:**
> I think you're being too harsh about Wine. 

Wine is a volunteer project which is more than 15 years old now, and has release Wine 1.0 only several months ago after working very hard all those years.

And what do you expect from a program-loader (Wine is not a PC-emulator like VMware,VirtualBox,Qemu etc.) which tries to load programs originally made for ... a proprietary OS.
 
See also here for some more information :
[http://wiki.winehq.org/Printing](http://wiki.winehq.org/Printing)
[http://en.wikipedia.org/wiki/Wine_(software](http://en.wikipedia.org/wiki/Wine_(software))

This has nothing to do with wine. It is the other native programs that I was talking about. In one of my other post I said that in xnview in wine I could get to a printer dialog box that would let me choose duplexing, but it never would indeed duplex. But that was a lest better then most of the native programs, that would not even give the option.

---

