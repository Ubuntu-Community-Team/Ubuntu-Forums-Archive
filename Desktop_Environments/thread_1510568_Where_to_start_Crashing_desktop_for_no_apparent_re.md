---
title: "Where to start? Crashing desktop for no apparent reason. 10.04 Gnome"
date: 2010-06-15
forum: Desktop Environments
---

### Post by bigwigbaz on 2010-06-15
I have had a problem since installing Ubuntu 10.04, machine is a dell and quite old, 2.6gHz with no additional graphics processors. Every time I use this system it has random crashes and eventually gets to a screen with text, briefly mentioning battery state... Then I get vertical black and white bars flashing up at the top of the screen on and off. I can do nothing other than power off on the button or Alt+SysRq+ R,E,I,S,U,B. Alt+F2 does nothing. I cannot get to the TTY1-6 either with Ctrl+Alt+F1-6. 

I have previously installed 8.04 (Xubuntu) on this same system with NO problems, it has never crashed, only program crashes. I am considering installing the XFCE desktop as it has served me well in the past, but I don't know if this is a Gnome issue or a 10.04 issue. 

It seemed to be a firefox thing, so I have installed chromium, but still happens. 

I desperately need to do something, I need a stable, easy to use system that will not need too much attention (hence LTS!) for my dad's photos, nothing used except for email (web), basic internet use and some photo management program. I still have 8.04 installed so I am using that at present.  

Any input would be greatly appreciated.

---

### Post by irv on 2010-06-15
Are you doing a dual boot with 8.04? Just a suggestion, I had trouble with 10.04 so I went to 9.10 everything works fine. I did a fresh install. You might want to try one more fresh installs of 10.04 to see if it had something to do with the install. Don't forget you need to install the  Ubuntu restricted extras after installing 10.04 and get all the updates there has been some fixes added to the install files.

---

### Post by bigwigbaz on 2010-06-15
Thanks IRV, 

yeah I chose to do a fresh install because the (default) EXT4 filesystem is now regarded as stable and is also much faster. I have seen massive improvements in bootup speed between the two systems. 

It is currently dual booting 8.04 and 10.04. I have installed the restricted extras and updated via the update manager. other than that is more or less a standard fresh install. I only have an 80GB drive and an external backup drive to schedule backups to. 

I want to avoid going back to 9.10 as I will need to upgrade to a new system soon, when the updates stop. I would rather install the current debian or similar. 

I have installed via USB rather than live CD, same install process but needs ubuntu to create USB install drive. 

I think there will be something in the system logs but I cannot figure out what to look at, or what the logs actually mean (as they are generally not in plain english). 

This is an issue for Ubuntu, especially as I have a (basic) understanding of the system, if a default install fails repeatedly with no forseeable fix, people will revert back to M$ or whatever they were using previously.

---

### Post by irv on 2010-06-15
Right now I am running 10.04 on my Dell Inspiron 1521 laptop and it has been running flawless for almost 3 weeks. I also have it running on my Server and it is doing the same. The only things I found was the suspend locked up on me once. Out side of this I have had no problems. I too did a fresh install, and am triple booting with Win7 Ubuntu and Peppermint, which is a cut down version of Ubuntu with xfec desktop. The only reason I install it was it boot very fast. About 10 seconds. I use it if I need to get on the Internet fast and then shut down. I use Ubuntu for everyday stuff, and Win7 for Watching Netflix and a couple of win programs I like.
I wish I could tell you what is going on with your install, but it must have something to do with a piece of hardware or something that is running that causes the problem. I lean more toward hardware. Maybe someone can help with the log files. I am not sure where to look either.
I did find this by doing a google search. Maybe this will help.

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/]("Right now I am running 10.04 on my Dell Inspiron 1521 laptop and it has been running flawless for almost 3 weeks. I also have it running on my Server and it is doing the same. The only things I found was the suspend locked up on me once. Out side of this I have had no problems. I too did a fresh install, and am triple booting with Win7 Ubuntu and Peppermint, which is a cut down version of Ubuntu with xfec desktop. The only reason I install it was it boot very fast. About 10 seconds. I use it if I need to get on the Internet fast and then shut down. I use Ubuntu for everyday stuff, and Win7 for Watching Netflix and a couple of win programs I like. I wish I could tell you what is going on with your install, but it must have something to do with a piece of hardware or something that is running that causes the problem. I lean more toward hardware. Maybe someone can help with the log files. I am not sure where to look either. I did find this by doing a google search. Maybe this will help.  http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/")

---

### Post by irv on 2010-06-15
You can run the System > Administration > Log file viewer, but don't ask me what I am looking at.
I know it keeps a daily log and maybe you can see something there that will tell you what happen when your system acts up.
Here is a screen shot of my daily log.[ATTACH]160589[/ATTACH]

---

