---
title: "internet problem, and hard drive partition and graphics and a couple more"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Rixis on 2006-07-19
first problem, probably easiest to solve:

i have a dual boot with windows xp and dapper on my laptop, and i have around 4 gig of music, i used a partition program in windows, but made it ntfs, this partition has every song etc on (5 gig partition incase i get more songs), both windows and lnux can read the songs, but linux cannot write to the partition, to drop new songs or anything, how would i solve this? format it to fat32 or something? i need both windows xp and linux to be able to read the songs and write new songs into it


second: when i boot it says something line pci graphics memory not allocated, and the ubuntu splash screen is choppy (the bit where it tells you the status of the boot, loading this file, that files etc), and to install linux, i have to plug a seperate monitor in to be able to read the instructions, the gfx card is an onboard via km400/kn400

third: i used dreamweaver and photoshop quite a lot, and would like to use windows liver messenger, rather than amsn/gaim etc, and mirc rather than konversation, so was wondering if there was a free way to port them to ubuntu, via an emulator or something? if not, guess i just means i need to keep windows on my hdd

fourth: this is the main problem, and its a weird one because i never touched the settings

basically, i booted up linux, while my network cable was plugged into my friends router, and my wireless card also connected to his router as well, and now, for some reason i cannot use most internet things in ubuntu, i can update ubuntu/software, i can download and install new software from the repositories, i can ping websites, and can log into knoversation and amsn, but cannot log into gaim (even the msn bit, using the same e-mail addy as i used for asmn), and none of my browsers load anything at all, firefox 1.5.0.4 and 1.0.7, opera or epiphany, its as though linux has somehow blocked most activity i'm allowed to do

all these things worked fine when i connected to my brothers computer (directly, no router or anything), so was wondering if it was a router problem (the router is a D-Link DSL-G624T), if i log off ubuntu and into windows, everything comes back (which is how i'm writing this post), and i'm using both wired and wireless connections in windows, so my best guess would be that it is a linux setting or something, or a conflict between wired and wirless (i've tried disabling both), changing all the simple options, using 1 at a time, unplugging the wire, taking the wireless card out etc (wired port via rhine II, wireless netgear ma251), nothing seems to change, i have also logged into the router settings (via ubuntu), and can;t see anything that appears to be a solution, so i figure best place to come was here :)

i thank anyone who can solve any or all of these problems, especially the internet one, as i kind of rely on the internet loads, and am forced to log into windows for this

---

### Post by thoolihan on 2006-07-19
1. ntfs write support is buggy at best and not installed by default.  If you want to try it, check out: 
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

2. Run the following command and post the results here, it will give us specific error messages:
```
sudo cat /var/log/Xorg.0.log | egrep "(EE)|(WW)"
```

3. You can run windows apps through wine, see:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
Or for a proprietary solution look up CrossOver By Codeweavers

4. As for the network problems, post some basic info, like the out put of:
```
ifconfig -a
netstat -rn

```

In the future, it's probably better to post your questions 1 at a time, you'll get better responses, and more people will look at the post since the subject will be clear and concise.

Best of luck, and if you post the info I mentioned above, I'll be glad to assist.
-Tim

---

### Post by Mickeysofine1972 on 2006-07-19
I'm almost sure that NTFS files and folders are regarded as owned by root too so if you copy you need to have you file browser running as root.

I do this in kubuntu by:

```

kdesu konqueror

it could take the form:

sudo <insert name of filebrowser here>


```

Hope this helps

Mike

---

