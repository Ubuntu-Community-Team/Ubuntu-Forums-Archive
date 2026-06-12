---
title: "Err.. Debian-based... what now? &gt;.&gt;"
date: 2008-12-09
forum: General Help
---

### Post by TheBlueBeastie on 2008-12-09
I installed Ubuntu 8.10, because my friends told me too.
I haven't had any problems with it, except for the printer and microphone not working, but I can live without those, for now.

But, there's a program I NEED, and to run it on Ubuntu, I apparantly need something called "Wine".

So, I went to the WineHQ (which was a nightmare.  It's impossible for me to navigate around, and most of the download links didn't like me. :/ ) and then, after much consideration of what I must get out of what I could, I downloaded wine 1.1.7.bz2 or something like that to Windows, and then wrote it to a disc.

Then, I went to Ubuntu's Source Manager, and tried to add the cd-rom as a source, but it tells me that it couldn't find any package files, and that it might not be Debian-based.

I don't have internet on the Ubuntu system, as I'm kind of hoping I can install what I need for that in Wine, so I can't do it any other way, it seems.  I really do want to try everything before I give up on it... :<

So, since I figure that this is all my fault, what am I doing wrong, and what should I do about? :D

---

### Post by taurus on 2008-12-09
Why not download the Ubuntu version instead of the source since you need to build it from source?

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by hyper_ch on 2008-12-09
```

sudo apt-get install wine

```

---

### Post by taurus on 2008-12-09
> **hyper_ch said:**
> ```

sudo apt-get install wine

```

I think he said that his Ubuntu is not connected to the network at this moment (probably network is not working yet).

---

### Post by hyper_ch on 2008-12-09
> **taurus said:**
> I think he said that his Ubuntu is not connected to the network at this moment (probably network is not working yet).

I "generously" skipped that part ;)

---

### Post by MarblePanther on 2008-12-09
It sounds to me like you should stay with windows (if it wasn't giving you problems)

WINE isn't the end-all solution to replacing windows

If you need that program, at least dual-boot

Doing what your friends tell you isnt a good reason ;)

---

### Post by davidbilla on 2008-12-09
Hey, if you have broadband, type

$ sudo pppoeconf

in the terminal and choose the default options.(Default options are fine for most people). Your network will start working just fine! By the way, what's that program that you need so badly?

---

### Post by Dan_Dranath999 on 2008-12-09
> **taurus said:**
> Why not download the Ubuntu version instead of the source since you need to build it from source?

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)


download a DEB package, put it on a USB stick, take it to the Ubuntu system, n'double click on it (GDebi will ask you to install it) 

(i asume the windows system is not in the same machine Ubuntu is, as you say there isn't an internet connection on the last one)

---

### Post by Baggers on 2008-12-09
Hi there bluebeastie,
I think it would be good to hear which program you are trying to install.
Wine is a great project for running office software, games and some other apps but it certainly definitely isn't the thing you want to install if you are trying to use drivers for instance.

I'm assuming this because you said: ***"I don't have Internet on the Ubuntu system, as I'm kind of hoping I can install what I need for that in Wine,"***

So in light that Wine is probably not the solution, lets take a step back.
[LIST]
[*]What version of ubuntu are you using? (I'm assuming the latest, ie Intrepid Ibex)
[*]What type of Internet connection are you trying to connect to?
[*]Is this wired or wireless?
[/LIST]

As others have said swapping due to peer pressure is an odd one...certainly haven't heard that one before. But hey welcome anyway!
Now lets try and get you online!

---

### Post by dragos_iliescu_2005 on 2008-12-09
Printer and microphone is the problem if I understand well. 
First, check the compatibility in Linux of your printer. If is not there, must of the chance, Wine will not help. I had the same problem - Lexmark X3330. Finally I use VirtualBox for install the printer.
If you find your model in the list, then you can select the correct Linux version for printer support. Normally it should work this.

For the microphone, check alsa settings (type in terminal "alsamixer") and check in there if your microphone is enabled.

---

### Post by Baggers on 2008-12-09
Oh just to expand on dragos' comments about the microphone, perhaps have a fiddle with the settings through the GUI before delving into the command line (as that is a little daunting for a beginner)

Double click on the speaker icon in the top right corner to open the mixer.
Go to preferences and enable to option to change "microphone capture" click ok and go to the new tab named "switches" and turn on microphone capture.

If that doesn't work then mess with any options pertaining to microphones and capturing!

---

### Post by TheBlueBeastie on 2008-12-09
> **Baggers said:**
> Hi there bluebeastie,
I think it would be good to hear which program you are trying to install.
Wine is a great project for running office software, games and some other apps but it certainly definitely isn't the thing you want to install if you are trying to use drivers for instance.

I'm assuming this because you said: ***"I don't have Internet on the Ubuntu system, as I'm kind of hoping I can install what I need for that in Wine,"***

So in light that Wine is probably not the solution, lets take a step back.
[LIST]
[*]What version of ubuntu are you using? (I'm assuming the latest, ie Intrepid Ibex)
[*]What type of Internet connection are you trying to connect to?
[*]Is this wired or wireless?
[/LIST]

As others have said swapping due to peer pressure is an odd one...certainly haven't heard that one before. But hey welcome anyway!
Now lets try and get you online!

Well, I mean you know, it's just they really seemed to like it, and I wanted to see what they were talking about it, so when they told me to try, I obliged.

Now then, I thought wine would help, because the 3G modem card I'm using comes with software that connects me. Something called "Axcess"
Interestingly, my service provider, Alltel, doesn't seem to be on the list of providers on the network setup list for wireless.  I only see different versions of AT&T and T-Mobile.
Just thought you should know.

Oh, and yes, I'm using 8.10.  The one they seem to called they Intrepid Ibex.


@Baggers and the dragos comment extension.
Actually, after doing all that, my microphone started working. xD
Thanks!

> 
download a DEB package, put it on a USB stick, take it to the Ubuntu system, n'double click on it (GDebi will ask you to install it)

(i asume the windows system is not in the same machine Ubuntu is, as you say there isn't an internet connection on the last one)

ohnoes!  So close! >.<;
I get Error: ... is not satisfiable: libaudio2

I already forgot what it was that wasn't satisfiable. x3  Both systems on the same computer.  I can just only connect using Windows.

---

### Post by Baggers on 2008-12-09
***"Well, I mean you know, it's just they really seemed to like it, and I wanted to see what they were talking about it, so when they told me to try, I obliged."***
Haha yeah I know the feeling when I first saw Linux I thought the desktop sucked (it was some strange distro though) I finally got Ubuntu to mess around with simple server stuff....and now its on my main PC..weird!

Hmm the 3G is an odd one though, I think we may be waiting for a US dude to see this as I'm in Blighty and don't really know the services out there.
Does the device have a model number or something...maybe that Alltel use the same hardware as some other company.

Sorry I couldn't be more help than that...I guess we wait!

---

### Post by TheBlueBeastie on 2008-12-09
> **Baggers said:**
> ***"Well, I mean you know, it's just they really seemed to like it, and I wanted to see what they were talking about it, so when they told me to try, I obliged."***
Haha yeah I know the feeling when I first saw Linux I thought the desktop sucked (it was some strange distro though) I finally got Ubuntu to mess around with simple server stuff....and now its on my main PC..weird!

Hmm the 3G is an odd one though, I think we may be waiting for a US dude to see this as I'm in Blighty and don't really know the services out there.
Does the device have a model number or something...maybe that Alltel use the same hardware as some other company.

Sorry I couldn't be more help than that...I guess we wait!

Ah, I see...
To answer your question though, Ubuntu calls it a Huawei E620.
Everytime I log onto it, it asks me if I want to configure it, which takes me to the network setup.

---

### Post by Mr. Picklesworth on 2008-12-09
> **TheBlueBeastie said:**
> ohnoes!  So close! >.<;
I get Error: ... is not satisfiable: libaudio2

I already forgot what it was that wasn't satisfiable. x3  Both systems on the same computer.  I can just only connect using Windows.

This is definitely Ubuntu's weak spot; it REALLY needs an Internet connection to shine. Usually what happens is software like Wine, and all of its dependencies (in your case libaudio2) are available online in Ubuntu's repositories. apt-get install, Add / Remove Applications and the Synaptic Package Manager all act to download that software from the repositories and install it.

When you tried to install Wine with the Debian package you downloaded, the installer needed a few other packages. Usually it will fetch these automatically via the Internet (from Ubuntu's repositories). In your case, you will need to download those each onto a disk. This may take a while :/
Check out [http://packages.ubuntu.com/](http://packages.ubuntu.com/) . From there, you can download all those packages in the Ubuntu repositories manually, then just open them to install on your Ubuntu machine. You may want to use [Ubuntu's wine package]("http://packages.ubuntu.com/"), then follow the trail of depedencies it asks for.

I have a vague recollection that someone put up a service which automatically downloaded a package and all its dependencies in one click, but I don't remember it off hand. Anyone?


As for Wine helping with your Internet connection, I am sorry to say it's quite doubtful at the present time. Wine does not have much control over hardware stuff yet. It's in the roadmap for a future release. Maybe worth a shot, but don't let your hopes up...

---

### Post by Baggers on 2008-12-09
Cool...havent been able to find any details unfortunately. Only a couple for EVDO modems.
I'm sure some expert will be along soon enough.

As for the dependency issue...Well one of the great bits of using ubuntu is when you install something, if it needs extra programs it just installs them for you. Unfortunately this is a issue if your not online as you would have to move the dependencies over manually .. eugh.

{EDIT}
Ahh Picklesworth...you got in before me and wrote a better responce! Blast you ! hehe

---

### Post by TheBlueBeastie on 2008-12-09
> **Mr. Picklesworth said:**
> This is definitely Ubuntu's weak spot; it REALLY needs an Internet connection to shine. Usually what happens is software like Wine, and all of its dependencies (in your case libaudio2) are available online in Ubuntu's repositories. apt-get install, Add / Remove Applications and the Synaptic Package Manager all act to download that software from the repositories and install it.

When you tried to install Wine with the Debian package you downloaded, the installer needed a few other packages. Usually it will fetch these automatically via the Internet (from Ubuntu's repositories). In your case, you will need to download those each onto a disk. This may take a while :/
Check out [http://packages.ubuntu.com/](http://packages.ubuntu.com/) . From there, you can download all those packages in the Ubuntu repositories manually, then just open them to install on your Ubuntu machine. You may want to use [Ubuntu's wine package]("http://packages.ubuntu.com/"), then follow the trail of depedencies it asks for.

I have a vague recollection that someone put up a service which automatically downloaded a package and all its dependencies in one click, but I don't remember it off hand. Anyone?


As for Wine helping with your Internet connection, I am sorry to say it's quite doubtful at the present time. Wine does not have much control over hardware stuff yet. It's in the roadmap for a future release. Maybe worth a shot, but don't let your hopes up...

Oh... my. o.x

So, let me get this straight, before I start downloading anything.
What I basically do is, I download all the things found here: [http://packages.ubuntu.com/intrepid/wine](http://packages.ubuntu.com/intrepid/wine)  and then I run them in Ubuntu?

As for not hoping Wine fixes my internet problems, I'm pretty pessimistic when it comes to computer's anyway.

I can't even start Firefox in Windows without thinking, "I wonder what's going to go wrong. :D"

I'm not expecting Wine to help, I just want to say that I tried it. :3

EDIT
Actually, all I needed was to install libaudio2.  After that, Wine installed, and I installed the Axcess software! :D

New problem: It gets stuck trying to find the wireless card during setup.  It does say it might take a few minutes, and I waited five. Maybe I should've waited longer...
Anyway, is it possible that it's not detected the card because Ubuntu doesn't have the driver(s) for it?  I think so, but, what do I know? xD

---

