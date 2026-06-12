---
title: "New to Ubuntu and have some questions"
date: 2008-12-24
forum: General Help
---

### Post by vector8 on 2008-12-24
Hey everyone.  Well, I have been trying to install Ubuntu using Wubi for a while now and couldn't seem to get it to work.  After my Windows XP PC crashed tonight I decided I would just go ahead and do a full install of Ubuntu 8.10.  Let me just start off by saying WOW I can't believe how simple it was to install.  It literally took 20 minutes.

I went ahead and installed all the important updates from the Update Manager.  I didn't install any of the Recommended ones because I don't even know what half of them are.
I noticed my sound worked when it started up.  That was weird because I'm used to having to install drivers.

Which brings me to the questions:
Do I have to download drivers for all the hardware like I would do in Windows XP? (i.e. ATI Display Drivers, Sound Card Drivers, Motherboard Chipset drivers... etc..)

Is it best just to activate the driver thing under System>Administration>Hardware Drivers?

Is there like a website or something that shows a check list of everything to install on a fresh Ubuntu install?

Also are there any good guides for new Linux users that switched from Windows?

I have been playing around with a LiveCD for a while now and really like how easily accessible everything is, but I'm still quite lost so any help is much appreciated!

---

### Post by adult swim on 2008-12-24
hi and welcome to ubuntu.  you should have to download and install most drivers, ubuntu should do that for you automatically.  if something is not working right, like your wireless card or graphics card then you can look into system>adminsistration>hardware drivers and see if there are any proprietary drivers available for  you to use.  if there arent any there and your hardware still isnt working correctly, then some additional steps will need to be taken to get them working.  just post a new thread with the hardware device and whats going on with it.  im sure there are alot of sites that will explain the difference between windows and ubuntu if you google it.  here is one that is from the ubuntu community [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)  
you may find that mp3s and certain things wont play starting out.  an easy solution to get codecs for music/video files is to go to a terminal (applications>accessories>terminal) and enter in  ```
sudo apt-get install ubuntu-restricted-extras
```  it will ask for your password, type that in and hit enter and it will install.  if you run into any problems or have other questions dont be afraid to ask!

---

### Post by balaknair on 2008-12-24
Hello Vector8, and Welcome to the Ubuntuforums.

[I]"Do I have to download drivers for all the hardware like I would do in Windows XP? (i.e. ATI Display Drivers, Sound Card Drivers, Motherboard Chipset drivers... etc..)
Is it best just to activate the driver thing under System>Administration>Hardware Drivers?"[/I]

No you don't. In most cases, Ubuntu will take care of hardware drivers for you, unless you have some really exotic hardware, you don't need to fetch and install drivers. The Ubuntu installation CD itself contains all the Open Source drivers, and proprietary drivers can be installed after you install Ubuntu(you get a pop-up asking if you want to enable proprietary 'Restricted Drivers'). And yes, the best option is to use the Hardware Drivers manager.

[I]"Is there like a website or something that shows a check list of everything to install on a fresh Ubuntu install?

Also are there any good guides for new Linux users that switched from Windows?"
[/I]

The best guide I know of for newbies:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

As for a list of things to do, I think psychocats covers most things in the above guide. I'll just mention a core few things I always do:
1) Enable extra repositories

2) Install restricted packages(closed source stuff like codecs, flash, java, MS TrueType Fonts etc) and proprietary divers.

3) Install an antivirus app(not really needed, I know, and many people will say that an antivirus app will not protect you in Ubuntu, true, but i still do it for peace of mind) and a backup tool(clamav and sbackup)

4) Install Ubuntu-Tweak

5) Enable Compiz and 3D effects and tweak it to my taste

Instructions for most of these steps are available in Psychocats' guide.

Hope this was helpful.

---

### Post by 2hot6ft2 on 2008-12-24
More helpful things to bookmark for future reference.

Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linux.org/apps/](http://www.linux.org/apps/)
[http://www.gimpshop.com/](http://www.gimpshop.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

Everyone asks coming from windows
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

Customizing and apps
[http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)
[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

Learning Linux
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)
[http://ubuntuforums.org/showthread.php?t=655207](http://ubuntuforums.org/showthread.php?t=655207)

Troubleshooting and misc help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
[http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html](http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html)

Welcome and enjoy

---

### Post by vector8 on 2008-12-24
Oh wow so I don't have to go hunt down drivers compatible with Linux?  I can just use what Ubuntu has installed?  That is really awesome!  I always hated doing all that.  Yeah I went ahead and Activated the Display Driver available under Hardware Drivers.  Everything seems to be working so far.

So when I type in that thing in the Terminal it will automatically install all the audio/video codecs I need?  Like Divx and AC3 ect..?

---

### Post by vector8 on 2008-12-24
Wow this is really cool.

Thanks a lot for all of yalls help!

---

### Post by 2hot6ft2 on 2008-12-24
> **vector8 said:**
> Oh wow so I don't have to go hunt down drivers compatible with Linux?  I can just use what Ubuntu has installed?  That is really awesome!  I always hated doing all that.  Yeah I went ahead and Activated the Display Driver available under Hardware Drivers.  Everything seems to be working so far.

So when I type in that thing in the Terminal it will automatically install all the audio/video codecs I need?  Like Divx and AC3 ect..?
Sure will. Well not Divx but xvid which will play divx files. And you can find tons of apps in Synaptic
System>Administration>Synaptic Package Manager

---

### Post by 2hot6ft2 on 2008-12-24
You can also install stuff by going to Applications>Add/Remove it gives you categories to look in.

---

### Post by vector8 on 2008-12-24
Haha it seems like I have been using the wrong OS for the last 10 years.  Ubuntu seems like it will suit me really well.  So simple.

Thanks again everybody for all the help and the quick replies.

---

### Post by vector8 on 2008-12-24
Ok I just ran into a problem with the Proprietary Display Drivers that I activated.  It makes videos that I play really choppy and scrolling down on a webpage is very slow and choppy also.  It didn't do this before I activated it.  Is there a way to fix this or do I just have to disable the driver?

---

### Post by hyper_ch on 2008-12-24
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by vector8 on 2008-12-24
Considering this is the General Help part of the forum and I had General Questions, that is why I only put that in the topic.  No one else here seemed to have a problem helping me, but thanks for the advice for future reference.

---

### Post by Slim Odds on 2008-12-24
> **vector8 said:**
> Considering this is the General Help part of the forum and I had General Questions, that is why I only put that in the topic.  No one else here seemed to have a problem helping me, but thanks for the advice for future reference.

Think of how many **more** people might read your message if it had a better title.

---

