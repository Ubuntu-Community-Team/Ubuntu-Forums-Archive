---
title: "I want to remove XP-but I bet no one knows a solution to all my problems!"
date: 2006-07-24
forum: Desktop Environments
---

### Post by lifeperfecti0n on 2006-07-24
I have been facing several problems for the last few weeks which has left me thinking perhaps computers are not for me! If someone-anyone (PLEASE!!) can solve my problems I will be grateful...but then again, as I said, no one knows a solution..! ](*,) 

**Problem #1 Alacarte**

OK This is a serious one..(at least to me) my menu bar has been messed up! I don't have any options for applications, no preferences, and no administration. Besides, I can't select any thing in alacarte, and if I apply the changes nothing happens (I don't know if I apply them or not-I mean there isn't any button for that is there?).This is a known issue-I tried all the workouts given on the following threads-but to no avail.
1. [http://www.ubuntuforums.org/showthread.php?t=220580&highlight=alacarte](http://www.ubuntuforums.org/showthread.php?t=220580&highlight=alacarte)
2. [http://www.ubuntuforums.org/showthread.php?t=163272&highlight=alacarte](http://www.ubuntuforums.org/showthread.php?t=163272&highlight=alacarte)
post#5,7,9(I use gnome not KDE)
3. [http://www.ubuntuforums.org/showthread.php?t=212236](http://www.ubuntuforums.org/showthread.php?t=212236)
For the last one, three menus did appear in applications, I again tried to 'revert to original settings' hoping everything would come again, but now I don't even have those three menus!
This is getting more and more serious gradually! Now I find I cannot open a program through Nautilus! Everything works on the terminal but if, lets say, I want to play an MP3, I double click and a message appears 'cannot display!'. Even if I click 'open with other application' no application is on the list! :mad: 
Please, please, people, tell me what to do! XP has already gone berserk (virus infection) and I work in Ubuntu these days. (I have some XP 'anti-monial' :evil: to relate-but later...this message will get too long)

**Problem #2 Creative Webcam Vista Pro**

Ok this is something I am pretty sure no one has a workaround for. I have this Creative webcam with bundled XP software (it was the only decent one available in my area-so don't give me that look) which isn't working on linux. I have followed these threads:
1.[http://www.ubuntuforums.org/showthread.php?t=191349&highlight=webcam+vista](http://www.ubuntuforums.org/showthread.php?t=191349&highlight=webcam+vista)
2.[http://www.ubuntuforums.org/showthread.php?t=194951&highlight=webcam+vista](http://www.ubuntuforums.org/showthread.php?t=194951&highlight=webcam+vista)
3.[http://www.ubuntuforums.org/showthread.php?t=167324&highlight=webcam+vista](http://www.ubuntuforums.org/showthread.php?t=167324&highlight=webcam+vista)
   I have successfully (I think) compiled the spca driver, but when I run camorama I get the error 'could not connect to device (/dev/video0) please check connection' In xawtv,spcaview I get similar errors. As for easycam, it just makes a text file asking me to e-mail the webcam model to an e-mail address! I did 'sudo touch /dev/video0 | ln -s /dev/usb/001/001 /dev/video0' but this also didn't work. Please also note that headers for kernel 2.6.15-26 have not been released yet so I am using kernel 2.6.15-23 for checking my webcam.

**Problem #3 Configuring proxy for some programs**

Can anyone please tell me where the .conf files for the following programs are located, and how to declare http_proxy for each file?
1. Evolution
2. VNC
3. Gaim (I am able to use MSN over http but not Yahoo/IRC-I get a 'proxy connection error 502')
I have tried declaring and exporting the http proxy through bash but this did not work-I am unable to 'ping www.google.com' [Error: 'Host not found']

**Problem #4 Sometimes synaptic and ubuntuforums don't work**

Yesterday, I wanted to post this thread, but [www.ubuntuforums.org](www.ubuntuforums.org) did not work! I could browse all other websites-I even checked my mail, but strangely enough, only this didnt work. At the same time, synaptic continued facing errors in applying upgrades-what is happening?
This one is not so important, ofcourse, but in Ubuntu, I like everything to work!
Update: I just recieved this error from synaptic:
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26-686_2.6.15-26.44_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26-686_2.6.15-26.44_i386.deb)
  404 Not Found
Any idea why this happened?


Oh, and if anyone knows how I can re-install dapper without having to re-install jave/flash/OO/gmplayer and other stuff please tell me how.

THANKS IN ADVANCE!!! :D

---

### Post by aysiu on 2006-07-24
Do you still have problem #1 even for a different user (if you don't have a different user, just create one--System > Administration > Users & Groups)?

Problem #4 had to do with the forums *and* Ubuntu's web server being down temporarily. Everyone experienced that, apparently.

---

### Post by lifeperfecti0n on 2006-07-24
I tried it, but no change.
Update: Installed gparted just now...its coming under administration in the system menu.

---

### Post by lifeperfecti0n on 2006-07-25
Hey people after all, ubuntu is about community-helping each other out-isn't it?? I am too sad that I have recieved only one reply uptil now to my problems-which are increasing slowly!
I am not able to open a single program without the terminal! E.g. if I click on an .odt file it just says 'couldn't display' and if i click open with other application no application is on the list! But this was just a tiny part of my growing problems..
OpenOffice is waaaay toooo slow! If I scroll to a page containing a picture-the whole system freezes for around 10 seconds before the 'picture toolbar' appears. Even if I disable that, scrolling through a .odt file full of pictures still remains a nightmare ](*,) 
I checked CPU usage-and Xorg was taking up 20-25% of CPU and 20 MB ram.
My system specs are:
PIII 1.0 Ghz 133Kb FSB
Intel D815EGEW Desktop Board
256MB ram
20 GB Hard Disk
[And I was not running Xgl by any chance [-( ]
PLEASE please please people reply....I want ubuntu to live up to its name!

---

### Post by lamego on 2006-07-25
lifeperfecti0n,
we can help but we can't do miracles.

Problem #1 Alacarte
It would help if you could provide some information on how did you get into this situation. Whatever happened was a result of some action on your side, knowing the action would make it easier to revert.

Problem #2 Creative Webcam Vista Pro
You think you have compiled the driver, but did you checked ? Did you tried to modprobe it ?

Problem #3 Configuring proxy for some programs
1. Evolution

2. VNC
I don't know any VNC application which supports http proxy (Linux/Windows).

3. Gaim (I am able to use MSN over http but not Yahoo/IRC-I get a 'proxy connection error 502')
Check your proxy configuration, gaim works fine with proxies.

I have tried declaring and exporting the http proxy through bash but this did not work-I am unable to 'ping www.google.com' [Error: 'Host not found']
You are not expected to ping over an http proxy, ping sends an network packet which can't be sent over an http proxy.

4. Probably there was a problem with the ubuntu core servers.

---

### Post by richbarna on 2006-07-25
Hi, lifeperfection.

Firstly I recommend the re-install, 
1 Ghz Pentium III/256Mb RAM would be better suited to Xfce desktop or maybe even KDE. "Some" people have said that Gnome is slower.

Secondly, forget the webcam, companies refuse to release Linux drivers, and although there is a big effort to get webcams working, only a handful of people succeed. To be honest, I don't think that the quality is all that hot on mac or Windows either.

Thirdly, if you choose the KDE desktop route, you will have Kmail (email), Kopete (multi messenger).

I actually had less problems with my KDE setup than Gnome. I still use Gnome more often, although I have slightly more power than your PC and it took a while to get it set up how I like it.

For a good source of information, go to Aysiu's site [psychocats,]("http://www.psychocats.net/ubuntu/index.php") and have a good read, I would pay special attention to the part that is called "_Playing Around_" and especially the "Pure KDE" and the "Pure XFCE" sections.

If you choose a re-install, remember that [Automatix]("http://getautomatix.com/wiki/index.php?title=FAQ") will sort out many multimedia problems in one go.

Good luck !!

---

### Post by lifeperfecti0n on 2006-08-02
ok sorry for the late post i was a bit busy
I installed kde via synaptic n been usin it 4 a while now...but i dont like it that much...nywayz some1 suggested i reinstall gnome n since v 2.14 is now out im goin to do that...
regarding my webcam problem i realised i had not inserted the compiled spca5xx.ko file in the kernel n did 'sudo insmod spca5xx.ko' but got the following:
insmod: error inserting 'spca5xx.ko': -1 Unknown symbol in module
Any idea what is happening?
I just want to get the webcam to work-i am not too worried about using it thru MSN because apparently my LAN's firewall doesn't allow webcam connections :roll: 
Do you think prelinking modules is worth the risk for speeding up my system?
Anyways....thanks v.v. much for the advice..im not at least not stuck in limbo as I was a few days back :D

---

