---
title: "1st post - new to Ubuntu &amp; need help with WoW"
date: 2007-05-30
forum: Gaming &amp; Leisure
---

### Post by FishBoi on 2007-05-30
Hi,

This is a repost from my orginal in the beginners section. Nothing going on there.  I'll try keep this short and sweet. Thanks in advance for your help. BTW - I really like the layout of the forums. Hope this is a taste of what lies ahead in Ubuntu.

Goal - my girlfriend and I would like to play WoW together, and try get two separate terminals running off one PC (each with their own mouse, keyboard and monitor, but using one box), so that we dont have to buy her a new PC. As you know WoW runs through the internet, so we dont have to worry about multiplayer network settings on one PC for now.

History - I've spent a week trying to get this right on XP using 3rd party software etc. Nothing has worked. MS Multipoint also has no release date yet. Someone at THG suggested I try Linux. I've never even seen Linux being used, LOL. To conclude, I'm a total noob when it comes to this OS. I did some research, and I decided that Ubuntu was the way to go (ie. most popular platform out there so it will probably have the most support in the forums). This OP suggested I use Linux to run multiple X-servers (still learning about this), and config those X-servers to accept their own inputs (mouse, keyboard, monitor), and even independent outputs (2nd sound card). I'm hoping I can use my x1900xt with dual monitor support, so I dont have to buy another v-card (too expensive and a deal killer for this project).

My specs - E6600 @3.33Ghz; | P5W DH Deluxe @370Mhz FSB | Thermalright Ultra-120 | MSI x1900xt | 2GB OCZ Plat Rev2 @740Mhz, 4-4-4-12 | Seagate Barracuda 320GB

My plan - From what someone advised me, this setup should be simple. Install Ubuntu, update your drivers, install Wine or Cedega, copy your WoW folder across from XP, setup the multiple X-server setup (maybe using MPX), config your inputs, and green for go. I know its never gonna work out first time, but this is my planned route.

Question 1 - Is this multiple user setup even possible with Ubuntu (and able to run dual instances of WoW on one PC with 2 terminals, no lag). My PC is a machine, so I dont see hardware limitations. Its gonna come down to software. It may be possible in theory, but I would like to speak to someone who has actually got it working.

Question 2 - I hear there are massive issues with ATI drivers. Very surprised that this hasnt been sorted out for over a year now, but so be it. Will this setup work baring in mind the issues with ATI drivers?

Question 3 - Do you agree with my planned route to get this right?

So far - Last night I installed an old HDD so my main HDD doesnt have to be partitioned. I also put in a Nvidia 7900GS on loan incase 2 vcards worked better. Booted up from the CD. Moved forward with the installation. The orange bar loaded up and was being filled, and then I got an error saying that my vcard or something wasnt supported (will get the exact error message tonight). It could be that I have a 2nd Nvidia 7900 installed, and this caused install probs. My plan is to take the Nvidia out, install the x1900xt as my main, and then try again. Really not a good start if I cant even get to the install screen, LOL! Is this a know issue (ie. trying to install Ubuntu with two different vcards installed)

Thanks again. Lets hope this works out! I really like the philosophy behind Ubuntu. Good on you.

---

### Post by dfreer on 2007-05-30
:shock: ummmm.... good luck? seriously, it will be much better to do two pcs, or even a dumb terminal that can access the linux box. nevertheless, if you REALLY want to do this and won't take no for an answer, I'll try to help you out after I get off work tonight. but if this is just "hey that sounds cool I wanna do that" and you're just gonna flake out after hitting 1-2 speedbumps than it isn't worth the time, just get another PC.

---

### Post by FishBoi on 2007-05-30
> **dfreer said:**
> :shock: ummmm.... good luck? seriously, it will be much better to do two pcs, or even a dumb terminal that can access the linux box. nevertheless, if you REALLY want to do this and won't take no for an answer, I'll try to help you out after I get off work tonight. but if this is just "hey that sounds cool I wanna do that" and you're just gonna flake out after hitting 1-2 speedbumps than it isn't worth the time, just get another PC.

LOL!!  Dude, read this post.  Will give you some context of my struggle.  
[http://forumz.tomshardware.com/hardware/modules.php?name=Forums&file=viewtopic&all=1&t=238387&postdays=0&postorder=asc](http://forumz.tomshardware.com/hardware/modules.php?name=Forums&file=viewtopic&all=1&t=238387&postdays=0&postorder=asc)

People have been saying it cant be done 24/7.  Where there is a will, there is a way.  If this can be done, then I have weeks to get this sorted out.  No rush.  I just have got to get this done cause it can save me thousands.  The GF and I wanna be setup for some hard core gaming before the winter comes, cause in winter we cant really do much else.  It sucks!  I've gotten started on this now so I can get it perfected.

Do you have a 2nd monitor at home?  Are you able to really work with me through this?  Would be great to get a partner in crime to help out, who is actually trying to solve this issue with me hands on.  I'm a Google machine and can get the tools we need.  I just have no idea how to implement them.

Anyway, **_first_** let me see how tonights install goes first.  Hopefully I can get Ubuntu up and running on my single x1900xt without too much nonsense.

Can you post your specs?  Chat soon, and thanks.

---

### Post by Lucifiel on 2007-05-30
About ATI drivers, this is because ATI had never much interest in producing Linux drivers. They never came true on any of their announcements to do so. Recently, they were acquirred by AMD and who knows, they may actually come true on their announcement this time round. But we'll see only when there's evidence.

---

### Post by Lucifiel on 2007-05-30
Also, this might interest you about multiple users. I have not tried it 'cos uhm, my hard disk is gone and I'm running off an Wolvix iso image. lol. 

[http://www.freesoftwaremagazine.com/articles/users_in_ubuntu#comment-636](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu#comment-636)

---

### Post by The Noble on 2007-05-30
The nice thing with linux is that anything is possible. That doesn't mean it's feasible, but it is surely is possible. Try this thread for multiple graphics cards: 
```

http://ubuntuforums.org/showthread.php?t=329754

```

Otherwise, I can't help you much; all of my computers are laptops.

One question though: Do you have an integrated intel graphics card on your mobo? If you do, it may help a lot in the long run. Good luck.

---

### Post by Lucifiel on 2007-05-30
Also, you might have trouble booting with your motherboard although the other person had P5W DH , no Deluxe. And he managed to find out a solution which may or may not work for you.

"So to get this motherboard working with 7.04 Feisty i386 you need to plug a hdd (that wont be usable) into one of the EZ BACKUP (orange) connectors."

[http://ubuntuforums.org/showthread.php?t=438816&highlight=p5w](http://ubuntuforums.org/showthread.php?t=438816&highlight=p5w)

And about the ATI drivers, the official drivers are dreadful and piece of hell. Don't install them if you want to preserve your sanity.

---

### Post by FishBoi on 2007-05-30
> **Lucifiel said:**
> Also, you might have trouble booting with your motherboard although the other person had P5W DH , no Deluxe. And he managed to find out a solution which may or may not work for you.

"So to get this motherboard working with 7.04 Feisty i386 you need to plug a hdd (that wont be usable) into one of the EZ BACKUP (orange) connectors."

[http://ubuntuforums.org/showthread.php?t=438816&highlight=p5w](http://ubuntuforums.org/showthread.php?t=438816&highlight=p5w)

And about the ATI drivers, the official drivers are dreadful and piece of hell. Don't install them if you want to preserve your sanity.

Yeah, good start.  I managed to get to the install screen this time around by removing the Nvidia card.  I got to the test desktop, double clicked on the install icon, and went through the motions.  It then asks me which drive to install on, and it cant find my 2nd HDD.  I have the 320GB SATA, and a 110GB IDE plugged into this port (see pic).
[[IMG]http://img259.imageshack.us/img259/9107/p5wdhdeluxeyb1.th.jpg[/IMG]](http://img259.imageshack.us/my.php?image=p5wdhdeluxeyb1.jpg)

Ubuntu doesnt recognize my second drive.  WTF?  Guess I'm gonna go digging.  Thanks for the info on the P5W DH.  Any other ideas?

---

### Post by Lucifiel on 2007-05-30
> **FishBoi said:**
> Yeah, good start.  I managed to get to the install screen this time around by removing the Nvidia card.  I got to the test desktop, double clicked on the install icon, and went through the motions.  It then asks me which drive to install on, and it cant find my 2nd HDD.  I have the 320GB SATA, and a 110GB IDE plugged into this port (see pic).
[[IMG]http://img259.imageshack.us/img259/9107/p5wdhdeluxeyb1.th.jpg[/IMG]](http://img259.imageshack.us/my.php?image=p5wdhdeluxeyb1.jpg)

Ubuntu doesnt recognize my second drive.  WTF?  Guess I'm gonna go digging.  Thanks for the info on the P5W DH.  Any other ideas?

Sorry, man. In terms of assembling hardware and troubleshooting hardware, I'm... kinda out of touch?

I suspect these booting issues might have to do with the JMicron chip or wahtever you call it.

Perhaps you can try this: remove your second hard disk and then put it back after installation is done. Although I'm not too sure whether it'll be recognised after the installation goes through, it's worth a try.

---

### Post by Lucifiel on 2007-05-30
Oh and one more piece of advice: if your installation goes well, make sure to get Partimage and back up everything!!!!

Finally, I'm already sure you know to put "/home" on a different partition, right?

---

### Post by FishBoi on 2007-05-30
I cant even get to the partition part.  It defaults to my main C: with all my info, and I cannot delete/partition that drive.  I have a spare IDE 110GB in there, but the install shield doesnt recognize/see it.  Any ideas?  Im still looking.

---

### Post by The Noble on 2007-05-30
Try changing which one is master and slave in the bios. After you install, use gparted to see what the [new] slave's (the 320 SATA) location is (ie /dev/sdc3). Ubuntu won't mount the extra hard drive until you add it to fstab, so add it at the bottom. ask if you want help, as I know a little about what you are going through.

EDIT: Also, try using the alternate cd instead of the desktop install cd you are using, as the desktop cd is trimmed down, feature wise. It may only be looking for the primary hard drive, thuse my comment on master/slave.

---

### Post by Lucifiel on 2007-05-30
Uh oh... do you need the JMicron controller? I'm afraid you might have to disable it. 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502/comments/204](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502/comments/204)

Gee... maybe someone who owns a JMicron board can step in and help.

---

### Post by FishBoi on 2007-05-30
Wow guys, this is really tough.  Linux is a bitch to work with.  The 110GB HDD is on its own IDE cable, going into that black port.  The 320GB is a SATA, using a separate small SATA jack.

Any other ideas how I can see my 2nd HD?  I tried disabling the 320GB, make the 110 my main etc. in the BIOS.  No luck.

---

### Post by Lucifiel on 2007-05-30
No, Linux isn't the problem here. :p The problem is that the hardware manufacturers refuse to include Linux support for their drivers(Good ol' Microsoft plays a hand in this). So, the Linux folks have no choice but to try and write up support for the devices. However, there're only so many people and thus, the "support" doesn't always work.

Did you try disabling the JMicron controller?

---

### Post by Lucifiel on 2007-05-30
Also, you could try the Alternate LiveCD as TheNoble has suggested.

---

### Post by FishBoi on 2007-05-30
I cant.  I remember when I built my rig, this was the only way I could get it to work.  I also have a DVD ROM on IDE.  I remember this whole thing is screwy.  This combination of connections allowed me to see both the DVD and 110GB DVD.

What happens when I disable JMicron?  Im gonna try.

---

### Post by Dylnuge on 2007-05-30
> **FishBoi said:**
> LOL!!  Dude, read this post.  Will give you some context of my struggle.  
[http://forumz.tomshardware.com/hardware/modules.php?name=Forums&file=viewtopic&all=1&t=238387&postdays=0&postorder=asc](http://forumz.tomshardware.com/hardware/modules.php?name=Forums&file=viewtopic&all=1&t=238387&postdays=0&postorder=asc)

People have been saying it cant be done 24/7.  Where there is a will, there is a way.  If this can be done, then I have weeks to get this sorted out.  No rush.  I just have got to get this done cause it can save me thousands.  The GF and I wanna be setup for some hard core gaming before the winter comes, cause in winter we cant really do much else.  It sucks!  I've gotten started on this now so I can get it perfected.

Do you have a 2nd monitor at home?  Are you able to really work with me through this?  Would be great to get a partner in crime to help out, who is actually trying to solve this issue with me hands on.  I'm a Google machine and can get the tools we need.  I just have no idea how to implement them.

Anyway, **_first_** let me see how tonights install goes first.  Hopefully I can get Ubuntu up and running on my single x1900xt without too much nonsense.

Can you post your specs?  Chat soon, and thanks.

Listen closely: It is possible to run two terminals off the same computer. Same computer=shared processor, shared memory, etc-including shared network connection. WoW will run really slow. Add that to the fact that WoW is not made for Linux (which will make the game slow), and you have some major speed issues. If you can get WoW working. If.

I am not trying to turn you away from Ubuntu. I am not laughing at you, or telling you I don't take this seriously. Computers can be expensive, and saving money may seem worth it. However, based on the speed issues, your best bets are to take turns or buy a new PC. Now Linux is great for a lot of things. I love the system, and I play tons of video games which I get working under Wine or Cedega. I have used multiple terminal environments before: to see the effects, press CTRL-ALT-F1 through F6. **To return press CTRL-ALT-F7.** (Bolded so you would read before trying). If you want, log in and type gdm. Then that terminal will be working.

However, that is not for the faint of heart. Neither is emulation. Understand that a processor can only handle so much at a time. If you currently experience absolutely no lag, that experience will change. If you do, you will experience about twice what you are now, maybe more.

Now that said, I am willing to help out. I don't mind the idea, just don;t want you to be set up for disappointment. Good luck.

---

### Post by FishBoi on 2007-05-30
> **Lucifiel said:**
> Also, you could try the Alternate LiveCD as TheNoble has suggested.

Sorry to be a noob, and a dumb question I know, but where do I get the LiveCD?

---

### Post by FishBoi on 2007-05-30
> **Dylnuge said:**
> Listen closely: It is possible to run two terminals off the same computer. Same computer=shared processor, shared memory, etc-including shared network connection. WoW will run really slow. Add that to the fact that WoW is not made for Linux (which will make the game slow), and you have some major speed issues. If you can get WoW working. If.

I am not trying to turn you away from Ubuntu. I am not laughing at you, or telling you I don't take this seriously. Computers can be expensive, and saving money may seem worth it. However, based on the speed issues, your best bets are to take turns or buy a new PC. Now Linux is great for a lot of things. I love the system, and I play tons of video games which I get working under Wine or Cedega. I have used multiple terminal environments before: to see the effects, press CTRL-ALT-F1 through F6. **To return press CTRL-ALT-F7.** (Bolded so you would read before trying). If you want, log in and type gdm. Then that terminal will be working.

However, that is not for the faint of heart. Neither is emulation. Understand that a processor can only handle so much at a time. If you currently experience absolutely no lag, that experience will change. If you do, you will experience about twice what you are now, maybe more.

Now that said, I am willing to help out. I don't mind the idea, just don;t want you to be set up for disappointment. Good luck.

No I appreciate you being candid.  We'll see if we can get it to work.  Hope so.  If not, its going to be a long winter LOL!  Got to figure out that damn 2nd HDD.  Cant even find it LOL.  Resetting now to disable JMicron.

---

### Post by Lucifiel on 2007-05-30
> **FishBoi said:**
> Sorry to be a noob, and a dumb question I know, but where do I get the LiveCD?

Oh!!! Hang on, lol!!!

[http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso)

Okay the Alternate cd uses a text-based installer. Here's a tutorial site on how to install using the Alternate cd. [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Lucifiel on 2007-05-30
Oh and I've been skimming through this thread(very lengthy). It appears you might need to flash your bios.
This post mentions something about a fix.
[http://ubuntuforums.org/showpost.php?p=2321425&postcount=295](http://ubuntuforums.org/showpost.php?p=2321425&postcount=295)

This is the whole thread(very long!!!)
[http://ubuntuforums.org/showpost.php?p=1947596&postcount=262](http://ubuntuforums.org/showpost.php?p=1947596&postcount=262)

I'll be back in about 10 mins or so. I need to make breakfast.

---

### Post by The Noble on 2007-05-30
He was incorrect in saying that it was a livecd  (at least how you were thinking it is). You can get it here:
```

http://www.ubuntu.com/getubuntu/download

```
At the bottom of the page there is a little box that says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer." Click it and download the cd.

 Warning though: it is text based, but it's only scary if you don't like reading directions. It's easy to use, so be patient.

Also, there is no need to be sorry, you are learning quite quickly, but you are choosing a task that would rival even the best of us (especially as a beginner). Ask questions, lots of them, we are willing to help as much as you need, and I may even be able to get a computer to do the same thing you require.

The one thing I want you to do is read that first link I gave you, as it points out **one very important thing**: The fglrx and nvidia drivers will probably conflict. If they do, you are out of luck, as they are closed source and you would need access to the source to fix it. The one thing you could do is use that crappy intel integrated graphics card built into your motherboard, along with the nvidia card to make this relatively no frills.

About the hard drives...Why not use only one? Have a 20 gig partition on the major 320 gig sata drive that has ubuntu and wow, as that is what you want. Even though you will both be loading from one hard drive, there should be minimal slowdown. The hard drive is only accessed during loading sequences, so you should both rarely coincide with your access times.

---

### Post by Lucifiel on 2007-05-30
Sorry, oops... yes, it's not a LiveCd but it's an alternate installer. However, do make sure to read that lengthy tutorial. It'd at least get you through the process. 

Thanks, Noble. :) Now, I really have to get something to eat. :p

---

### Post by The Noble on 2007-05-30
Hey, no problem! Enjoy your breakfast! It's dinner where I live, so I have a few more hours before I go to sleep. Let's see if we can get ubuntu to finally install on your system before I have to sleep.

---

### Post by Lucifiel on 2007-05-30
You meant "his", right? :P

Oh and I'm a female lol... but it's okay. :) And I'm back with coffee and cake. :D 

However, from what I've read so far, he might have to patch his Bios first. And I probably advise that Fishboy bring his pc and the bios to a store. That way, if anything goes wrong, the guys can reset the bios.

Edit: Oh and there's this O/S called Zenwalk which can work on JMicron. However, I know nothing about it.

---

### Post by wolf08 on 2007-05-30
I would like to echo the warning others gave - what you want to do is not anywhere near mainstream, however, I think it can be done. In that case...

I have a few points to add:

First of all, my setup is as follows:

Athlon x2 3800
Dual Nvidia 6600GTs
Dual monitor setup. 

I originally only had one graphics card and my 2 monitors. WoW ran fine, albeit at lower framerates than I was used to. However, it was perfectly playable (And I raided 3 times a week, so not just casually playable). 

I acquired the second video card a few weeks ago, and in addition, was able to borrow a 3rd monitor for a while. I thought, wtf, lets try a multiuser setup, and got to work. 

I ended up with this: 

Nvidia drivers for both cards worked perfectly. I needed to manually edit something called the xorg.conf file (The thing that tells your gui wtf is up, located at /etc/X11/xorg.conf) and I had to secure a second mouse/keyboard, but everything worked really well. I could do 3d effects on both 'user environments' at the same time, with no noticeable slowdown. Would it run wow? I have no clue. However, everything else ran well. 

[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

The above link REALLY helped me get setup correctly. I was only doing 2 users, not 6, but the same principles applied. If you keep plugging at this, I'm happy to help.

---

### Post by Lucifiel on 2007-05-30
Btw, Fishboy, whoever advised you to try Ubuntu obviously didn't do much thinking and research beforehand. Honestly, it's not advisable to recommend an o/s which has known problems with certain components to someone whose hardware comprise of such components. 

For something like Linux, sometimes such "oops" can really sour your experience.

However, Zenwalk btw is not for beginners so I'll have to try and see if there's another o/s you can try. Trust me... if Ubuntu doesn't work after a couple of tries, don't waste your time on trying everything out of the book.

---

### Post by The Noble on 2007-05-30
Sorry, I wasn't thinking too much at the time I was writing that, but yes, his computer. And pardon me calling you a man; I don't see many females on The Internets much these days. 

With that out of the way, flashing the bios is not that dangerous if you use a new floppy and have plenty of reliable power. I don't know much about zenwalk either, although it is a slackware based operating system, so have fun compiling. You'll do alot. Tell us what happens after you try booting without jMicron on.

---

### Post by Lucifiel on 2007-05-30
> **The Noble said:**
> Sorry, I wasn't thinking too much at the time I was writing that, but yes, his computer. And pardon me calling you a man; I don't see many females on The Internets much these days. 

With that out of the way, flashing the bios is not that dangerous if you use a new floppy and have plenty of reliable power. I don't know much about zenwalk either, although it is a slackware based operating system, so have fun compiling. You'll do alot. Tell us what happens after you try booting without jMicron on.

Haha it doesn't matter about me being female or not. :p

However, really... I don't know about the power thing but flashing a bios by yourself ain't always the smartest thing for it might fry a lot of stuff on your board. :x Often, it's a trial and error issue.

Furthermore, if he ends up flashing the wrong version, he could well bork up his entire system. That's why I actually suggested a visit to the hardware store: sometimes, they might even have the right version of the bios(with the fix). 

'Cos from what that post mentioned, you needed to have the fix integrated into the bios and you know, hacking into or patching a bios sounds quite tough. Not to mention that you might not even know if you integrated the fix properly. 

Although, maybe he can just ring up a few stores and see if they know anything about JMicron and fixes for JMicron PATA for Linux.

---

### Post by The Noble on 2007-05-30
I found this while doing a google search; it may help. 
```

http://ubuntuforums.org/showthread.php?t=373662

```
You are using feisty, right?

---

### Post by Lucifiel on 2007-05-30
I think the threadstarter is using the Feisty LiveCd (wait... he better be using it 'cos Edgy and the other versions might not work so well for JMicron) but he seems to have gone off.

---

### Post by Lucifiel on 2007-05-30
To fishboi : please, tell us you're using the 7.04 LiveCd or I'm really going to cry. =P

---

### Post by bodhi.zazen on 2007-05-30
> **FishBoi said:**
> Hi,

This is a repost from my orginal in the beginners section. Nothing going on there.  I'll try keep this short and sweet. Thanks in advance for your help. BTW - I really like the layout of the forums. Hope this is a taste of what lies ahead in Ubuntu.

This is short and sweet ? LOL

> Goal - my girlfriend and I would like to play WoW together, and try get two separate terminals running off one PC (each with their own mouse, keyboard and monitor, but using one box), so that we dont have to buy her a new PC. As you know WoW runs through the internet, so we dont have to worry about multiplayer network settings on one PC for now.

History - I've spent a week trying to get this right on XP using 3rd party software etc. Nothing has worked. MS Multipoint also has no release date yet. Someone at THG suggested I try Linux. I've never even seen Linux being used, LOL. To conclude, I'm a total noob when it comes to this OS. I did some research, and I decided that Ubuntu was the way to go (ie. most popular platform out there so it will probably have the most support in the forums). This OP suggested I use Linux to run multiple X-servers (still learning about this), and config those X-servers to accept their own inputs (mouse, keyboard, monitor), and even independent outputs (2nd sound card). I'm hoping I can use my x1900xt with dual monitor support, so I dont have to buy another v-card (too expensive and a deal killer for this project).

My specs - E6600 @3.33Ghz; | P5W DH Deluxe @370Mhz FSB | Thermalright Ultra-120 | MSI x1900xt | 2GB OCZ Plat Rev2 @740Mhz, 4-4-4-12 | Seagate Barracuda 320GB

My plan - From what someone advised me, this setup should be simple. Install Ubuntu, update your drivers, install Wine or Cedega, copy your WoW folder across from XP, setup the multiple X-server setup (maybe using MPX), config your inputs, and green for go. I know its never gonna work out first time, but this is my planned route.

Question 1 - Is this multiple user setup even possible with Ubuntu (and able to run dual instances of WoW on one PC with 2 terminals, no lag). My PC is a machine, so I dont see hardware limitations. Its gonna come down to software. It may be possible in theory, but I would like to speak to someone who has actually got it working.

Yes. Linux is a multi user environment. You need to decide how you would like to set this up :)

Is this what you want ?

[http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)

> Question 2 - I hear there are massive issues with ATI drivers. Very surprised that this hasnt been sorted out for over a year now, but so be it. Will this setup work baring in mind the issues with ATI drivers?

I donna know. I Nvidia.

Sell your ATI and buy a Nvidia :twisted:

ATI seems lagging in the "support Linux" Department.

This *might* help:

ttp://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide

> Question 3 - Do you agree with my planned route to get this right?

Should work

> So far - Last night I installed an old HDD so my main HDD doesnt have to be partitioned. I also put in a Nvidia 7900GS on loan incase 2 vcards worked better. Booted up from the CD. Moved forward with the installation. The orange bar loaded up and was being filled, and then I got an error saying that my vcard or something wasnt supported (will get the exact error message tonight). It could be that I have a 2nd Nvidia 7900 installed, and this caused install probs. My plan is to take the Nvidia out, install the x1900xt as my main, and then try again. Really not a good start if I cant even get to the install screen, LOL! Is this a know issue (ie. trying to install Ubuntu with two different vcards installed)

Thanks again. Lets hope this works out! I really like the philosophy behind Ubuntu. Good on you.

OK. But I think you need to read and then build around your plans.

You should also check out edubuntu :

[http://www.freesoftwaremagazine.com/articles/linux_terminal_server?page=0%2C0](http://www.freesoftwaremagazine.com/articles/linux_terminal_server?page=0%2C0)

[http://doc.ubuntu.com/edubuntu/handbook/C/](http://doc.ubuntu.com/edubuntu/handbook/C/)

I do not think edubuntu is exactly what you had in mind, still ...

Let us know how we can help :)

---

### Post by Lucifiel on 2007-05-30
Thank you, Bodhi for fulfilling my request to look at this thread. :D  

Anyways, fishboi, go take the next few days and slowly have a read through various documentation and threads about this problem. :) 'Cos there might be stuff you gotta disable and enable and rushing through the installation right now won't be the best idea. :) 

Remember,  Linux is not Windows #2, so the learning curve might be a bit jagged for now. :D

---

### Post by Lucifiel on 2007-05-30
Still, I wonder if there are ways or utilities to allocate a minimum to maximum amount of cpu speed to a program. And also, it's a pity you don't run dual processor as there might be utilities to assign each processor to each instance of the program and limit the program to only 1 processor. (I've heard of some folks who tried the latter but I don't know if it worked. As they were likely using Windows, I don't know if this will work under Linux.)

---

### Post by The Noble on 2007-05-30
I would like to build on what she said though and say that it gets quite eeasy later. 

By golly I hope he hasn't had trouble with the install. If he accidentally reinstalled over xp, well, oops.

---

### Post by FishBoi on 2007-05-30
Hi again guys, and now a lady I hear :)

Wow, this is a lot to digest.  I really need to take a few days to take this all in.  Some intial comments:
- I tried getting the 110GB setup.  I coulndt.  Tried all my settings in the BIOS.  I've had issues with this setup from day one (JMicron takes control of all IDEs and messes with them).  I'm gonna order another 320GB SATA drive, which would make things 10,000 times easier.  It should be here by Saturday.  Will install and then try again.
-I cant partition my existing drive cause I'll lose all my data.  I have nowhere to back it up (250+ gigs), and I cant lose it.  I need a 2nd HD to install Linux on to.  I'll allocate around 60GB of the new 320GB to Ubuntu.  I could use the space anyway
-my BIOS is the latest version, flashed it about a month ago, v20.07 I think.
-someone mentioned that they may be able to try and set this up at home, with me and working together.  That would just be grand as we can share our experiences as we grind through this.
-I downloaded the 6.06 version I think (didnt know any better, looked at the LTS).  Suppose I have egg on my face now.  Sorry again guys.  Noobie noob in the house, but learning.
-I'll get the alternate CD as it seems like thats the way to go.
-Wolf08 you legend!!!  Seems like you got it to work.  Please do chip in and help me to get there when I get up and running.

Give me a few days to get that 2nd HDD installed and please do come back here when I have it up and running.  I love the way you guys are willing to chip in.  Really appreciate it.

I will also probably post a few questions leading up to the new install.

Long live the penguin!

---

### Post by The Noble on 2007-05-30
> **Lucifiel said:**
> Still, I wonder if there are ways or utilities to allocate a minimum to maximum amount of cpu speed to a program. And also, it's a pity you don't run dual processor as there might be utilities to assign each processor to each instance of the program and limit the program to only 1 processor. (I've heard of some folks who tried the latter but I don't know if it worked. As they were likely using Windows, I don't know if this will work under Linux.)

He **does** have a dual core. A core 2 duo to be exact. His cpu will be fine; ubuntu should automatically allocate each instance of WoW onto each core. I am more worries about the graphics situation currently, as support is shoddy at best.

We'll help him through, whatever the case.

---

### Post by Lucifiel on 2007-05-30
LOL... don't use 6.06!!! It has problems with JMicron. Go get Feisty fawn... lol! :P

Man, why don't you just sell off that board and get a new one from NewEgg(or another online store), with less problems? 

To Noble: Sorry my mind is not awake!! LOL... 

And junk the ATI card 'cos even though ATI has promised Linux drivers, we can't say for sure until they release them.

---

### Post by Lucifiel on 2007-05-30
Oh and if I were you, don't use the Alternate Cd yet. Just give the LiveCD a shot 'cos Alternate is only really recommended if you can't get the LiveCd to run. And it's a lot more difficult to use some Command Line Interface (think a very sophisticated version of CLI instead of the very limited and confusing version of Dos) especially if you're new to Linux.

And finally, when you install Ubuntu, do a "manual partitioning". Do NOT allow Ubuntu to use the whole hard disk or it will hose your entire installation of WinXP! Also "guided partitioning" might not work out so well.

Instead, use these settings:

"/" (Without the parenthesis, / refers to root. Root stores all the folders equivalent to system, system32, etc., )
Root needs to have at least 6 to 8 gb free. Set it as ext3 filesystem.
/home (Home stores all your personal settings like program settings, Terminal settings(Ms-Dos is so not comparable to this), etc. etc.)
Home is recommended to have between 15 gb to 20 gb minimum. Set as ext3 filesystem.

And finally, there's your linux swap partition. Set it as "linux-swap" filesystem. I recommend double your system memory. Games can be really intensive and you don't want to run out of memory halfway, especially with this setup of yours.

---

### Post by FishBoi on 2007-05-30
> **Lucifiel said:**
> Oh and if I were you, don't use the Alternate Cd yet. Just give the LiveCD a shot 'cos Alternate is only really recommended if you can't get the LiveCd to run. And it's a lot more difficult to use some Command Line Interface (think a very sophisticated version of CLI instead of the very limited and confusing version of Dos) especially if you're new to Linux.

K will do.  Thanks.  Also, I've give Fiesty a run.  See if it works.  I dont wanna just start scrapping my hardware just yet.  This setup is one of the best available using XP.  It really works well.  If Linux delivers, I will gladly move.  I dont really use XP anyway - nothing more than my 10 core apps.  XP is just really great when it comes to plug and play.

I'll keep you posted.  Getting Fiesty as we speak.

---

### Post by The Noble on 2007-05-30
Ok guys, lets take this slow from here on out. Here is the list of things that need to be done before anything else is started;

1. Fishboi, download the latest 7.04 Feisty Fawn Alternative Cd from the main site. It's fine that you chose the 6.06 cd the first time around: it's better for people new to the scene to only deal with the stable releases. If you have a real fast internet connection I would recommend that you download the Desktop Cd as well. It would help if anything goes wrong.

2. Revert to your original settings on the motherboard. It's good to start with a base that you know works. As a rule, only toggle one option at a time so you know where to look if something fails.

3. (optional) Install using the nvidia card in and the ATI card out. Let's get to the gui before we do some real tinkering.

4. Try the install using the alternative cd. If you use fesity, it should work quite a bit better now. There are reports of 7.04 working better with the jMicron controllers. If this is the case, we should have smooth sailing. Just use the defaults in the install, we don't want you to bork the install with a bad partitioning table or anything. If you do feel comfortable messing with options, be my guest.

After you have a successful install, come back here. This should only take an hour if you have no problems. If you do, just come here and ask.

EDIT: I just read Lucifiel's comment, and I agree that you should try the LiveCD first. Maybe you won't have any hiccups. All we need to do is get ubuntu onto that hard drive! As a warning, your mbr on the first hard drive will be overwritten by something called grub. It doesn't go over anything really important, so don't stress about it.

---

### Post by Lucifiel on 2007-05-30
Oh and I re-edited my previous post. Do give it a read.

Okay, sure, fishboi and Noble. :)  Yeah, if you say so. :)

---

### Post by FishBoi on 2007-05-30
> **The Noble said:**
> Ok guys, lets take this slow from here on out. Here is the list of things that need to be done before anything else is started;

1. Fishboi, download the latest 7.04 Feisty Fawn Alternative Cd from the main site. It's fine that you chose the 6.06 cd the first time around: it's better for people new to the scene to only deal with the stable releases. If you have a real fast internet connection I would recommend that you download the Desktop Cd as well. It would help if anything goes wrong.

2. Revert to your original settings on the motherboard. It's good to start with a base that you know works. As a rule, only toggle one option at a time so you know where to look if something fails.

3. (optional) Install using the nvidia card in and the ATI card out. Let's get to the gui before we do some real tinkering.

4. Try the install using the alternative cd. If you use fesity, it should work quite a bit better now. There are reports of 7.04 working better with the jMicron controllers. If this is the case, we should have smooth sailing. Just use the defaults in the install, we don't want you to bork the install with a bad partitioning table or anything. If you do feel comfortable messing with options, be my guest.

After you have a successful install, come back here. This should only take an hour if you have no problems. If you do, just come here and ask.

Sounds good buddy.  Fiesty = 15% done.  Gonna give it a run.  I have already put back the x1900xt card, and will hopefully get it to run.  If not, I'll put the Nvidia in.  No biggie, but the ATI is already all wired.  Might as well try.

Who else is trying to get this one their setup?  I know there was one other.  Wait for me to get up to speed!  LOL!

---

### Post by Lucifiel on 2007-05-30
> **FishBoi said:**
> Sounds good buddy.  Fiesty = 15% done.  Gonna give it a run.  I have already put back the x1900xt card, and will hopefully get it to run.  If not, I'll put the Nvidia in.  No biggie, but the ATI is already all wired.  Might as well try.

Who else is trying to get this one their setup?  I know there was one other.  Wait for me to get up to speed!  LOL!

Okay dude... good luck, man! :D :p

Boy, it's really fun helping out with threads like these. You get to learn new things. :)

---

### Post by The Noble on 2007-05-31
The ATI card will work, I guarantee you it will, at least with some tinkering. How well though is another question. It looks like the fglrx driver works for your card, so that needs to be installed after the install. It's good to see that you started the installation.

---

### Post by Lucifiel on 2007-05-31
Hmmm... the flgrx driver is good or bad news, depending on the user. Hence, to fishboi: go and do this!

Download Partimage and clone your Ubuntu installation BEFORE you install flgrx. Don't choose any Gzip compression. That way, if anything goes wonky, just hit restore! :p 

Try this tutorial for Partimage:

[http://ubuntuforums.org/showthread.php?t=287522&highlight=partimage](http://ubuntuforums.org/showthread.php?t=287522&highlight=partimage)

---

### Post by The Noble on 2007-05-31
> **Lucifiel said:**
> Hmmm... the flgrx driver is good or bad news, depending on the user. Hence, to fishboi: go and do this!

Download Partimage and clone your Ubuntu installation BEFORE you install flgrx. Don't choose any Gzip compression. That way, if anything goes wonky, just hit restore! :p 

Try this tutorial for Partimage:

[http://ubuntuforums.org/showthread.php?t=287522&highlight=partimage](http://ubuntuforums.org/showthread.php?t=287522&highlight=partimage)

I don't know. That looks complicated and could take a lot of time. He won't have anything valuable on the system, so he might as well do a full reinstall if anything goes haywire. Let's see how far we can go without a backup. If we hit a good stopping point that would be a pain to get to again, we should make a backup. Otherwise, a backup of a fresh install would be a waste of time.

---

### Post by Lucifiel on 2007-05-31
Hmmm... it isn't that complicated.

It's just mounting the partition you want to backup to and then selecting the partition you want to restore to.

Like: sudo mkdir /backup

Then, "mount /dev/hdc3 /backup"

Then, you start up "partimage" by typing "partimage" at the command prompt. Then, select the partition you want to save and fill in the partition and image name like /backup/backup_01"

I proposed that 'cos seriously after going through all that work to get Feisty up and running, you don't want to have reinstall a second time that fast, right? ;p 

But yeah, Noble, you have a good point there. :) Let's see hwo things go for now.

---

### Post by The Noble on 2007-05-31
Remember, he is, for lack of a better word, a newb. For you or I, that is trivial stuff, but for him it could take an hour or two to complete. If he completes the installation once, he would be able to do it again much faster. It worked for me that way at least. Let's take one step at a time though.

Edit: It's a great suggestion for later, as either a stopping point or when we are finished. It would suck to get everything working then losing it all again.

---

### Post by Lucifiel on 2007-05-31
Oops... yep, I tend to forget I'm a power user and that 'cos I kept running into problems(mostly user-inflicted problems), I was forced to learn how to tinker a lot with Ubuntu within just 2 months. :p

Yeah... Partimage is good for later on but not right now... oops. =P

---

### Post by The Noble on 2007-05-31
Hey, I just wanted to point a heads up: The latest fglrx (36) causes problems on a bunch of cards. A new version should be out tomorrow, so wait till then to install it.

Also, I am going to bed, and I should not be able to get back on until 24 hours from now. I will keep an eye on this thread though when I get back. Good luck, and i'll see how this progresses in a day! Don't finish it off when I'm gone!

---

### Post by Lucifiel on 2007-05-31
Yeah, man... I'm also going to have to go off soon. ^^;; I've got a load of work to do.

Hmmm... I'm suggesting to maybe wait a day or two to install flgrx 'cos you'd want to get user opinions from the old birds before you try plonking it onto your system. Sometimes, new drivers break more than the old ones, so hold onto the default drivers first and use the time to learn more about Ubuntu and Linux in general. :D

Edit: Bodhi recommends that you read this article. It's definitely what you want, correct? :D

[http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)

---

### Post by FishBoi on 2007-05-31
Hi guys,

It got too late last night so I couldnt complete the 7.04 install.  I'll do it first thing tonight to see if it recognizes my IDE HD, and hopefully it will.  If not, I'll order another SATA HD and take it from there.  Probably will only get here next week so we will then have to be patient for a few days.  I'm gonna go fishing on Saturday anyway!  Lets hope the IDE works so we can get going.

I found this link, FYI: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502).  Seems like its a known issue.  The P5B is nearly the same as my mobo.

PS. There is a lot to read and take in, but its all gibirish to me as I have no context to put it into.  I think it will have more impact when I am actually in step #x in the process, and actually reading up on how to do step #x.  Some of the terms you mention - I have no idea what they are! LOL

Anyway, will be a quiet day here.  Let me get home tonight and see what I can do. Over and out!

---

### Post by Lucifiel on 2007-05-31
Oh boy, don't worry. :)

If it heartens you, I was like you in the beginning too. :D I first started using Ubuntu about 60 days ago. After a string of reinstallations(oh I borked up my install far too much) and tinkering around, I finally became much more comfortable with Linux. :)

Ever since I started using Linux, I've booted less than 10 times into WinXP and each time I did so, I was guilt-ridden. :p 

Oh and here're a few explanations about mounting.

In any operating system, your partitions have to be mounted in order for the data and programs to be accessed and modified, etc., etc. In WinXP, the partitions are often mounted automatically for you BUT with one setback: the drive letters sometimes change when you reinstall WinXP or add in a new partition. 

In Linux, most of the times, the partitions are mounted automatically but the partition numbers are very consistent. Like /media/hdc1 (Usually for IDE/Pata drives) and /media/sda1(For Sata partitions).

/dev/hdc1 , /dev/hdc2, /dev/sda1, etc. all are devices themselves and the labels under /media/ point to the devices. The devices(partitions) themselves cannot be accessed and if you want to access the partitions, you need to use /media/sda1, /media/hdc1, etc. 

You may notice the lack of drive letters but in my honest opinion, the labels that Linux uses are often more logical because they're labelled according to the order of the partition.

Anyways, sometimes the labels are not automatically created. So, you will need to link the device to the label. You do this by mounting the partition.

Like > mkdir /media/chicken_momma
sudo mount /dev/hdc3 /media/chicken_momma

---

### Post by The Noble on 2007-05-31
> **FishBoi said:**
> Hi guys,

It got too late last night so I couldnt complete the 7.04 install.  I'll do it first thing tonight to see if it recognizes my IDE HD, and hopefully it will.  If not, I'll order another SATA HD and take it from there.  Probably will only get here next week so we will then have to be patient for a few days.  I'm gonna go fishing on Saturday anyway!  Lets hope the IDE works so we can get going.

I found this link, FYI: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502).  Seems like its a known issue.  The P5B is nearly the same as my mobo.

PS. There is a lot to read and take in, but its all gibirish to me as I have no context to put it into.  I think it will have more impact when I am actually in step #x in the process, and actually reading up on how to do step #x.  Some of the terms you mention - I have no idea what they are! LOL

Anyway, will be a quiet day here.  Let me get home tonight and see what I can do. Over and out!

Aye, the reason we are telling you to use feisty instead of Dapper, is that dapper uses a kernel before 2.6.17 while feisty uses 2.6.20, so the known issue should be fixed. I have an hour or two at home before I have to leave again, so now is a good time to catch up on anything you don't exactly know about. Ask any question you have, as we will probably be able to figure it out. Good luck on the install.

---

### Post by graigsmith on 2007-05-31
as long as you can find something that lets you run 2 videocards and 2 mice, and 2 desktops on the same computer, i figure it could be possible.

---

### Post by Dylnuge on 2007-05-31
> **FishBoi said:**
> Hi guys,

It got too late last night so I couldnt complete the 7.04 install.  I'll do it first thing tonight to see if it recognizes my IDE HD, and hopefully it will.  If not, I'll order another SATA HD and take it from there.

Good luck.

> **Lucifiel said:**
> If it heartens you, I was like you in the beginning too.

I was too, pretty sure we all were. Everyone needs to start somewhere, right :).

---

### Post by FishBoi on 2007-05-31
> **Dylnuge said:**
> Good luck.
I was too, pretty sure we all were. Everyone needs to start somewhere, right :).

LOL - start somewhere, yeah right!  I've got to get into Ubuntu before I can do anything.  So just a quick update.  Mounted the 7.04 version on a CD (CD #2 now), and tried to boot up.  Got this error:

/bin/sh: can't access tty; job control turned off
(initramfs) [340823011] ata3.00; failed to set xfermode (err-mask=0x40)

/bin/WTF does that mean!

I guess I'm gonna have to go to CD #3 and use the alternate installer then, or just get a better SATA HD and avoid the JMicron.  Actually, come to think of it, my DVD is also on IDE and the JMircon controls that too.  Disabling that will lose my DVD too.  Not even sure if a new HD will sort that out,  I need to give it some thought.

Anyway, dont trouble yourselfs with this.  Im gonna hit google now, see what I can dig up.  Thanks again for the help.  Will let you know how things pan out.

---

### Post by FishBoi on 2007-05-31
I found this.  Gonna give it a whirl:

Originally Posted by Aldebran  
I think I have some solutions :

The first solution is (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'all_generic_ide'

The second solution is more complex but i think it's better (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'break=top'
A shell will appear, so :
- Write 'modprobe piix' (after you will see some text)
- Finally, write 'exit'

The third and the four solutions are not really good so don't use it if the first or the second works :
- You can let a floppy disk in your computer and "maybe" it will work.
- You can use the option "Install with driver CD" with the live-cd, and press Enter without changing the CD (two times), and "maybe" it will work.

---

### Post by FishBoi on 2007-05-31
Nope, when I hit F6, it gave some strange character (cant even draw it).  Weird.  Searching ......

---

### Post by FishBoi on 2007-05-31
Random - I tried to reboot and try again, and it went into the install desktop this time!  Woohoooo!

Still cant find my 2nd HD.  A question - I read somewhere that the partition manager can manage my main HD without affecting any of my existing data (ie. dont touch the 250 gigs of my 320GB HD, and only install on say 20 gigs.

Is this true.  Anyway, if I dont come right tonight, Im gonna get a new HD.

---

### Post by FishBoi on 2007-06-01
Once I have the desktop up, is there any terminal I can open to maybe punch in some code to try and find my drive?

---

### Post by Lucifiel on 2007-06-01
Go to Applications ====> Accessories ====> Terminal

Then in Terminal, type

> sudo fdisk -l 

If you can't find more than 1 hard disk listed, then it's not being detected. 

Geez, it's amazing that I can remember all this off my head.

---

### Post by bodhi.zazen on 2007-06-01
> **FishBoi said:**
> Once I have the desktop up, is there any terminal I can open to maybe punch in some code to try and find my drive?

Once you are running live, open a terminal : Applications _ > Accessories -> Terminal

Enter ```
sudo fdisk -l
```

This should give a list of all HD.

#2 Yes, you can use part of your HD to install ubuntu. Start Gparted.

You will need say 15-20 Gb for a base and you also need a swap partition. In general the size of swap = RAM X2, max 1Gb (the more ram you have the less you will need swap).

This may help :

Basic partitioning : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Gparted : [http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

### Post by Lucifiel on 2007-06-01
Hah, bodhi, I beat you... :p Looks like the young folks still win! :D

---

### Post by The Noble on 2007-06-01
The best way to add the ubuntu ubuntu to your first hard drive is to start the desktop live cd and install gparted through synaptic. Once the install is complete, start gparted and shrink the the main partition already there (after defragging windows once or twice). Have 20-30 gig of unpartitoned space at the end of the drive.  Once that is done, start up the installer and tell it to use all unpartitioned space. This way, only that 30 gig partition at the end of the drive will be used. If you want to later, that part of the drive can be regained for window's use through gparted. Ask before you do anything, though, and triple check everything you do. I understand that you still may want to use the second hard drive, and I do think it is a better choice (if you can get it running).

---

### Post by Lucifiel on 2007-06-01
Hmmm... Fishboi, maybe after installing Ubuntu, you can try this. Disabling Jmicron drivers and forcing Ubuntu to select a better set of drivers?

I've heard that some managed to get that working out and thus allow their Pata drives to be detected.

Edit: This is what I found. It worked for Dapper/Edgy and might not work for Feisty. What you have to do is blacklist the JMicron drivers(which're the more primitive versions) and force Feisty to use the drivers from libata. If you succeed in blacklisting the drivers, then you could very likely get your PATA to be detected. 

[http://ubuntuforums.org/showpost.php?p=1947596&postcount=262](http://ubuntuforums.org/showpost.php?p=1947596&postcount=262)

Also, this post does mention some interesting stuff about the IDE option which is supposed to be enabled all the time. And about how it was actually off and disabling RAID enabled IDE again. 
[http://ubuntuforums.org/showpost.php?p=2518196&postcount=297](http://ubuntuforums.org/showpost.php?p=2518196&postcount=297)

---

### Post by The Noble on 2007-06-01
If you do decide to disable the jmicron driver after you are done with the install (this implies that you install ubuntu to the first hard drive), you can use gparted (on the live cd ONLY, do NOT use the installed ubuntu system with gparted) to copy the installed ubuntu partition onto the the second hard drive. You may have to mess with fstab, but we can do that later. Let's first see if we can have feisty find the hard drive before the install.

---

### Post by Lucifiel on 2007-06-01
Well he can probably try disabling Raid and see what happens, if he hasn't tried that already.

From what I know, he doesn't need that feature as he's using a SATA and PATA.

---

### Post by FishBoi on 2007-06-01
> **Lucifiel said:**
> Go to Applications ====> Accessories ====> Terminal
Then in Terminal, type
If you can't find more than 1 hard disk listed, then it's not being detected. 
Geez, it's amazing that I can remember all this off my head.

Morning guys.  I'll try to answer these one by one.  I actually googled that last night.  Found the terminal on my own so Im getting there, slowly!  Its fun.  I check fdisk -l, and I didnt see the drive there.  Its not being detected.  I want to see if I can program it to find it.  Reading the rest of the responses now .....

---

### Post by FishBoi on 2007-06-01
> **bodhi.zazen said:**
> Once you are running live, open a terminal : Applications _ > Accessories -> Terminal
Enter ```
sudo fdisk -l
```
This should give a list of all HD.
#2 Yes, you can use part of your HD to install ubuntu. Start Gparted.
You will need say 15-20 Gb for a base and you also need a swap partition. In general the size of swap = RAM X2, max 1Gb (the more ram you have the less you will need swap).
This may help :
Basic partitioning : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
Gparted : [http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

This could be a plan to avoid buying a new HD (although I dont mind - could always use it in a RAID 0 setup if this doesnt work out).

This is key - is there even the smallest risk of losing my data on C: ?  I cannt afford to lose my pictures files etc.  If there is the smallest chance, I cannot take it.  Reading on ....

---

### Post by FishBoi on 2007-06-01
> **The Noble said:**
> The best way to add the ubuntu ubuntu to your first hard drive is to start the desktop live cd and install gparted through synaptic. Once the install is complete, start gparted and shrink the the main partition already there (after defragging windows once or twice). Have 20-30 gig of unpartitoned space at the end of the drive.  Once that is done, start up the installer and tell it to use all unpartitioned space. This way, only that 30 gig partition at the end of the drive will be used. If you want to later, that part of the drive can be regained for window's use through gparted. Ask before you do anything, though, and triple check everything you do. I understand that you still may want to use the second hard drive, and I do think it is a better choice (if you can get it running).

This makes alot of sense.  I've heard the gparted works well.  I also read is essential that you defrag your C: (some poor noob I read about on the forumz forgot to and lost some data).  Im think Im gonna do this.  Quick question - what if there are files/system files that are unmovable at the end of the drive?  Will those be lost?  Thanks guys.  Reading on .......

---

### Post by FishBoi on 2007-06-01
> **bodhi.zazen said:**
> Once you are running live, open a terminal : Applications _ > Accessories -> Terminal
Enter ```
sudo fdisk -l
```
This should give a list of all HD.
#2 Yes, you can use part of your HD to install ubuntu. Start Gparted.
You will need say 15-20 Gb for a base and you also need a swap partition. In general the size of swap = RAM X2, max 1Gb (the more ram you have the less you will need swap).
This may help :
Basic partitioning : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
Gparted : [http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

Do you need to setup the swap partition too, or does it get done automatically when you partition the main section?  I think I'll allocate 30 gigs main, and then the max of 1GB swap.  I have 2GB RAM.

---

### Post by FishBoi on 2007-06-01
> **Lucifiel said:**
> Hmmm... Fishboi, maybe after installing Ubuntu, you can try this. Disabling Jmicron drivers and forcing Ubuntu to select a better set of drivers?
I've heard that some managed to get that working out and thus allow their Pata drives to be detected.
Edit: This is what I found. It worked for Dapper/Edgy and might not work for Feisty. What you have to do is blacklist the JMicron drivers(which're the more primitive versions) and force Feisty to use the drivers from libata. If you succeed in blacklisting the drivers, then you could very likely get your PATA to be detected. 
[http://ubuntuforums.org/showpost.php?p=1947596&postcount=262](http://ubuntuforums.org/showpost.php?p=1947596&postcount=262)
Also, this post does mention some interesting stuff about the IDE option which is supposed to be enabled all the time. And about how it was actually off and disabling RAID enabled IDE again. 
[http://ubuntuforums.org/showpost.php?p=2518196&postcount=297](http://ubuntuforums.org/showpost.php?p=2518196&postcount=297)


This could also work.  A total noob question first - when I startup with the LiveCD, does a new install take place each time??  ie. if I go into the desktop, before I click install, if I edit my "config files" (wherever they are), does it save it somewhere on the machine?, or if I exit without a full install, does everything get reset?

I need to answer that for learning purposes, and also where I'm going with it is to see that if I edit the drivers, will it detect the IDE drive immediately, or do I need to reboot?

Thanks!

---

### Post by FishBoi on 2007-06-01
> **The Noble said:**
> If you do decide to disable the jmicron driver after you are done with the install (this implies that you install ubuntu to the first hard drive), you can use gparted (on the live cd ONLY, do NOT use the installed ubuntu system with gparted) to copy the installed ubuntu partition onto the the second hard drive. You may have to mess with fstab, but we can do that later. Let's first see if we can have feisty find the hard drive before the install.

Thanks.  I'll make note when we get going.

---

### Post by FishBoi on 2007-06-01
> **Lucifiel said:**
> Well he can probably try disabling Raid and see what happens, if he hasn't tried that already.
From what I know, he doesn't need that feature as he's using a SATA and PATA.

I dont have RAID enabled.  In my BIOS, its setup as standard IDE.  Reading your comments now about how to tweak the drivers.

---

### Post by FishBoi on 2007-06-01
Ok thanks guys.  I think I might just get a second HD (only $80).  I lose time everyday when I come to work and read up about possible solutions, only to figure out they dont work at night.  Thats then another 24 hour cycle to get things right, and I'm just losing days.

I read those links regarding PSATA, and that guy had a heck of a time sorting it out.  Cant believe that was June 2006, and the issue wasnt resolved with Ubuntu 7.04.  Are they out of their minds?  No C2D mobos natively support Ubuntu.  Fricken insane.  1 year later and a new release ???

If Linux has any hope of a future against the big daddy Microsoft, they will definately have to become more user friendly, as well as incorporate a fully intergrated GUI.  Code is great for those who are literate and are enthusiasts.  Definately keep that as part of the core setup going forward.  For beginners, its never gonna work.  Mass adoption will never take place with this situation, my $0.02

---

### Post by Lucifiel on 2007-06-01
Fully integrated GUI may not work 'cos many computer settings are usually quite delicate. 'Cos sometimes the GUI does not always enable the options you wanted or it enables options you did not choose or there are certain things(sometimes BIOS) that have to be configured which the GUI doesn't always warn about. 

I've had drivers implement the wrong options because the detection didn't work out well enough(supposedly this was caused by a Windows patch/update) and which caused me to have to reinstall Windows 3 hours after I just installed it. 

Though of course, much needs to be improved on so users get better output than some "standard error message" which you got. In such a respect, it's no different than some of Microsoft's Event ID messages. Sometimes, the message is so ambiguous that it could be an entirely different matter. 

And hopefully, Xorg 7.3 will resolve many "detection" problems. Right now, Feisty uses 7.2. Xorg = the system which receives input from your hardware and displays everything on your LCD/CRT and so on. 

With every new release of a software, something is bound to break. A standard rule to bugtesting is to assume that anything and everything can and will break, even if none of those components are related to one another. And this applies even if the problem has already been fixed in a previous release. 

Yet, if the developers were to try and spend their time looking for all the bugs, it'd set Canonical back by many years because we're talking about lot of "possible issues and causes" and over 1 million lines of coding here. This is why many games and software often release bugfixes after a release. Because complicated code is rarely perfect and there's always something breaking once you change or implement something. 

However, us end users can help by bugtesting the alpha/beta releases of Ubuntu and filing a bug report. :p That way, the developers will know that _____ is breaking and provided you give them accurate information, they'll give a shot at duplicating the problem and fixing it. 

P.S. I do know that Mark(the founder of Canonical) does get onto irc. Go learn more about Linux and then you can I dunno... complain to him? :P

---

### Post by FishBoi on 2007-06-01
> **Lucifiel said:**
> P.S. I do know that Mark(the founder of Canonical) does get onto irc. Go learn more about Linux and then you can I dunno... complain to him? :P

Thats a good idea.  I could try reach him, but not to complain, but to encourage the man!  I ordered my new HD.  En route.  Probably will be here on Monday.  Have a nice weekend peeps.

PS.  Plz dont lose interest in my cause just because things are going slow.  I'll get this right.
PSa. Where do you log a report or get a ticket number for a prob.  I wanna make them aware of the JMicron issue.

---

### Post by Lucifiel on 2007-06-01
Oh, you can't PM him on IRC but you can find him under the nick of "sabdfl" on Freenode. :p :p I actually said "wow" and thanked him the other day. It was pretty sweet that he replied courteously and not lambasting me like some people on the internet do. 

The url for filing bugs is at [http://bugs.launchpad.net](http://bugs.launchpad.net) 

However, I suggest you search for the issue first as I'm very sure many others have already filed similar bugs. The only issue is that sometimes, it takes a very long time to get a device driver working. (@#$#@$ Hardware manufacturers and Microsoft.) 

Oh don't worry. Go enjoy your weekend. :)

---

### Post by The Noble on 2007-06-01
Wow, you certainly are progressing a lot faster than I did when I first started. And don't worry, we won't lose interest in helping you; I even have this as my main tab in firefox and never leave it. Now to answer your posts:

> 
This is key - is there even the smallest risk of losing my data on C: ? I cannot afford to lose my pictures files etc. If there is the smallest chance, I cannot take it. Reading on ....


Yes, there is a likely hood of you losing data, although it would probably be from user error rather than the partitioner. Also, in one of you later posts you ask about the unmovable files at the end of a defrag. I found the solution here:

[http://www.linuxquestions.org/questions/showthread.php?t=459829](http://www.linuxquestions.org/questions/showthread.php?t=459829)

It should answer any of your problems. I do recommend a backup, however. This would be a great time to buy a backup hard drive. I got one a while ago, and it is quite valuable. You can buy a 320 gig backup for 150 USD. 

> 
Do you need to setup the swap partition too, or does it get done automatically when you partition the main section? I think I'll allocate 30 gigs main, and then the max of 1GB swap. I have 2GB RAM.


The swap is automatically partitioned if you use the ubuntu utility to do it. I usually have a backup partition that allows me to reinstall without losing most of my personal stuff. The drive is a 60 gig; 15 go to the / partition (the equivalent of C:/), 1.5 goes to swap, and the rest is a /stuff partition. If I ever reinstall, I use gparted to remove the / and swap partitions and just auto install in the remaining space. The /stuff partition can just be remounted when I feel like it. What is nice is that the /stuff partition can be mounted as the /home partition. This would save you from having to reinstall WoW after every install. Ask if you want to do this, otherwise it's gain is minimal for you now.

> 
This could also work. A total noob question first - when I startup with the LiveCD, does a new install take place each time?? ie. if I go into the desktop, before I click install, if I edit my "config files" (wherever they are), does it save it somewhere on the machine?, or if I exit without a full install, does everything get reset?


The liveCD works by "installing" to the RAM on boot up. The programs are accessed when you need them from the CD, but the core system is on the RAM (the kernel and X). When you install using the liveCD, it just copies everything from RAM and the CD to the hard drive. If you do not install and pull out the CD, nothing will have been saved to the hard drive. 

> 
If Linux has any hope of a future against the big daddy Microsoft, they will definately have to become more user friendly, as well as incorporate a fully intergrated GUI. Code is great for those who are literate and are enthusiasts. Definately keep that as part of the core setup going forward. For beginners, its never gonna work. Mass adoption will never take place with this situation, my $0.02


Yes, everyone in the community realizes exactly what you are talking about; sadly, companies rarely make drivers for linux as we are a fringe 2% of computer users. That is growing, though. If you have noticed the news lately, dell is starting to ship ubuntu with some of its computers. Just go to dell.com and refresh a few times to see the banner. What may hearten you is that the progress the open source community is making is so staggering that when vista +1 comes out, we will have fixed almost all of the major usability issues. Things are coming together, and even the bigger companies are starting to see that. Sadly, you have one of the few buggy pieces of hardware that plagues the community, so please see that this is not a regular thing. All of my laptops have required no fiddling to get working at all, so see that the jMicron thing is unusual. 

All these questions are exactly what you should be asking, and I am really surprised how fast you are learning. Good job. Next week, I have the possibility of tampering with my desktop to see if I could get a set up similar to what you are asking for. It has a pentium 4, 1 gig of RAM, and an ATI x700 coupled with the integrated intel graphics card. I could try to get 2 instances of enemy territory running if I find the time to complete such a task. While you get feisty installed, I try to head off any problems further down the road with dual desktops. That should help you in the long run. God, this is going to be fun...:popcorn:

---

### Post by FishBoi on 2007-06-01
Cant wait till my HD gets here.  Breaking news, released 20 min ago.  Wonder if this will help my quest:

[http://www.tgdaily.com/content/view/32295/118/](http://www.tgdaily.com/content/view/32295/118/)
New AMD catalyst driver adds DX10 support for Radeon HD 2900 XT graphic cards        
Hardware  
By Wolfgang Gruener  
Friday, June 01, 2007 13:24  
Recommend article:Sunnyvale (CA) &#8211; AMD has released the fifth driver upgrade for its Radeon graphics card family.

Version 7.5 introduces the ATI DirectX 10 driver for single-card and Crossfire configurations of the Radeon HD 2900 XT. DX10 will work in 32-bit and 64-bit Windows versions for a single-card system, but only in 32-bit in Crossfire installations, AMD said.

Additionally, there is a usual array of performance improvements that go along with the driver release. AMD claims that OpenGL running with anti-aliasing and anisotropic filtering is improved for the Radeon X1950 XTX under Windows Vista. Cards with this chip are estimated to see performance gains of up to 18% in Doom 3 and Quake 4 as well as more than 15% in Prey. The Radeon X1950 Pro and Radeon X1650 XT also see improvements in Doom 3 and Quake 4 up to 14.1% at higher resolutions with anti-aliasing and anisotropic filtering enabled, AMD said.

**_[SIZE="5"]The new Linux driver [/SIZE]_**adds an updated version of the Catalyst Control Center. According to the manufacturer, the software now includes 3D settings which can enable and disable various 3D features in graphic-design applications, CAD applications, and games. There are also new display settings, color settings, and information about the current graphics hardware and software configurations.

The 7.5 driver can be downloaded from AMD&#8217;s website at ati.amd.com

[[IMG]http://img509.imageshack.us/img509/1723/ccclinuxpd9.th.jpg[/IMG]](http://img509.imageshack.us/my.php?image=ccclinuxpd9.jpg)

---

### Post by gregbl on 2007-06-01
I skipped a lot after the first page, So sry if I say whats been said.

You could download VMServer, put another install of Umbuntu on it. And run Wow off of it and your pc.

Now, I don't know how you would get the mouse and keyboard to work. And, I think wow would be so slow.

But it could work.

---

### Post by Lucifiel on 2007-06-01
Errr... to gregbl:

Virtualisation does not support 3d, you know?

To fishboi:

good luck, man! :D

---

### Post by The Noble on 2007-06-01
There are some virtualization suites which allow 3d, but that would be really horrible in terms of performance. For 1 just one instance of it running. That would not solve any of the problems we are trying to fix at all. Thanks for the suggestion gregbl, but read the first post again and you'll see what we are up against. It's a tad more complicated. 

Fishboi, I don't think the driver will be a revolution over previous versions, but it I may be incorrect. I think the problems are all going to extend to how the fglrx driver interfaces with X, not some gui that will help configuration. I may be wrong though, so we wil see when your drive comes in.

---

### Post by The Noble on 2007-06-02
I'm at my other house and I have access to my Desktop. I am downloading feisty now and should install it in an hour or two. Let's see how far I can get.

---

### Post by Lucifiel on 2007-06-02
Awesome, dude! :D

Make sure to tell us how it goes! :) 'Cos that way, you can help him out easily.

*goes to get some Milo + cake* I am a sucker for cakes... ahahaha.

---

### Post by Lucifiel on 2007-06-02
To fishboi: And man, you sure are a fast learner. :D It's actually pretty easy to learn how to use Linux. In fact, I already experimented a little with virtualisation and have compiled simple programs and got them to run. You'll find yourself picking up plenty of commands in no time. 

If anything goes wrong, I hope someone can help you with the installation 'cos I still don't have my RMAed hdd yet. :/ I could load the Ubuntu Livecd but it's really slow. :p

---

### Post by FishBoi on 2007-06-03
To The Noble - let us know how it goes buddy!  I'll be eagerly awaiting your results.  According to NewEgg tracking, I should get the HD tomorrow morning.

I found this total bargain, and actually regret buying my 320GB Seagate Barracuda for $80 after I found this.  Check out this bargain.  You guys have got to get one, LOL!

[http://www.buy.com/prod/cavalry-500gb-3-5-7200rpm-16mb-usb-2-0-external-hard-drive/q/loc/101/203268362.html](http://www.buy.com/prod/cavalry-500gb-3-5-7200rpm-16mb-usb-2-0-external-hard-drive/q/loc/101/203268362.html)

---

### Post by The Noble on 2007-06-03
I finally have the base installation down, and I am planning my further steps. I don't feel like downloadin everything again, so I'll take it nice and slow. I should be able to start the process today or tomorrow. I'll have a friend coming aver and it would be fun to show him the dual computer. First, I need to find an old crt somewhere.

Fishboi, good job on the buy! I bought a backup a few months ago for the same price and its only a 180 Gig! Now I'm off to find a monitor.

---

### Post by The Noble on 2007-06-03
OK, I pulled over my other monitor and I am trying to get it up and running, but my computer doesn't see my integrated 915G intel. You guys have any clue on how to get it up and running?

---

### Post by FishBoi on 2007-06-03
Sounds good buddy.  Im eager to see if you get it right.  I found a 20" Sony CRT in San Jose for $20 incase you need one.  Bulky, but its 20" and really cheap.
[http://sfbay.craigslist.org/sby/sys/342907909.html](http://sfbay.craigslist.org/sby/sys/342907909.html)

Are you and your friend hoping to get a dual setup running for gaming, or is it just for fun?

Anyway, cant wait to get my HD tomorrow.  Will install it tomorrow night and let you guys know how the Ubuntu install goes.  I think it will be fine, the next hurdle being the ATI driver installation.

1) Get Ubuntu running
2) Get the ATI drivers working
3) Get Wine to work
4) Try WoW, single instance
5) Try get the multiple X-server setup running
6) Make sure the inputs are configed flawlessly
7) Test dual instances of WoW

Have a nice weekend team!

---

### Post by FishBoi on 2007-06-03
> **The Noble said:**
> OK, I pulled over my other monitor and I am trying to get it up and running, but my computer doesn't see my integrated 915G intel. You guys have any clue on how to get it up and running?

LOL - simultaneous post.  Glad you got a CRT.  Let me read up on the integrated card.  When you say "cant see", do you mean that Ubuntu doesnt recognize it?

What happens if you download the drivers and try install it anyway, see then if the OS picks it up?

---

### Post by FishBoi on 2007-06-03
Not sure if this will help, but PM this guy to ask him about the driver setup (how he got it running):
[http://ubuntuforums.org/showthread.php?t=395214&highlight=915G+intel](http://ubuntuforums.org/showthread.php?t=395214&highlight=915G+intel)

---

### Post by The Noble on 2007-06-03
I've gotten a little further, but the setup is missing something that requires a little more finnese than I have. Here are the important sections:

```

Section "Device"
	Identifier	"ATI RADEON X700 PRO"
	Driver		"ati"
	Screen          0
	BusID		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier      "Intel"
	Driver          "i810"
	Option          "MonitorLayout" "CRT,LFP"
#	Option          "DevicePresence" "true"
#	Option          "UseFBDev"
	Screen          1
	BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor1"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Generic Monitor2"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X700 PRO"
	Monitor		"Generic Monitor1"
	DefaultDepth	24
       SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier      "IntelMonitor"
	Device          "Intel"
	Monitor         "Generic Monitor2"
        SubSection "Display"
		Depth	24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

X doesn't crash anymore, but the second screen is not responding. At least I have a base to work from now!

---

### Post by FishBoi on 2007-06-03
Wow, so u got the second screen up and running at least.  Awesome.  Do you have the multiple X-servers setup yet?

Are you gonna try MPX?
[http://www.youtube.com/watch?v=0MUOn_nJmRA](http://www.youtube.com/watch?v=0MUOn_nJmRA)

---

### Post by The Noble on 2007-06-03
Sorry, I wasn't clear. The second screen is **not** working. But at least my system is not crashing due to the extra xorg.conf modifications. It seems like my system is not detecting my 915G Intel card though. 

```

brian@btubb3:~$ lspci|grep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
...

```

Looks like it is missing the Intel card. I'm going to do some more research though.

---

### Post by Dylnuge on 2007-06-03
Hello.

Have not posted in this thread in a little while, I was away this weekend. Looks like progress is being made :). I understand your worry about getting a second hard drive, however, if done right, there should be no issue with partitioning the first. (Actually, if you move around the Windows partition or resize it there is a risk, unless you know what you are doing).

Good luck. Sorry Ubuntu has had some troubles, but I hope everything starts to work out. Still reading what I missed, but I will jump back in soon.

---

### Post by The Noble on 2007-06-03
Dylnuge is correct. I resized my very full windows hard drive and had no problems (after I defragged). There is no definite need for another hard drive, but it would help.

On to my dual head setup. I ran into a little problem that may be very easy to fix. Or it may not. When I have my ATI card in, the intel Integrated card is automatically turned off. This means I have access to only on Graphics card at a time. I really don't want to go buy a pci graphics card, as I am young (17) and don't have the money. I am going to do some more research. If it can be solved, this should be a really easy set up. I'll keep you guys posted.

---

### Post by The Noble on 2007-06-03
Wow, Intel really screwed the pooch on this one.

> 
From [http://www.intel.com/support/graphics/intel915g/sb/cs-013595.htm](http://www.intel.com/support/graphics/intel915g/sb/cs-013595.htm)
...
The GMCH graphics engine is incapable of operating in parallel with an external PCI Express* graphics device.
...

Essentially, I can't use my PCI-E graphics card with an integrated card. That's really a pisser. I was totally depending on this for the second card. I really want to know what technical limitation just screwed me over, as I can't think of anything that conflicts between my two cards. If I am really lucky, I may have a pci graphics card somewhere around my house. Otherwise, I may buy a 10 dollar card from a used store. Otherwise, I am not going to be able to complete the dual head setup. Bummer. Time to start looking...

---

### Post by The Noble on 2007-06-03
No luck, guys. All the video cards in the house are AGP. It may be a long shot, but there is a white plug on my graphics card that I think is a Display Port. I need to look it up, but I may be able to find a adapter for my second monitor. Don't get your hopes too high though.

EDIT: Ok, I actually did some research on the second port and found that it was a DVI connection. Luckily, ATI was kind enough to have a DVI to VGA plug in the box it came in. So, right now I have two screens both with the same desktop. I want to see if my graphics card can take two instances of Enemy Territory with the radeon driver. I'm back in business boys (and girl).

---

### Post by FishBoi on 2007-06-04
> **The Noble said:**
> No luck, guys. All the video cards in the house are AGP. It may be a long shot, but there is a white plug on my graphics card that I think is a Display Port. I need to look it up, but I may be able to find a adapter for my second monitor. Don't get your hopes too high though.

EDIT: Ok, I actually did some research on the second port and found that it was a DVI connection. Luckily, ATI was kind enough to have a DVI to VGA plug in the box it came in. So, right now I have two screens both with the same desktop. I want to see if my graphics card can take two instances of Enemy Territory with the radeon driver. I'm back in business boys (and girl).

Hey Noble! - a new week and the quest continues.  How did you make out in the end with the dual DVI outputs.  Did you get it right?  HD arrives this morning.  Will let you know how everything goes.  Let me know where you are in the process.  Maybe I can read up on it and send you some info.

Chat later,

---

### Post by FishBoi on 2007-06-04
Found this on Digg.com - looks really cool.  Im sure there are thousands of useful apps out there that can really make Ubuntu worth it.  Even more of a reason to get this right.

I can even liken it to WoW - it was fun, but when I found out about the modding community, the whole gameplay setup changed drastically.  I had so many fantastic tools that just made the whole experience a lot more enjoyable.

[http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)

---

### Post by The Noble on 2007-06-04
OK, I got really far. I had a setup that showed my desktop across the two screens (as in I now had a 2048x768 screen). It was working well and I was adding the extra keryboard and mouse. Then I ran into problems. My ubuntu install must have some stuff messed up, as I could not restart or play games. It really slowed down. I'm going to reinstall for a fresh system and I'll redo most of the stuff. Hopefully I don't mess up again.

---

### Post by FishBoi on 2007-06-04
> **The Noble said:**
> OK, I got really far. I had a setup that showed my desktop across the two screens (as in I now had a 2048x768 screen). It was working well and I was adding the extra keryboard and mouse. Then I ran into problems. My ubuntu install must have some stuff messed up, as I could not restart or play games. It really slowed down. I'm going to reinstall for a fresh system and I'll redo most of the stuff. Hopefully I don't mess up again.

Ahhhhh no buddy, what a pity.  You're getting there though!  Keep at it.  We all knew it wouldnt be easy.  My HD has arrived.  Will let you know how it goes tonight.

Could you perhaps list the steps you took to get where you are so I can implement something similar and not waste too much time.  How are you configging multiple inputs?  How did you get two mouse cursors going?

Thanks bud.  Chat tonight again.

---

### Post by The Noble on 2007-06-04
It's not too bad to set up. I didn't have the two mouses set up though. I'm not at that point yet. I was part way through this guide posted earlier.:

[http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)

Before you try to go too far, let's just make sure your install is smooth. Your set up is different than mine, so don't follow what I am doing. Use this guide:

[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

It should be more suitable for what you are doing. I'm just trying to get it working before you do so I may adapt to help you. Good luck on the install.

---

### Post by Dylnuge on 2007-06-04
If it goes well tonight, and you can install, here are some tips for getting set up (you will probably want to settle in before working on your WoW):

1. Change around your themes. Get your desktop to look the way you want. Check [art.gnome.org]("http://art.gnome.org") for some awesome wallpapers and themes for GNOME.

2. Install the software you want. Check out [this list]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html") for some Linux equivilents.

3. Get the things that make your computer yours up. Specific background? Files? Fonts? etc.

4. Start learning the new software. Evoloution, OpenOffice, Firefox, GIMP, and more may be new to you.

5. Visit [www.linuxcommand.org](www.linuxcommand.org) and learn the terminal (You don't need to do the scripting lessons unless yoiu want to). I recommend learning this early on so you will understand it, especially since you are probably going to work with it to get your dual input set up.. In Feisty GNOME, the Terminal is located under Applications -> Accessories -> Terminal.

Also, some people use applications like Automatix ([www.getautomatix.com](www.getautomatix.com)) to eaisly install a bunch of software. I don't have anything aginst this, but I no longer use it. You may notice that there are a lot of options for applications on Linux. Many will be "recommended" by coming with the system-OpenOffice and GIMP both have alternitives for example. Sometimes, you may not know which to choose. You can ask around, but commonly the mix of answers turns into an X vs Y war more then helpful discussion. I would recommend trying everything, and choosing what is best for you.

Good luck.

EDIT/PS: If you like, you could try some software before the install. GIMP, OpenOffice, and Firefox come for Windows as well.

---

### Post by FishBoi on 2007-06-05
Hey guys, 

I managed to install my HD last night - it took forever.  The P5W DH is a tough board to work with when it comes to multiple HDs.  For the rest, its a breeze.  I had to in the end disable the JMicron, remove the other IDE, install the new SATA, and partition etc.  Took much longer than expected, and I only have a few hours in the evening as I get in usually pretty late.

Anyway - short of it is that I got Ubuntu installed.  It was so easy and real fast.  Gives me the option to boot into XP or Ubuntu when I startup.  Goes in, no prob.

I didnt have time last night to go further, but am excited to get back tonight.  I downloaded the ATI drivers just to give it a go.  Gave some error message when I double clicked on the install package.  I think its a bin file (.iso equivalent?).  I prob need to unpack it, and might install the program I recommended earlier to do it.

Anyway, we are getting there.  Will keep you updated.  Anyone else make traction?

---

### Post by dfreer on 2007-06-05
The ati drivers probably need to be chmod to 755, so that you can execute them. However, I don't quite remember if this has been mentioned on this thread (11 pages! jeez lol), but you are probably going to run into problems using an ATI card. Try using the Restricted Drivers Manager to install the correct driver first, and then make sure you are using the fglrx driver and direct rendering is enabled. Otherwise you won't get WoW to work (and even if you do get the drivers installed, from what I hear you may not be able to play 3D games smoothly enough with that ATI card).

But you guys have definitely been working hard on this project, I'm not going to be surprised if this doesn't slow you down! Good Luck!

---

### Post by FishBoi on 2007-06-05
> **dfreer said:**
> The ati drivers probably need to be chmod to 755, so that you can execute them. However, I don't quite remember if this has been mentioned on this thread (11 pages! jeez lol), but you are probably going to run into problems using an ATI card. Try using the Restricted Drivers Manager to install the correct driver first, and then make sure you are using the fglrx driver and direct rendering is enabled. Otherwise you won't get WoW to work (and even if you do get the drivers installed, from what I hear you may not be able to play 3D games smoothly enough with that ATI card).

But you guys have definitely been working hard on this project, I'm not going to be surprised if this doesn't slow you down! Good Luck!

dfreer - do you have some pointers on how to get the ATI drivers setup (steps).  I know its in this thread somewhere, and I will also Google it tonight.  Some keywords will just help my search.  Thanks!

---

### Post by dfreer on 2007-06-05
First try System > Administration > Restricted Drivers Manager, see if you can install it that way (simply check the box, hit apply, then hit ok).
Sometimes Restricted Drivers Manager doesn't always see the graphics card, and depending on your card you may find the open-source radeon driver may outperform the fglrx driver.
I don't have an ATI card, can't quite remember how to install them. But I can tell you what to look for:
(1) check and make sure it is using the right driver (either radeon or fglrx) instead of MESA
```
glxinfo | head
```
(2) also make sure direct rendering is working (needed for 3D games)
```
glxinfo | grep rendering
```

If it does end up using the MESA driver, I think you have to end up blacklisting it in the kernel. Like I said, I don't have an ATI card but hopefully this info can help you get yours installed. it should be using the radeon driver on a default install, and if that driver works for you in WoW then don't change anything.

---

### Post by The Noble on 2007-06-05
Using the restricted drivers manager worked perfectly for me. All that is required is a restart when it's done.

It's good to hear that you got the install down; it's nice to hear that you didn't have any more problems. I guess I need to haul in my second monitor and try this again. I took yesterday off because I was tired of xorg, but I'm ready again.

Time to get down to business.

---

### Post by Sammi on 2007-06-05
I've experienced a few hiccups with the restricted drivers management application. In it's defense I will add that it is a very young app.

To the best of my knowledge, Alberto Milone's graphics card driver installation application, called Envy, has a longer history. And it has faired me better in genaral usage, so I can only recommend it:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)


Anyway I find this to be the premier resource for Ubuntu graphics card driver installation instructions and info in general: [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Hope this is useful :D

---

### Post by dfreer on 2007-06-05
> **Sammi said:**
> I've experienced a few hiccups with the restricted drivers management application. In it's defense I will add that it is a very young app.

To the best of my knowledge, Alberto Milone's graphics card driver installation application, called Envy, has a longer history. And it has faired me better in genaral usage, so I can only recommend it:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)


Anyway I find this to be the premier resource for Ubuntu graphics card driver installation instructions and info in general: [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Hope this is useful :D

envy tends to break restricted drivers manager (I think it's complaining about a user modified xorg.conf file), so it is probably better to try restricted drivers manager first, and then use envy if restricted manager doesn't work IMO.

---

### Post by Sammi on 2007-06-05
> **dfreer said:**
> envy tends to break restricted drivers manager (I think it's complaining about a user modified xorg.conf file), so it is probably better to try restricted drivers manager first, and then use envy if restricted manager doesn't work IMO.Of course. I recommend that myself :D

Envy is just a very nice alternative if the restricted manager gets the hiccups. That's what I meant to imply :p

---

### Post by FishBoi on 2007-06-05
Hi guys,

I've got a lot of professional work that I have to get done tonight.  Not sure how much time I have.  Going through the setup for my x1900xt now.  Cool that FireFox is up and running.  Soon I wont need big bad old Windows, LOL!

FYI : error from the ATI file.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Could not open the file /home/Desktop/at…ler-8.37.6-x86.x86_64.run.

---

### Post by FishBoi on 2007-06-05
Update - I installed the restricted ATI driver, no probs so far.  Reboot went well.  Gonna try wine now.

---

### Post by Lucifiel on 2007-06-05
Whoa, glad to see the more experienced folks are helping you out fine. :)

May it go well. Then, perhaps, this can be used to promote a capability of Ubuntu(and maybe other distros if this can be applied to them), huh? :D

---

### Post by FishBoi on 2007-06-05
Ubuntu is no walk in the park.  This thing is really a witch to install.  I know it takes time, but I cant seem to "visualize" the programs I install etc.  Where is the summary of all the apps I have installed?  How do I see what I've done.

Ie. just installed wine through the terminal.  Where is it now?  How do I find out what I've added/removed?

1) got the ATI restricted driver installed
2) installed wine
3) copied WoW folder across
4) Now how do I get it going?

Trying this guide but its giberish: [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

If I dbl click on WoW.exe, get this message:

Cannot open /home/Desktop/World of Warcraft/WoW.exe: No application suitable for automatic installation is available for handling this kind of file.

---

### Post by FishBoi on 2007-06-05
PS. I know where the add/remove tab is under applications.  Working through that.

---

### Post by FishBoi on 2007-06-05
Guys, assuming I have Wine installed properly (before tweaks and patches), how do I get it to run WoW?

If it doesnt run properly, then I can go back and try the patches (ActiveX control, other registry tweaks etc).

Any ideas?  Thanks.

---

### Post by FishBoi on 2007-06-05
Holy sack!  Applications/accesories/wine file, found my desktop folder, and dbl clicked on WoW.exe.

WOOOOHOOOOOOO!  It open (fastest open Ive ever seen!).  The graphics are all messed up, but it worked, LOL!!!!

Awesome guys.  Now I gotta fix those graphics.  BRB!

---

### Post by Lucifiel on 2007-06-05
Hmmm... if Wine doesn't work, maybe you can also give Cedega a shot. It's commercial but you can always just suscribe for the first month.

---

### Post by MrMatt2532 on 2007-06-06
Saw that you were looking at a gentoo guide. While most of it is probably the same, i would recommend checking out this guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft). Worked well for me and has the opengl tweaks that you are looking for.

---

### Post by Sammi on 2007-06-06
> **MrMatt2532 said:**
> Saw that you were looking at a gentoo guide. While most of it is probably the same, i would recommend checking out this guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft). Worked well for me and has the opengl tweaks that you are looking for.That is supposed to be our first recommendation. It's our Ubuntu community WoW/Wine howto, and it does have all the most useful info in it.

@FishBoi
 I wouldn't really recommend the Gentoo wiki as a good alternative. If you want an alternative to our Ubuntu community guide, you should try [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

I've been working on both our guide and the wowwiki one.

[quote=FishBoi]I know it takes time, but I cant seem to "visualize" the programs I install etc. Where is the summary of all the apps I have installed? How do I see what I've done.

Ie. just installed wine through the terminal.  Where is it now?  How do I find out what I've added/removed?[/quote]The best visual application for handling package management is Synaptic. You find it in system -> administration -> synaptic

Initially it is a logical and straight forward application to start using for the first time. But it is also a very powerfull gui based application and it can take some time get to know all the advanced functions.

---

### Post by FishBoi on 2007-06-06
> **MrMatt2532 said:**
> Saw that you were looking at a gentoo guide. While most of it is probably the same, i would recommend checking out this guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft). Worked well for me and has the opengl tweaks that you are looking for.

K thanks.  There are 13 pages of text right now, so its hard to keep track.  I need to go back and read everything again.

This guide looks sweet.  Real easy to understand.  Its hard for me to wrap my hands around the way Fiest is laid out.  That will come with time I know, but they should really follow the basic Windows layout to make the transition easier (ie. took this noob 5min to find the trash can).

Anyway, digging it so far.  Im just so glad I got WoW to run, so at least I know it works.  Just got to sort out the resolution and graphics issues.  Then move on to MPX.  Noble, did you come right?

---

### Post by FishBoi on 2007-06-06
I am also looking forward to running some FPS benchmarks to see how they differ from Windows with the exact same hardware I have.  Anyone know of an application that can measure FPS in games, recording to an Excel file equivalent?

I might me able to run my FPS program using wine too.

---

### Post by FishBoi on 2007-06-06
Another guide if anyone needs it: [http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)

---

### Post by FishBoi on 2007-06-06
**_Dumb question_** - How do you create icons on your desktop so that you dont have to open the terminal (ie. a WoW Instance 1 icone that automatically starts WoW using wine, $ wine /WoW/wow.exe etc.

Thanks,

---

### Post by FishBoi on 2007-06-06
FYI for noobs - neat getting started guide: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by dfreer on 2007-06-06
> **FishBoi said:**
> **_Dumb question_** - How do you create icons on your desktop so that you dont have to open the terminal (ie. a WoW Instance 1 icone that automatically starts WoW using wine, $ wine /WoW/wow.exe etc.

Thanks,

You'll need to create an *.desktop file, and if you wanted to you can also put the file in /usr/share/applications, and as long as you made it right it will show up in your applications menu. 
Here's the code for one wine automatically made for Steam:
```
[Desktop Entry]
Name=Steam
Exec=env WINEPREFIX="/home/**$USER**/.wine" wine "C:\\Program Files\\Steam\\steam.exe"
Type=Application
Path=/home/**$USER**/.wine/dosdevices/c:/Program Files/Steam
Icon=75e1_steam.0
```

Here's one I created for the snes emulator that correctly places the shortcut in Applications > Games:
```
[Desktop Entry]
Version=1.3
Encoding=UTF-8
Name=zsnes32
Name[en]=zsnes32
Name[en_US]=zsnes32
GenericName=Super Nintendo Emulator (32-bit)
GenericName[en]=Super Nintendo Emulator (32-bit)
GenericName[en_US]=Super Nintendo Emulator (32-bit)
Comment=Play Super Nintendo Games using ROM's on AMD64 systems
Exec=/usr/local/games/zsnes32/zsnes
Terminal=false
Type=Application
Icon=/usr/share/pixmaps/zsnes32.png
Categories=GNOME;GTK;Application;Game;

```

---

### Post by Sammi on 2007-06-06
@dfreer
Now you are just trying to scare the noob. There's no need to go edting text files in order to make shotcuts.

There is a neat little gui based app for creating shotcuts, which can be found right here: system -> preferences -> menu layout

For making a shortcut on the desktop you just right click on an empty space on the desktop and choose "create launcher". From there you choose a name and icon for the shotcut, and then you just write the same command in to the "command" boks, that you would write in the terminal to launch the application you want.

---

### Post by dfreer on 2007-06-06
> **Sammi said:**
> @dfreer
Now you are just trying to scare the noob. There's no need to go edting text files in order to make shotcuts.

There is a neat little gui based app for that for creating shotcuts, which can be found right here: system -> preferences -> menu layout

For making a shortcut on the desktop you just right click on an empty space on the desktop and choose "create launcher". From there you choose a name and icon for the shotcut, and then you just write the same command in to the "command" boks, that you would write in the terminal to launch the application you want.

.... OMG. I totally forgot about that :oops: 

Yeah, do it that way. 

I'm so used to just making them myself, didn't even think about a GUI way of doing it lol.

---

### Post by FishBoi on 2007-06-06
Guys - the edits worked.  Im in WoW and its running fine.  I need to get sound.  Any ideas?  I dont have sound in Ubuntu yet (onboard Realtek Audio card on the P5W DH).  How do I check if I have a sound driver installed?

Thanks again.

---

### Post by FishBoi on 2007-06-06
Sweeeeeeeeeeeeeet!  Sound is running!  Guys, no I gotta get the dual x-server running.  Noble, where are you man???

---

### Post by FishBoi on 2007-06-06
Oh guys - just when you think you're making traction.  I installed the latest WoW patch, and now the game freezes as soon as I try enter the realm.  It starts up, I select my character, everything looks good, and as soon as Elwynn Forest loads up, it freezes.

Please guys - any ideas?

---

### Post by Sammi on 2007-06-07
You should try out every relevant thing you can find here:
[http://www.wowwiki.com/Linux/Wine#Troubleshooting](http://www.wowwiki.com/Linux/Wine#Troubleshooting)

Especially this one:
[http://www.wowwiki.com/Linux/Wine#ATI_enter_game_world_crash](http://www.wowwiki.com/Linux/Wine#ATI_enter_game_world_crash)

---

### Post by FishBoi on 2007-06-07
> **Sammi said:**
> You should try out every relevant thing you can find here:
[http://www.wowwiki.com/Linux/Wine#Troubleshooting](http://www.wowwiki.com/Linux/Wine#Troubleshooting)

Especially this one:
[http://www.wowwiki.com/Linux/Wine#ATI_enter_game_world_crash](http://www.wowwiki.com/Linux/Wine#ATI_enter_game_world_crash)

**_Sammi_** - That looks like the exact fix I need.  Thanks a lot buddy.  I really appreciate it.  Your guide was really useful and I wouldnt have got this far without it.  There were many guides out there, but yours was the simplest to understand, especially for a complete noob.  Thanks for putting that together for the greater good.  You should add these links with a brief heading to your troubleshooting page.

Chat soon,

PS.  Update to everyone else - the graphics in the game (the brief seconds I could see) looked much better than before, so I think it was that sound fix that I put in, or maybe that registy edit.  A few more steps to go.

---

### Post by FishBoi on 2007-06-07
Has anyone got mutiple x servers running yet?  Should I first get a 2nd monitor working, or should I get 2 x servers working?  Which path is best?

---

### Post by bodhi.zazen on 2007-06-07
> **FishBoi said:**
> Has anyone got mutiple x servers running yet?  Should I first get a 2nd monitor working, or should I get 2 x servers working?  Which path is best?

Did I hear Multiple X Servers ?

[http://ubuntuforums.org/showthread.php?&t=271674](http://ubuntuforums.org/showthread.php?&t=271674)

~ Bodhi *loves Multiple X servers

---

### Post by Sammi on 2007-06-07
> **bodhi.zazen said:**
> Did I hear Multiple X Servers ?

[http://ubuntuforums.org/showthread.php?&t=271674](http://ubuntuforums.org/showthread.php?&t=271674)

~ Bodhi *loves Multiple X serversSeems like the guru himself decided to drop by :D

That's pretty script you've made. I'm probably going to try it out just for kicks...

---

### Post by bodhi.zazen on 2007-06-07
> **Sammi said:**
> Seems like the guru himself decided to drop by :D

That's pretty script you've made. I'm probably going to try it out just for kicks...

:lolflag:

More like "Bodhi the lazy poster who has not read through all 140 or so posts".

Let me know how that script works out for you :twisted:

---

### Post by dfreer on 2007-06-07
> **bodhi.zazen said:**
> :lolflag:

More like "Bodhi the lazy poster who has not read through all 140 or so posts".

Let me know how that script works out for you :twisted:

hmmm. Looks very interesting bodhi, I wanna go play with it now :)

---

### Post by bodhi.zazen on 2007-06-07
> **dfreer said:**
> hmmm. Looks very interesting bodhi, I wanna go play with it now :)

Enjoy, it is fun to explore to be sure. It has a great many applications.

For those who have one monitor, try this :

[http://doc.gwos.org/index.php/VirtualX](http://doc.gwos.org/index.php/VirtualX)

---

### Post by FishBoi on 2007-06-07
> **bodhi.zazen said:**
> Enjoy, it is fun to explore to be sure. It has a great many applications.

For those who have one monitor, try this :

[http://doc.gwos.org/index.php/VirtualX](http://doc.gwos.org/index.php/VirtualX)

Bodhi - Im so glad I have another great addition to this team.  Welcome and thank you for the post.  I'll be sure to crunch away at this over the weekend.  Im getting there.  

For some reason I now have multiple Ubuntu installs on my PC (asks for multiple startup options).  Not sure how I got there.  There is also another CD drive extra etc?  All screwed.  I may need to do a reformat, but its not a prob.  This time I could probably setup WoW in under 5min.

Chat soon guys.  Its Friday, wooohooooo!!!!

---

### Post by dfreer on 2007-06-07
ummm. Are they different kernel numbers, perhaps? Everytime a new kernel comes out and you update your machine, it will add two entries to your /boot/grub/menu.lst. You could post the results from:
```
sudo fdisk -l
```
and
```
sudo cat /boot/grub/menu.lst
```
We can easily tell you if you have more than one install going on.

Also, what do you mean there is an extra CD drive? any specific reason?

---

### Post by Lucifiel on 2007-06-08
> **FishBoi said:**
> Bodhi - Im so glad I have another great addition to this team.  Welcome and thank you for the post.  I'll be sure to crunch away at this over the weekend.  Im getting there.  

For some reason I now have multiple Ubuntu installs on my PC (asks for multiple startup options).  Not sure how I got there.  There is also another CD drive extra etc?  All screwed.  I may need to do a reformat, but its not a prob.  This time I could probably setup WoW in under 5min.

Chat soon guys.  Its Friday, wooohooooo!!!!

Well, I actually knew bodhi would be interested in this thread so I passed him the link. ;) 

Anyways, have fun getting it all set up. :p And best of luck, mate! :)

---

### Post by FishBoi on 2007-06-08
Cant wait to get home tonight and try get this thing finally sorted out!  Its Friday, woohooooooo!  

Hey bodhi, do you have a video clip of your setup?  Why dont you post something on YouTube, it will really help us out (+ prove to me that this actually works, LOL - with gaming I mean).  Doesnt have to be a 10 min walkthrough, but if I can actually see dual instances of _any _gaming playing, working on a single PC with multiple seats, that would just be awesome!

Some dumb questions:;
-does your code allow for a "windowed mode" X server (bare in mind I dont know how this is going to even look), or does it simply just open in full screen on the 2nd monitor (ie. Ununtu load screen and then ask for username, at the same time as the 1st screen).


Thanks,

---

### Post by hikaricore on 2007-06-08
@FishBoi

I can't imagine it would be possible/easy to do desktop recording which switching between X servers.

I also can't imagine how anyone could prove that someone didn't just splice video clips together so how would this be useful?

---

### Post by FishBoi on 2007-06-08
> **hikaricore said:**
> @FishBoi

I can't imagine it would be possible/easy to do desktop recording which switching between X servers.

I also can't imagine how anyone could prove that someone didn't just splice video clips together so how would this be useful?

1) This whole project is based on the honor system and I dont even know if this can be done yet.  Just trying to save myseld $$$ as well as other avid gamers out there.

2) He could use a digital camera to record a 1min .avi to show the setup.  Would be awesome.

---

### Post by hikaricore on 2007-06-08
That's just silly ^_^

Why don't you just try his script out yourself?  It can't hurt anything.

---

### Post by bodhi.zazen on 2007-06-08
The script is more for different layouts of one's X server. Twinview vs. Dual monitors vs. single monitor.

As far as what FishBoi is talking about, if I recall correctly, is basically dumb terminals.

I posted a how to on how to set up the terminals much earlier.

The two scripts I posted allow one to set up multiple instances of X and/or dual monitors. I am not sure if the one on dual monitors could be adapted for games, but it does lay out a separate X configuration (one for each monitor) with a shared mouse. The separate configurations run at the same time, on one x server.

Otherwise this thread is soooo long and meandering I am not sure what FishBoi is trying to do. I just threw out a few scripts ...

FishBoi, HTH =)

---

### Post by dfreer on 2007-06-08
Once again I don't know much about how to do this...
But my main concern is once you get multiple screens working, how are you going to hook up two keyboards, 2 mice, and 2 sound cards so that they work independently of each other? The only way I can see this would be to have two seperate xorg.conf files along with the 2 X servers, which wouldn't work well with a dual head video card.

---

### Post by bodhi.zazen on 2007-06-08
Like this :

[http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)

*I KNOW it is a long thread, I posted this link some time ago*

---

### Post by The Noble on 2007-06-08
> **dfreer said:**
> Once again I don't know much about how to do this...
But my main concern is once you get multiple screens working, how are you going to hook up two keyboards, 2 mice, and 2 sound cards so that they work independently of each other? The only way I can see this would be to have two seperate xorg.conf files along with the 2 X servers, which wouldn't work well with a dual head video card.

Hey guys! My sis stole the monitor for school, so I am not able to configure my system for dual head. I got kinda far, but not where I liked. I never got the dual instances of X, but I wish I still had access to that other monitor to try out bodhi's script. 

**[http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)**

This has been posted a few times and has the best description for the dual input. Here is a basic lesson guys:

[http://netpatia.blogspot.com/2006/09/multiseat-iii-xorgconf.html](http://netpatia.blogspot.com/2006/09/multiseat-iii-xorgconf.html)

Read the xorg file. Make sense? It should. He has organized his xorg to a work of art. I suggest doing exactly what he did and giving everything it's own section (that is, a mouse section, screen section, graphics card section, etc). Delete everything about the Wacom tablet, cuz that is merely annoying now. 

That's it for this post. I'll make a larger post on what I learned after this one.

EDIT: OK, no way am I going to make a post on what I think you should do. I started and got part way through an I realized that a guide on something I only partially completed would be a pain. In 1 week, I will be able to work on the computer again. Until then, I will help guide you along if you need help. if you don't have the time, wait until next week and I will make a guide once everything is working.

---

### Post by airtonix on 2007-06-09
did you run into memory problems?

my mate has a coreduo hackintosh...he need all the system to run wow at full hog.

i cannot imagine another (even crippled version of wow) running on the same machine.(even though it has two cpus).

heck my 1.8AthlonXP-1gbram-ATI7660 struggles to get 25fps consistantly.

im not feeling very positive about this idea, sorry. it can be done but the fesiability of it would only allow for scenarios like libraries....ie providing a terminal for book searches.

trust me .... try to play like this ..... and ill gank your *** in hillsbrad. muwhahahaa

(ps: adding heaps of high speed ram and second 3d card plus a mobo with high bus speeds and massiv cpu cahce will help you here)

---

### Post by dfreer on 2007-06-09
@bodhi.zazen 
Thanks for the link, I thought I had read the entire thread but I must have missed something somewhere. 
EDIT: yep, right around page 4 I believe. sorry about that

@The Noble and FishBoi
Yeah, this project is beginning to look very plausible. Very interesting indeed!

---

### Post by The Noble on 2007-06-09
This is looking very plausible, but it is looking very difficult. My main concern is the dual video card setup. As said earlier, I think the drivers may conflict. All hope is not lost, however, because if the x1900 could probably play two instances of WoW we are OK.

---

### Post by FishBoi on 2007-06-11
Hey team - this weekend was very unproductive.  I tried on Friday night for a few hours to get WoW running (freeze problem), and couldnt get it sorted out.  The troubleshooting walkthroughs seem to have all the aswers, but they didnt work on my PC.  There must be something else wrong.

I didnt have time the rest of the weekend - had to take care of some outstanding errands I've been putting off for weeks.  I'll also be travelling till Thursday but will touch base with you guys when I get back.  This project is becoming mission impossible cause there are so many variables I need to control, and I'm not fluent in code.  Let me know if you guys make any progress over the next 3 days.  I knew it wouldnt be easy, but Im stumped at such an early stage.  Two x servers etc - whooaaaa baby.

Chat soon,

---

### Post by hazen on 2007-06-11
Pardon for not having read the side threads linked to by Bodhi (which may very well include this info), but thought this link might be useful to you all r.e. multiple independent *OpenGL accelerated* X servers..

[http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.DualSeatX](http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.DualSeatX)

This could facilitate running 2 wow instances off of a single dual-head graphics card, and avoid issues involved with setting up 2 distinct 3d accelerated graphics cards.

---

### Post by The Noble on 2007-06-11
Hey, thanks hazen! The link definitely saved me over 2 hours! I had been going the wrong way and your site pointed me in the right direction. I find it interesting that XGL could be helpful in this situation... I need to set this up next week.

---

### Post by Drezliok on 2007-06-12
I look forward to see how this turns out.


This link was posted on this thread, it's full of great info on how to do this.
[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

BUT they didn't mention how to get sound to the separate heads[a term from the link]

Has anyone given any thought to the sound issues? I for one would hate not having sound.

---

### Post by The Noble on 2007-06-12
I have no clue how the sound issue will be sorted out. Maybe we can allocate each set of speakers to each X session? I truly don't know.

I do know that the Volume control can be used to choose between several devices, so each user would pick the speakers next to them. I don't think iy would be too difficult if I am correct. This will require an extra sound card, but that isn't too expensive.

---

### Post by dfreer on 2007-06-12
I'm thinking if you can get seperate X sessions (that would also have seperate user logins), then you could have one user set his sound device to be soundcard1 and the other user set the sound device to soundcard2 in the sound options, it should work (provided you have two sound cards).

---

### Post by Sammi on 2007-06-12
Aren't extra soundcards very cheap? Surely this shouldn't be the show stopper.

---

### Post by The Noble on 2007-06-12
Yes, brand new sound cards are easliy found for under 20 bucks (USD), and that's with the surround sound addition. No problems yet. Worst case scenario is no WoW sound, but i think that can be lived with.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829130001](http://www.newegg.com/Product/Product.aspx?Item=N82E16829130001)

It says it is supported by linux too.

---

### Post by Lucifiel on 2007-07-15
So, how did it go?

---

### Post by Sammi on 2007-07-16
He stopped posting. That last message was his last :(

---

