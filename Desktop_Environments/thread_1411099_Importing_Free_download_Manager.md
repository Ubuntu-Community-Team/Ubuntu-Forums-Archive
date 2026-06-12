---
title: "Importing Free download Manager"
date: 2010-02-19
forum: Desktop Environments
---

### Post by hariks0 on 2010-02-19
This is the most useful software I had in windoze. It is open source and still a linux version is not available. Why don't somebody make a ppa or deb for Ubuntu? I do not have any programming skill and if I had any, this piece of software will be the first thing I would contribute to Linux. I could not help but boot to the other OS for doing any big downloads, especially with scheduling.

I tried installing it in wine but it i not doing anything.

Thanks a million to those who do something to import FDM to ubuntu.

---

### Post by onyxwolf on 2010-02-19
There are a couple options. First off wget (standard bash download manager) has the same kind (resume if interrupted) of capabilities via HTTP and FTP. It also continues downloading with interaction.
```
man wget
```

       "Wget has been designed for robustness over slow or unstable network connections; if a download fails due to a network problem, it will keep retrying until the whole file has been retrieved.  If the server supports regetting, it will instruct the server to continue the download from where it left off."


For Bittorrent support use the default Bittorrent client.

For acceleration use Axel (so I've heard, never needed it myself) but its CLI.

For GUI with pause, resume, limiting abilities use gwget2. 

However I do agree that a good gui accelerator / manager would be nice. (Maybe just give gwget acceleration capabilities).

---

### Post by SecretCode on 2010-02-19
"Downloader for X" is also an option.

---

### Post by hariks0 on 2010-02-20
But none has scheduler, power off after download etc as I have a data plan that allows unlimited only between 02.00 am and 08.00 am. Let me clarify this. 

1. I have setup to boot my PC automatically at 02.00 at morning. 
2. GBUB selects Windoze as the default OS after 10 seconds.
3. FDM is started at startup.
4. FDM does the scheduled downloads and shuts down the PC after completion.

I want the same thing done in ubuntu after step 2 selects Ubuntu and does autologin.

Thank you all.

---

### Post by Ozymandias_117 on 2010-02-20
Ignore this =D I was being stupid =)

---

### Post by 2hot6ft2 on 2010-02-20
> **hariks0 said:**
> But none has scheduler, power off after download etc as I have a data plan that allows unlimited only between 02.00 am and 08.00 am. Let me clarify this. 

1. I have setup to boot my PC automatically at 02.00 at morning. 
2. GBUB selects Windoze as the default OS after 10 seconds.
3. FDM is started at startup.
4. FDM does the scheduled downloads and shuts down the PC after completion.

I want the same thing done in ubuntu after step 2 selects Ubuntu and does autologin.

Thank you all.
I can see how this would be real useful for your situation. On more than 1 occasion I have wanted something like it.

I wonder it it would work in wine. I kinda doubt it but maybe.

---

### Post by 2hot6ft2 on 2010-02-20
I did some looking and there is some good news
> Free download manager for Windows, Mac OS X and **Ubuntu Linux is coming soon.**
From here [http://www.freedownloadmanager.com/](http://www.freedownloadmanager.com/) at the bottom (that's pretty much all that's there)

It IS Open Source so there is this
> Also we **plan to port it to Linux** and Mac OS. 
here: [http://sourceforge.net/projects/freedownload/](http://sourceforge.net/projects/freedownload/)

So there is some hope. Now if a few programmers care to help push it along it may just happen in the near future. It sure has a lot of features. Even the "Video Conversion plugin" should appeal to a lot of people. Saw that here: [http://www.freedownloadmanager.org/download.htm](http://www.freedownloadmanager.org/download.htm)

I'll have to keep a watch on this one.

**VOTE FOR IT**: It's already **in Ubuntu Brainstorm** so if you would like to see this in Ubuntu then vote for it at:
[URL="http://brainstorm.ubuntu.com/idea/3828/"][B]Idea #3828: A good download manager
Solution #4: Port FDM to Linux[/B][/URL]

---

### Post by 2hot6ft2 on 2010-02-20
> **hariks0 said:**
> But none has scheduler, power off after download etc as I have a data plan that allows unlimited only between 02.00 am and 08.00 am. Let me clarify this. 

1. I have setup to boot my PC automatically at 02.00 at morning. 
2. GBUB selects Windoze as the default OS after 10 seconds.
3. FDM is started at startup.
4. FDM does the scheduled downloads and shuts down the PC after completion.

I want the same thing done in ubuntu after step 2 selects Ubuntu and does autologin.

Thank you all.
May have a temporary solution for you. Not sure if it will work but it's the closest I could find for now.
It's called FatRat
You'll have to download both files for your system and install them in the order they are listed. The first one is the data files required by the second one.
> Ubuntu 9.10

32-bit:
[https://launchpad.net/~medigeek/+archive/experimental/+files/fatrat-data_1.1.1-5~ppakarmic1_all.deb](https://launchpad.net/~medigeek/+archive/experimental/+files/fatrat-data_1.1.1-5~ppakarmic1_all.deb)
[https://launchpad.net/~medigeek/+archive/experimental/+files/fatrat_1.1.1-5~ppakarmic1_i386.deb](https://launchpad.net/~medigeek/+archive/experimental/+files/fatrat_1.1.1-5~ppakarmic1_i386.deb)

64-bit:
[https://launchpad.net/~medigeek/+archive/experimental/+files/fatrat-data_1.1.1-5~ppakarmic1_all.deb](https://launchpad.net/~medigeek/+archive/experimental/+files/fatrat-data_1.1.1-5~ppakarmic1_all.deb)
[https://launchpad.net/~medigeek/+archive/experimental/+files/fatrat_1.1.1-5~ppakarmic1_amd64.deb](https://launchpad.net/~medigeek/+archive/experimental/+files/fatrat_1.1.1-5~ppakarmic1_amd64.deb)

It has a Scheduler (See the pic below)

There's no shut down when finished but it's as close as I could find.

Found it here:
[https://bugs.launchpad.net/ubuntu/+bug/228265/comments/10](https://bugs.launchpad.net/ubuntu/+bug/228265/comments/10)

Not the best place to find an app. (a bug page), looks like it will be available in 10.4

---

### Post by 2hot6ft2 on 2010-02-20
Thought I would add the FatRat Homepage for the documentation here:
[FatRat Homepage Documentation]("http://fatrat.dolezel.info/documentation")

and a screen shot of the "Drop Box"...:rolleyes: more like a "Drop Trap" that you can move to wherever you want on your screen.

Seems to work pretty good.

---

### Post by hariks0 on 2010-02-20
Hi 2hot6ft2, Thank you very much for the pains you have taken. I have installed the FDM in wine. But it is of no use. The promise of porting FDM had been there for ages. See some comments on the brainstorm idea. BTW, I use Transmission for BitTorrent downloads in ubuntu by adding it add quitting transmission client. At power on at 02.00 a.m, Ubuntu will autologin and transmission will autostart and do the download. I have to manually shutdown the PC at 08.00 AM. If I setup a shutdown command or gshutdown, the PC ony logs off and the recover boot menu is shown. NO SHUTDOWN.

See the beauty of FDM with windows. FDM shuts down the PC after downloads or windows does the shutdown at 08.00 a.m whichever is first and resumes the download by 02.00 a.m next morning.

I am compelled to admit that windoze has the upper hand there and it is only due to FDM. I would install windows again only for this if I am not able to run FDM in Ubuntu.

Thank you once again. Please do post any new information.

---

### Post by hariks0 on 2010-02-21
Now I got it. I opened a terminal and as root edited /etc/crontab and that did the trick. Now my entry in crontab looks like ```
*/5 2-8 * * * root /home/root/sd.sh #JOB_ID_1
```.

sd.sh is a script that checks the presence of a virtualbox process and shuts down when none is found.

FYI, let me summarise the whole story before you. My actual requirement was to do the downloads between 02:00 - 08:00 a.m during which period I have unlimited downloads. The steps are as follows :-

1. I have setup to power on my PC automatically at 02.00 at morning.
2. GRUB selects Ubuntu as the default OS after 10 seconds.
3. wxp is started in VirtualBox with ```
VBoxManage startvm wxp
```
4. In wxp FDM is started at startup.
5. FDM does the scheduled downloads and shuts down wxp after completion.
6. OR wxp does shutdown at 08:00 a.m if the downloads are not finished.
7. [Here comes the role of this post] Cron checks the presence of a virtualbox process each 5 minutes and shuts down Ubuntu when none is found.

Of course it is a very clumsy way. But I do not have any other option as FreeDownloadManager is not available for Linux.

Thank you very much for the help.

---

