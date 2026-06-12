---
title: "Problems with Adobe AIR on Ubuntu 8.10"
date: 2009-03-13
forum: General Help
---

### Post by Neroli on 2009-03-13
Hi there, I'm new to this forum (obviously), so if I've posted in the wrong place, feel free to move this thread.

I installed Ubuntu 8.10 as my OS a couple of weeks ago because I was sick of Windows, and both my brother and mum use 8.10 so I thought, 'Why not?' However, since then I've been having a multitude of problems--some of which I've been able to solve simply by searching Google, while others I don't know how to fix.

The latest issue is with Adobe AIR. I don't know exactly what I did to cause this problem (I was dealing with some serious compiz malfuntions prior to this and had to resort to the failsafe terminal to remove certain things before I was able to log into Ubuntu), but basically programs which run on AIR just aren't working properly. I uninstalled Adobe AIR and reinstalled using [[color=red]this tutorial[/color]](http://linuxondesktop.blogspot.com/2008/12/installing-adobe-air-and-some.html), to no avail. TweetDeck, for example, is completely blank when I launch it (see [[color=red]this picture[/color]](http://img6.imageshack.us/img6/3779/screenshotyuk.png)--when I click the buttons along the top, nothing happens; can't log in, can't alter settings). and when I install and try to run ReadAir I get [[color=red]this[/color]](http://img26.imageshack.us/img26/1889/screenshot1pno.png).

I'm relatively new to Linux (having only dabbled in 8.10 when at my mum's and brother's houses) so I don't know what information people might need to help me out. If there are system specs or whatever that would make it easier to find out what's wrong, please ask and I'll provide them ASAP.

Thanks in advance.

---

### Post by mtmercydave06 on 2009-03-23
You're not alone, I'm having the same or a similar problem.  I installed Adobe AIR correctly and it came up as being successfully installed, but when I try to install TweetDeck I see the getting ready to install box pop up but it closes before finishing installing any apps.  I tried twhirl and tweetdeck with no success.

Not quite sure what the problem is.

David

---

### Post by Neroli on 2009-03-23
Hi David, thanks for replying.

I've been scouring the web trying to find some answers but I still haven't had any luck. Someone linked me to this support page but even after following the steps, I'm still having issues. [http://blogs.adobe.com/air/2008/12/tips_on_resolving_application.html](http://blogs.adobe.com/air/2008/12/tips_on_resolving_application.html)

A number of friends have recently moved to 8.10 and reported the same problem from the get-go, yet I--and a few people I know--managed to run AIR just fine until one day it randomly stopped working. It's supposedly not supported with the current distro, but it seems strange that it would work for some and not for others.

Hopefully we can resolve this soon! It's too hard to keep up with Twitter when I don't have TweetDeck sorting all my @replies ;)

---

### Post by mtmercydave06 on 2009-03-23
Yeah I know what you mean.  I love Tweetdeck but in the meantime I've been using the Twitterbin addon to firefox until the Adobe AIR problem gets resolved.  Twitterfox is another good firefox addon.  I know they're not as good as Tweetdeck, but as of right now that's the only thing I can get to work that avoids Adobe AIR.

David

---

### Post by nyiti on 2009-03-25
I'm probably in the same boat with you, Adobe AIR 1.5.1 installs, but when I try to install any .air app, it throws segmentation fault.

The file browser opens, I select the .air, the install window flashes up for a moment and then segfaults. Maybe it's some sort of environmental issue?

What does AIR depend on? Say, does it use the flash plugin at all?

---

### Post by rajatm on 2009-03-26
Hi all, 
     
       Air requires keyring daemon to be running before any application accessing it is launched . So just make sure that its running.

Running gnome-keryring-daemon in case your desktop environment is Gnome and keywallet (in case of KDE) would solve your issue.
So start the daemon process and after that launch the application. I think it should work after that.

---

### Post by nyiti on 2009-03-27
> **rajatm said:**
>      
       Air requires keyring daemon to be running before any application accessing it is launched .

Thx for the tip, it is running though:
```
tsukimi@thousandth:~$ ps aux |grep keyring
tsukimi   6618  0.0  0.0  14700  2004 ?        S    06:54   0:00 /usr/bin/gnome-keyring-daemon -d --login
tsukimi   6701  0.0  0.1  13916  3632 ?        S    06:54   0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
tsukimi   7818  0.0  0.0   3236   792 pts/0    R+   07:03   0:00 grep keyring
```

Maybe some libs are not where AIR expects them?

Rajatm, are you running Ubuntu? Are AIR apps working for you?

---

### Post by syed mehdi on 2009-03-27
Your ubuntu is 32-bit or 64-bit.
If its 64-bit, then please install these libraries to get it working. Execute these commands on terminal:
sudo getlibs -l libgnome-keyring.so
sudo getlibs -l libgnome-keyring.so.0
sudo getlibs -l libgnome-keyring.so.0.1.1

if its 32-bit, then please file a bug along with steps at: [http://adobe.com/go/wish](http://adobe.com/go/wish)

Regards
Syed

---

### Post by mtmercydave06 on 2009-03-27
I have the same problem as you nyiti but I don't get a segmentation fault.  Whenever I try to install an app the dialog pops up to install and goes away quickly without it installing, and without an error.

Also checked to see if gnome-keyring-daemon is running, and it is.

David

P.S. Upgraded to the 9.04 Beta today to see if it would resolve the problem, and nope still has the same problem.

---

### Post by bruseleno on 2009-03-27
I had no problems with the install of Adobe Air, TweetDeck and Twihrl in Ubuntu 8.10, but I think the install has screwed up my QT libraries and now a [lot of programs won't run]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/115970") (virtualbox, skype, lastfm,...)

How did I install it? I just clicked on the Install now banner in Tweetdecks homepage. A pop up asked for permision to install, another one asked for the password for administrative tasks, another one asked where did I want to install and gave some options and that was it. I just had to watch it being installed and the program runs perfectly.

---

### Post by mtmercydave06 on 2009-03-31
I used the install banner as well on the tweetdeck homepage.  Now I click it and it gets the tweetdeck file and asks me if I want to open or save it.  I click open and then a window pops up saying getting ready to install and goes away quickly, without a crash message or anything.

I'm running 8.10 as well, and installed the Adobe Air 1.5.1 version from the adobe website.

David

---

### Post by chris.h on 2009-03-31
I have the same problem here on ubuntu64. I installed the libgnome-keyring files but to no avail. 

Twhirl and destroy twitter launch (sometimes twhirl does and sometimes it doesn't) but neither will authenticate.

---

### Post by mtmercydave06 on 2009-03-31
Ahh I'll have to try Destroy Twitter.  Tried Twhirl and Tweetdeck and they didn't launch at all.  I'm actually not even sure they installed because I don't get that notification.

I ended up using Twitux for now.  That seems to be the best non Adobe Air client I've found so far.  If anyone else knows of any non Adobe Air twitter clients that work in Linux that would be great to know as well.

David

---

### Post by rajatm on 2009-04-01
> **nyiti said:**
> Thx for the tip, it is running though:
```
tsukimi@thousandth:~$ ps aux |grep keyring
tsukimi   6618  0.0  0.0  14700  2004 ?        S    06:54   0:00 /usr/bin/gnome-keyring-daemon -d --login
tsukimi   6701  0.0  0.1  13916  3632 ?        S    06:54   0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
tsukimi   7818  0.0  0.0   3236   792 pts/0    R+   07:03   0:00 grep keyring
```

Maybe some libs are not where AIR expects them?

Rajatm, are you running Ubuntu? Are AIR apps working for you?

Yes applications are working for me.
To check out the problem i installed ubuntu 8.10 32 bit and istalled tweetdeck as docuemented here [http://www.tweetdeck.com/beta/](http://www.tweetdeck.com/beta/)

Everything worked great. No dependencies nothing.

---

### Post by Oceanwatcher on 2009-04-06
I installed Air and Twhirl on Kubuntu 9.0 beta without any problems.

BUT - if you run desktop effects and nVidia driver 180, you will have problems with Twhirl. So I am not running that yet. Hoping for a better release of the nVidia driver soon.

---

### Post by rhuann on 2009-06-03
i am using ubuntu 9.04 32bits, and having exaclty same problem, when i run twhirl it appear and quickly disapper, and it happens with every application at adobe air. with twhirl i did some progess, i ask to a friend install in his linux fedora and was normal, it runs normaly, i ask to him send-me the twhirl folder, when i try to run it runs normaly, i put my user name and password, when it will show the screen with tweets and stuffs, disappear...looks like it try to call a another air app from twhirl and fails, no error throws...just segment fault...

any ideas?


//i dont know if i was clear, but my english sux

---

### Post by Neroli on 2010-03-07
Er. I forgot my forum login details and consequently haven't been here in a while...

I tried the options suggested in this thread with no joy. Even having upgraded to 9.04 and later 9.10, I never managed to get TweetDeck to work. Twhirl, meanwhile, which also runs on AIR and has a generally less-cluttered interface than TweetDeck, works perfectly.

I haven't solved the problem for myself, but I have found an alternative solution - use twhirl instead!

---

