---
title: "Ubuntu, xfce, lxde and system optimization"
date: 2013-02-17
forum: Desktop Environments
---

### Post by motocollage on 2013-02-17
Hello All,

I'm currently running 12.04LTS on my older acer aspire D250 as a dual-boot with windows 7 starter. I love everything linux/open source! I'm an artist currently in my terminal (MFA) program, attempting to specialize in New Media and installation. Basically, any materials or technology I can get my hands on I want to turn into some sort of other-worldly thing.

So, not sure where to start, but I've only really asked for help on the forums for one major problem, and I was ASTOUNDED how awesome the community is. Another user jumped on my problem, and it was great being able to perform under the hood maintenance to my computer. This is my current goal:

I am running 12.04 on my netbook, with some Xubuntu packages installed as well. I want to understand what the difference is when I log in via a different GUI/shell. I'm assuming my Home folder stays the same, but I've noticed each GUI (unity/gnome, xfce, or more?) requires different packages when updating. Or seemingly. What I'd really like to do is see if/how I can remove the packages for Xubuntu and replace it with Lubuntu. If i understand correctly, LXDE is the GUI for Lubuntu (which I really like), while XFCE is for Xubuntu. Now is Unity completely different from GNOME, or is it a derivation? At any rate, I like Unity on my netbook, but sometimes switch and would like that to be LXDE. That, and maybe some pointers on some general maintence I can do to my netbook (Janitor, clean out old packages, understand how best to optimize my resources, etc.)



Anyone interested in tackling any of these problems?

---

### Post by motocollage on 2013-02-17
Oh, and when I set up my info on the forum, I was running 10.10. Can I seriously not change my info until I've had 25 posts?

---

### Post by Bucky Ball on 2013-02-17
All good but I suggest you split this into three separate threads to avoid confusion. 

Edit the post leaving the first question here and I will move it to ***Desktop Environments***, where it belongs.

Copy and paste the other two to new threads in the sub-sections most appropriate. Use descriptive thread titles to increase your chances of help. This one is generic and gives no information about your actual questions/issues/problems. That would be hard though as you are attempting to cover so many bases in the one thread. You can change the title for half an hour after it is posted. Otherwise I can change it for you after you have done some editing and clarified problem one in the one thread. Just PM me with a new title if you'd like this to happen.

Good luck.

PS:

> **motocollage said:**
> Oh, and when I set up my info on the forum, I was running 10.10. Can I seriously not change my info until I've had 25 posts?

Correct. Your new threads will get you there in no time. ;)

PPS: The easiest is not to install xubuntu-desktop but just the DE, xfce4. Same for lxde; just installing lxde will do it. Unity has nothing to do with Gnome, not a derivation.

---

### Post by motocollage on 2013-02-17
Hey, thanks for the prompt response! Give me a few minutes and I'll recompose/move this questions. Yeah, I'm trying to tackle a lot here, but pumped!

---

### Post by Bucky Ball on 2013-02-17
;) That's not a bad thing. But too much info for one thread and there will be others pumped to help if broken into bite sized chunks. Good luck. ;)

---

### Post by Bucky Ball on 2013-02-17
*Thread moved to **Desktop Environments**.*

---

### Post by snowpine on 2013-02-17
Here are instructions to remove Xubuntu and install "pure" Lubuntu: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

It's easy to get 25 posts---just drop by the Absolute Beginner or Multimedia sub-forums and help some people (as we are helping you). :)

---

### Post by seppalta on 2013-02-18
[http://lxlinux.com/xubuntu.html](http://lxlinux.com/xubuntu.html)

---

### Post by motocollage on 2013-02-19
snowpine, I followed the link and copied the Remove Ubuntu code into terminal (on my secondary linux machine, HPpavilion DV6000:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I was doing something the other day and got a similar message. This system has Lubuntu, Lubuntu Netbook, GNOME/OpenBox and Ubuntu. After the results, I will try it on my primary linux machine, the Acer D250.

Another option I thought of was to do a complete re-install from the disk. So far I have been installing from the UBUNTU 10.04 LTS Desktop Edition cd that came with "The Official Ubuntu Book." Will I have the option for a minimal ubuntu install from that disk?

More importantly, as mentioned in the code above, why am I "unable to lock?"

seppalta, i'm gonna put that link on the backburner. A little technical for me, but I think I understand most of what's going on. Essentially, endorsing Xubuntu but installing LXDE, right? My primary goal is to clean out any extra packages/desktop environments. Well, keeping Ubuntu/Unity on my netbook as well as LXDE, but then running a LXDE/*buntu system on my Hp laptop.

---

### Post by motocollage on 2013-02-19
also, I've been running into this text in terminal, I'm assuming dealing with proprietary windows software: 


How do I 'hit' <OK> ? I can't seem to exit terminal once this prompt occurs.

---

### Post by Bucky Ball on 2013-02-20
I had the HP 6000 myself until it died. Long story.

Should be running fine now with all flavours.

---

### Post by sudodus on 2013-02-20
> **motocollage said:**
> snowpine, I followed the link and copied the Remove Ubuntu code into terminal (on my secondary linux machine, HPpavilion DV6000:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I was doing something the other day and got a similar message. This system has Lubuntu, Lubuntu Netbook, GNOME/OpenBox and Ubuntu. After the results, I will try it on my primary linux machine, the Acer D250.

Another option I thought of was to do a complete re-install from the disk. So far I have been installing from the UBUNTU 10.04 LTS Desktop Edition cd that came with "The Official Ubuntu Book." Will I have the option for a minimal ubuntu install from that disk?

More importantly, as mentioned in the code above, why am I "unable to lock?"

seppalta, i'm gonna put that link on the backburner. A little technical for me, but I think I understand most of what's going on. Essentially, endorsing Xubuntu but installing LXDE, right? My primary goal is to clean out any extra packages/desktop environments. Well, keeping Ubuntu/Unity on my netbook as well as LXDE, but then running a LXDE/*buntu system on my Hp laptop.
It looks like you have another program running, that is also managing installation and removal of program packages, for example Synaptic or Software Center. Close that program and try again!

---

### Post by sudodus on 2013-02-20
> **motocollage said:**
> also, I've been running into this text in terminal, I'm assuming dealing with proprietary windows software: 


How do I 'hit' <OK> ? I can't seem to exit terminal once this prompt occurs.
Press the TAB key to move the cursor (active field) to the OK field, and press Enter to confirm.

---

### Post by snowpine on 2013-02-20
> **motocollage said:**
> 
Another option I thought of was to do a complete re-install from the disk. So far I have been installing from the UBUNTU 10.04 LTS Desktop Edition cd that came with "The Official Ubuntu Book." Will I have the option for a minimal ubuntu install from that disk?


It's time to trash your 10.04 disk, as support ends in 2 months.

Here are easy instructions to perform a "minimal Ubuntu install" if that's your thing: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by motocollage on 2013-02-26
[QUOTE=snowpine;12515943]Here are instructions to remove Xubuntu and install "pure" Lubuntu: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

So, I copy/pasted the terminal command for removing Xubuntu for 12.04. After lines of code, here is the response:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libxine1-ffmpeg : Depends: libmad0 (>= 0.15.1b-3) but it is not going to be installed
 libxine1-misc-plugins : Depends: libgraphicsmagick3 (>= 1.3.5) but it is not going to be installed
                         Depends: libmng1 (>= 1.0.10) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

---

### Post by unheeding on 2013-02-26
> **motocollage said:**
> [QUOTE=snowpine;12515943]Here are instructions to remove Xubuntu and install "pure" Lubuntu: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

So, I copy/pasted the terminal command for removing Xubuntu for 12.04. After lines of code, here is the response:

```
The following packages have unmet dependencies:
 ...

```[/QUOTE]

Try this command:

```
sudo apt-get -f install
```

It should install the dependencies.

---

### Post by motocollage on 2013-02-27
I should clarify at this point that this pertains to my Acer netbook running 12.04 (I know I've been jumping around a bit):

> **unheeding said:**
> Try this command:

```
sudo apt-get -f install
```

It should install the dependencies.

Okay, before I proceed, this was returned:

```
The following packages were automatically installed and are no longer required:
  gir1.2-totem-1.0 libunity6 linux-headers-3.2.0-36 linux-headers-3.2.0-37
  linux-headers-3.2.0-37-generic libtotem0 libdee-1.0-1 linux-headers-3.2.0-36-generic
  gir1.2-totem-plparser-1.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I assume this command would be 'sudo apt-get autoremove' followed by the lines above. What I am concerned about is 'libunity6.' I just want to make sure that that is an aspect of Xubuntu and not my standard Ubuntu shell. I do like Unity and standard Ubuntu on my netbook, but I would like to try out LXDE with it as well. I simply want to purge as much of Xubuntu/XFCE as I can.

---

### Post by sudodus on 2013-02-27
```
sudo apt-get autoremove
``` is a complete command, and it will remove the above mentioned packages. If you want to reinstall Unity, no problem. You can do that from a text screen according to the tips in the 'psychocats' link, if you have removed or broken every graphical desktop environment.

If you don't want to remove all of them, remove those you want to remove with
```
sudo apt-get remove package1 package2 ...
```

Learn more about apt-get in ```
man apt-get
```

---

### Post by motocollage on 2013-03-01
Haha, okay! I think I've indeed broken every desktop environment successfully. Here are some of the issues that I am having:

Unity/Gnome are still showing up in my login manager, but definitely do not work

LXDE has been installed, but the system is acting strange and unstable.

Xfce/Xubuntu has not been removed/purged, but I can and sometime feel I need to login to an xfce session, but it is also unstable.

Trying to use gparted to create a new ext4 partition, but cannot strictly copy my Home folder to because I am not allowed permissions (and I have yet to backup anything linux)

When I log into ttyX shell or whatever the correct terminology is, a wireless bug keeps printing "no mac address," but someone informed me that is a harmless bug. I just know that it wasn't happening until I did whatever I did. 

The netbook is dual booting this broken 12.04 and windows 7 starter. I used pendrive linux usb iso program on the windows side previously to create different flash drive 'live cds' and it is not allowing me to anymore. The system is again telling me that I don't have permission to even format the 8g flash drive. I'm not even sure if these problems are related.

And....that's all so far. I have a command that I'm going to try for backing up my home folder, but then I think the best idea is a clean reinstall, maybe just go straight to the most recent .iso of Lubuntu and be done with it. However, I need to create a bootable flash drive, and can't seem to do it anymore. I've dug myself into a hole for sure! This is fun! (but also a little inconvenient). Maybe I should try to create the usb drive from linux, but I'm worried if my system is stable enough to do so (and I need to do a little research to see how best to proceed). Hmmm....

---

### Post by tartalo on 2013-03-01
> **motocollage said:**
> I think the best idea is a clean reinstall, maybe just go straight to the most recent .iso of Lubuntu and be done with it.
Yes, a clean install is the best option, just backup your important data and create a separate home partition this time.

> However, I need to create a bootable flash drive, and can't seem to do it anymore.

With your pendrive mounted type:
```
df -h
```
This command will show the partitions you have and how much space is used/free in each, it shouldn't be difficult to identify your pendrive.
Let's say that your pendrive is in **/dev/sdb** then this command would be enough.
```
sudo dd if=/path/to/your/lubuntu.iso of=/dev/sdb && sudo sync
```
Replace the paths for input file and output file. Be **very careful** because if /dev/sdb is not your pendrive you could completely erase another hard drive! Also notice that you type the address of the hard drive, not the partition (/dev/sdb not /dev/sdb1)

Hope that makes sense

---

### Post by motocollage on 2013-03-07
Thanks for the help all. I actually got pendrive linux to work on my windows partition and created a live usb lubuntu 12.10 to boot from. I successfully backed up using Deja Vu, decided to restore my windows partition to factory settings (its pretty much useless) and shrink that partition, then installed Lubuntu to the larger partition. So far, all is well after installing the b43 driver that my netbook needs, my only problem now is that I cannot wirelessly access the secure network setup signal at my university. Other than that, I'm a lubuntu guy now!

---

### Post by sudodus on 2013-03-07
Congratulations :KS and you are welcome :-)

---

### Post by Bucky Ball on 2013-03-07
I have marked this thread as 'Solved' for you as the regular 'Solved' method is not working since the forum upgrade. ;)

Good luck with it and don't forget to post a new thread with a descriptive title for any further issues/probs/questions.

---

