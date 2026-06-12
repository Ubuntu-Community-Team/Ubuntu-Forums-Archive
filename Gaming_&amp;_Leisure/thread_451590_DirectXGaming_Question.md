---
title: "DirectX/Gaming Question"
date: 2007-05-22
forum: Gaming &amp; Leisure
---

### Post by rdmike on 2007-05-22
Hi all,

I just installed the 64bit version of ubuntu last night. So far i am pleased with the performance and so forth but am still having some issues learning a new environment i.e. Linux. That said, I play some wargames which require little high tech resources. They are produced by John Tiller and his company HPS Simulations. In speaking with Rich Hamilton, their support guy, he mentioned the only problem he could see in running the games is the directX support. My question then is will I be able to run something like [Campaign Gettysburg]("http://www.hpssims.com/Pages/products/RifMusk/Gettysburg/gettysburg.html") in ubuntu? If so, how? I apologize if this issue has been covered already. I've tried running a forum search but what I have found deals primarily with games like WoW, CoD, and the like. These games are PBEM primarily and thus a different beast altogether. Furthermore, I am a linux boob....I mean noob hehehe and need all the help I can get to rise above the windows idiot status I currently possess, lol. Thanks in advance!

---

### Post by cogadh on 2007-05-22
You can probably play it, but you will need to use Wine to run it. Wine is an open source implementation of the Windows API on Linux, including DirectX functions. There is plenty of info on it here and elsewhere, just Google it. A good place to start is [www.winehq.org](www.winehq.org)

---

### Post by bmartin on 2007-05-22
The program used to run Windows applications in Linux is called Wine. You can grab it with:
```
sudo aptitude update
sudo aptitude install wine
```

The [Wine Application Database]("http://appdb.winehq.org/") site has a collection of games that have been tested with Wine. Unfortunately, your game isn't listed in there, so I can't predict whether it will work or not. Most simple Windows programs work almost flawlessly; results with games are varied. After installing Wine, you can double-click on EXE files to run them, just like in Windows.

If you have trouble installing the game, you might be able to copy the files from a Windows installation. There really isn't much way to tell if you game will work or not beforehand; your best bet is to try it and then post the results on the Wine site. I play the Windows version of Unreal Tournament all the time on Feisty with no problems.

---

### Post by Sammi on 2007-05-22
Remember that most PC games are written specifically for Windows and not Linux. You can't blame Linux for not supporting Windows games, when it's the game developers that choose to not write a version for Linux. They usually don't do Llinux versions for financial reasons (or lack thereof).

---

### Post by bmartin on 2007-05-22
The issue here isn't really the lack of support from video game companies, but rather the ability to run desired games.

Whether or not the game works, Wine gets better as time progresses. If it doesn't work now, it will eventually, but it's hard to tell how long it will take before it will work. The people who write Wine release a new version every two weeks; as time goes on, more software works with it. If all else fails, you can run a full copy of Windows within Linux; this approach is *much* slower and you need to have a legitimate copy of Windows, but it guarantees 100% compatibility.

Wine doesn't emulate Windows, so it's a much faster approach.

---

### Post by Sammi on 2007-05-22
> **bmartin said:**
> The people who write Wine release a new version every two weeks...
Just wanted to remark that Wine isn't really "released" every two weeks as understood in a classical sense. There is no release preparation and bug testing. The weekly "releases" are really just the same untested alpha development version one will get from downloading the development code directly from svn, only it's frozen for two weeks at a time and packaged for easy installation in different distributions.

---

### Post by rdmike on 2007-05-22
Hey all,

Thanks for the replies! I tried installing wine today from the add programs link in applications but it didn't do anything. I've installed a couple of other programs from there with no problems at all. Now, assuming this command line y'all mentioned works in terms of getting wine installed how do I install the game itself from the disk. As it is now I can put the disk in my drive but the OS doesn't see a thing there. Thanks again for the help and I apologize if these questions are silly. Your help is appreciated!

---

### Post by bmartin on 2007-05-22
There should be an icon for your CD drive on the desktop. Double-click on that and find your game's installer file. It should load just like it did in Windows if Wine is installed correctly.

---

### Post by rdmike on 2007-05-22
> This application is provided by the Ubuntu community.
Wine Windows Emulator cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.

Well, I was wondering if I should have just gone with the 32 bit version of ubuntu. Now, between games and my printer it looks like the 32 bit version is my only option. I'll download that I guess and reinstall the OS and see if that will solve the issue.

---

### Post by bmartin on 2007-05-22
I didn't realize Wine was 32-bit only. Most people I've talked to who own 64-bit processors use the 32-bit version of Ubuntu anyways. There are other issues with 32-bit software as well, like Firefox plugins and so forth.

---

### Post by Sammi on 2007-05-23
Sadly there are quite a few things that are 32 bit only and you'll probably be better of running Ubuntu 32 bit if you want to fiddle with your computer and install a lot of different things.

This page has lot's of info on using Wine: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

It instructs one to use the terminal/console for launching .exe files with Wine, but double clicking on them should also launch them with Wine if you installed it through the add/remove program.

---

### Post by rdmike on 2007-05-23
Hey all,

Thanks again for the assistance. I got the 32 bit version installed and wine installed as well. I'll be checking things out further here in a few minutes.

On another note I have been trying to get my Brother MFC 420CN printer to work with Ubuntu with no success. There are a few threads on this model but nothing mentioned has worked yet for me. I wen to the brother website and they mention deleting  a set of driver files as part of the process but when I attempt to do this the OS says I am not the root so I can't. I am the only user of this machine and did not set up a root account which I assume to be the same as an admin acount with Windows. Can anyone help walk me through this process step by step? Thanks again y'alls help is greatly appreciated!

---

### Post by Sammi on 2007-05-23
> **rdmike said:**
> ...the OS says I am not the root so I can't. I am the only user of this machine and did not set up a root account which I assume to be the same as an admin acount with Windows
That's so cute :D

Ubuntu doesn't have a superuser (or root) account by default. We have sudo, which can give any user temporary superuser rights.

See here for details: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Basically you just add "sudo" in front of every command you want to run in superuser mode and the os will ask you for your passw. For graphical apps you use "gksudo".

---

### Post by jondecker76 on 2007-05-23
prefix yoru commands with "sudo" -  this gives you superuser privledges. I.e. "sudo rm filename" instead of "rm filename"

---

### Post by bastiegast on 2007-05-23
I see you already installed 32 bit ubuntu but wine has also a 64 bit version since a while. Look on their site to download it but I guess you don't need it anymore.

---

### Post by AndrewRiedi on 2007-05-23
> **bastiegast said:**
> I see you already installed 32 bit ubuntu but wine has also a 64 bit version since a while. Look on their site to download it but I guess you don't need it anymore.

Thank you for the input.  However, to clear things up, I would like to mention that Wine is only 32-bit at the moment.  There is, however a 32-bit Wine for 64-bit distros that is built.  This is what you are talking about, and what people would want anyhow, as their applications are 32-bit.  The package will basically install the 32-bit deps for you also.  :)

Anyhow, yes, you can run Wine no problem on 64-bit linux, but Wine itself still runs as 32-bit so it can run 32-bit programs.

---

### Post by Sammi on 2007-05-24
@AndrewRiedi
Thanks for clearing that up.

---

### Post by rdmike on 2007-05-25
Another update.....

Ok, three days with Linux installed and still little to no functionality. Not quite the experience I hoped for......

Wine is installed just fine but the OS seems to selectively recognize my DVD/CD drive. I can burn a disk with no problem but I cannot access any programs through it wine or no wime.

I've been through every step of adding this printer countless times and still the OS cannot recognize my model of Brother printer. Every other model of brother printer yes, mine, not a chance. 

Sorry for the negativity but I have just about reached my limit with Linux. I've heard for a couple of years now how much better it is than Windows and it may be but if getting something as basic and simple as a printer to be recognized by the OS is this kind of chore..............then Linux is not a realistic option for anyone but those with tons of time on their hands or with a good help resource. The documentation for Ubuntu has nothing of value for most of the issues I have and I am just getting started. Since the install I have done nothing but screw with this damn printer setup. In windows this would have been done and WORKING in a couple of minutes. Now, I don't mind a little work. I like learning new things. I love getting under the hood of computer. I even went to school to get an A+ certification I like it so much but this is nuts.

Ok, I have vented now. I am going to get my wife's laptop and leisurely surf the internet as far away from linux as I can for a few minutes lest I break something. :-P

---

### Post by Sammi on 2007-05-25
Firstly Wine is alpha, not beta, software. It does not work for everything, and can be a pain in the *** when it doesn't.

[COLOR=Black][]("http://ubuntuforums.org/member.php?u=21941")Secondly aysiu always says it best. This is a good read if you want to know all the[/COLOR] limitations of Linux/Ubuntu:
[http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

Many of  the hardware qualms, like the one your having, can be blamed on the hardware manufacturers only supporting Win. That's their decision, and a lot of Linux users spend a lot of time reverse engineering the drivers for Linux in stead. Sorry to hear that you Brother printer is doesn't have functional Linux drivers.

---

### Post by hikaricore on 2007-05-25
> **rdmike said:**
> Another update.....

Ok, three days with Linux installed and still little to no functionality. Not quite the experience I hoped for......

Wine is installed just fine but the OS seems to selectively recognize my DVD/CD drive. I can burn a disk with no problem but I cannot access any programs through it wine or no wime.

I've been through every step of adding this printer countless times and still the OS cannot recognize my model of Brother printer. Every other model of brother printer yes, mine, not a chance. 

Sorry for the negativity but I have just about reached my limit with Linux. I've heard for a couple of years now how much better it is than Windows and it may be but if getting something as basic and simple as a printer to be recognized by the OS is this kind of chore..............then Linux is not a realistic option for anyone but those with tons of time on their hands or with a good help resource. The documentation for Ubuntu has nothing of value for most of the issues I have and I am just getting started. Since the install I have done nothing but screw with this damn printer setup. In windows this would have been done and WORKING in a couple of minutes. Now, I don't mind a little work. I like learning new things. I love getting under the hood of computer. I even went to school to get an A+ certification I like it so much but this is nuts.

Ok, I have vented now. I am going to get my wife's laptop and leisurely surf the internet as far away from linux as I can for a few minutes lest I break something. :-P

This post doesn't belong in this thread for one... and doesn't even belong in gaming and leisure.

Here's a little light reading for your trouble: [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by rdmike on 2007-05-25
My apologies for placing my post in the wrong place. How uncivilized of me. 

The thread started as and still remains an issue with DirectX which doesn't seem to be addressable. The printer thing was an add-on. From here on out I'll research my own information. I do appreciate the snide remarks however it made my day and certainly improved my image of this community. Cheers!

---

### Post by hikaricore on 2007-05-25
I'll start a thread about oranges and after days of folks discussing oranges, I will randomly burst into a rant about how much I !@#%ing hate bananas and how no one will help me with banana related issues.

See how much sense that makes?

As you've already been informed, directx api compatibility under WINE is limited.  Your best bet is to use games which
feature an opengl mode (such as WoW for example) that are easily switched to in a config file or command line.  That's
pretty much about the best I can offer for ya.

---

### Post by cisforcojo on 2007-05-27
hikaricore wasn't being snide. He's actually one of the more helpful people on the forums. Ubuntu actually has the best linux community of all of them (IMO). There's a general sense from previous linux experience that you can't mention Windows without saying how much you hate it and can't ask a simple question without apologizing for being a newbie. This is probably because of peoples' past experiences with arrogant, unhelpful linux users. People expect to be criticized by other linux users for this but that generally doesn't happen here. This is an image that Ubuntu is trying to change (and has done successfully). 

Your problem with your printer is indeed a problem and unfortunately isn't a rare one, but it's getting better. Little by little, the problems are going away. Stick with it and you'll see what I mean. It's a difficult OS to get used to but definitely worth it. But as you said, you do need time.

@ DirectX: You could also look into using CEDEGA([www.transgaming.com](www.transgaming.com)). In some instances, it seems a little less finicky than WINE. It's WINE-based and is also commercial so might not be the best solution for you.

Perhaps you could provide more information on the problem, what you are specifically trying to install and what the problem is. To get the most help, you should start a new thread in Gaming and Leisure.
It appears to be a CD/DVD problem in wine?

---

