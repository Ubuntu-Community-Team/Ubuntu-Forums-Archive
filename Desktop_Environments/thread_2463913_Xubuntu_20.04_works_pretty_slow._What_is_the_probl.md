---
title: "Xubuntu 20.04 works pretty slow. What is the problem?"
date: 2021-06-21
forum: Desktop Environments
---

### Post by sinoptic on 2021-06-21
Upgraded xubuntu from 18.04. That upgrade was not smooth &#8230;anyway, I passed it and found that upgraded xubuntu 20.04 works very slow, comparative to 18.04.
I&#8217;ve got pretty good hardware &#8211; CPU:i9-9900, RAM:32GB, SSD: Samsung 860evo, Nvidia 2080 but it doesn't help - everything is slow.
Indicators CPU, RAM, HDD shows that there is almost no system load.
Nvidia driver works fine any windows moves appears smooth, even GSync supports.
 
For example, I run &#8216;settings&#8217; from application menu&#8230; so I wait for a couple of seconds then window opens. Just incredible.
Another example, web-browser Chrome/Firefox &#8211; when I enter URL text appears extremely slow, it freezes for 1-3 seconds, and then text is jumped out. Any click on web page works after 1-2 seconds delay as well. Firefox is worst of them. Someone can tell: slow internet connection. The same PC with loaded MS Windows with Chrome works very well. Mac (next to this PC, has the same connections) works like a rocket.
JetBrain CLion has the same illness &#8211; any action after delay.
 
I was feed up of this and reinstalled xubuntu 20.04 completely. Now it works slightly better. Where it was 2 seconds delay, it became 1 second. But in general, OS is simply uncomfortable. Any action leads to delay and indicators show no system load at all. What is wrong?
 
I love xubuntu since it is light and fast and xfce is simple and flexible. This sets xubuntu apart from most of the OS. But now desktop works even slowly than Mac OS, MS Windows.

Thanks everyone who has patience to read this story to the end.

Is it going to be a new reality or it can be fixed?
Can you suggest me to do something with that?
Is problem with xfce, xorg or got surprises from new linux core?
What is wrong? Do you have the same troubles?

---

### Post by TheFu on 2021-06-22
> Do you have the same troubles? 
No, I do not, but I did after a fresh 20.04 install about a year ago.  I think the issue was related to either my choosing ZFS or Wayland.  After about 30 minutes, I gave up and reinstalled using LVM and X/Windows.

To figure out what's making it slow, we have to determine what is making it slow.  There are 2 broad issues.  Software or hardware.
Hardware issues should show up in the system logs, so check those for all errors and warnings.  Logs are in /var/log/ ... look at ALL OF THEM.
New hardware can fail completely or fail partially too.

Next, we're onto software issues.  Those are:
* Drivers
* Kernel
* OS
* GUI

Often, people complain about X being slow, but it is only the GUI that is slow, not the OS.  Knowing and determining which it is cuts the places to look 90%.
Sometimes a slow DNS response can make the entire computer seem slow too, but check that you are using a fast DNS server.  That probably is NOT the DNS that your ISP provides.

For drivers, slowness isn't usually the issue. Either they work or they don't.  Use lshw and inxi to gather hardware lists and drivers being used.  Don't  visit a vendor's driver download site unless an expert says to.  For example, the nvidia driver you want is best installed using 
```
sudo ubuntu-drivers autoinstall
```
 
You didn't mention patching.  Really need to fully patch any OS immediately post-install.
```
sudo apt update
sudo apt full-upgrade
```
A reboot is likely necessary. The patching often fixes slow running systems. The reboot is how a new kernel gets to work.  My systems don't get slower over time, so the idea of a weekly or monthly reboot being needed isn't something I follow. Rebooting isn't something I do, unless it is necessary and convenient.

Then there are issues with default setups for swap and abuse by some mainstream browsers taking 2x the RAM of the system. After all, RAM that isn't used is being wasted, right?  Use **top** and **free -hm** to research which programs are using all the CPU and RAM. Be certain to read up about what each column means for those commands. The columns do not have intuitively obvious meanings.  Browsers might list 37G as taken, but really using less than 1GB.  That's the nature of top.  I've seen the VIRT for firefox claim 37G, but further research showed it was really using only 400K.  Because I didn't like seeing huge RAM values like that, I configured a constrained environment to only let firefox see 8G of RAM total. That was purely for my sanity.

---

### Post by ajgreeny on 2021-06-22
No, I do not see that slow behaviour either and my hardware is hugely lower spec than yours:
[LIST=1]
[*]Intel(R) Core(TM) i3-4100M CPU @ 2.50GHz
[*]8GiB RAM
[*]4th Gen Core Processor Integrated Graphics
[*]Intel Wireless 7260
[/LIST]
I am also using a spinning HDD, not SSD.

My immediate suspicion would be the graphic driver not being up to scratch but never having had an nvidia card I can not tell you more in any detail.
Did you uninstall whatever nvidia driver you were using in 18.04 before upgrading the distro to 20.04?

---

### Post by monkeybrain20122 on 2021-06-22
> **ajgreeny said:**
> 
My immediate suspicion would be the graphic driver not being up to scratch but never having had an nvidia card I can not tell you more in any detail.
Did you uninstall whatever nvidia driver you were using in 18.04 before upgrading the distro to 20.04?

I agree. 

@OP the driver might be installed, but are you sure it is being used?

Can you start the Nvidia-x-server-settings app?

What are the outputs for

```
glxinfo|egrep "OpenGL vendor|OpenGL renderer"
``` ?

---

### Post by him610 on 2021-06-23
You can see how long your system takes to startup using these commands...
```

systemd-analyze time
systemd-analyze critical-chain
systemd-analyze blame

```
or you can run all three together...
```

systemd-analyze time && systemd-analyze critical-chain && systemd-analyze blame

```

Is my Xubuntu LTS 20.04.2 slower than 18.04.nn? Somewhat, but possibly because I added more programs to begin at startup. Unless one maintains a detailed record to compare startup times now versus sometime in the past, how can one really tell.

---

