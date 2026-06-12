---
title: "Problems with Ubuntu Lucid Lynx 10.04 UNR on Dell Mini 9"
date: 2010-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by psypher on 2010-05-04
Hi All,

Starting this thread to highlight all the issues I have with Ubuntu Lucid UNR and hopefully help anyone else in solving their issues. I have to say I'm quite disappointed on how badly Ubuntu Karmic and Ubuntu Lucid works on these Dell Netbooks. I would have really though Canonical would spend some time on perfecting the OS for these devices as they are one of the flagship Dell products which comes preloaded with Ubuntu. But lets see what we can figure out.

Specs:
Original Dell Mini 9 (Inspiron 910 with no 3G)
4GB SSD Drive
1GB RAM
16GB SD Card

Ubuntu Lucid 10.04 Netbook Remix is installed
Used the standard UNR live cd to create a bootable USB stick and installed from there

Root installed on SSD, USR folder mounted to a 4GB ext4 partition on the 16GB SD card. The 2nd partition is a 12GB FAT32




Here is a current list of issues I have:

[LIST=1]
[*]Wireless does not work out of the box
[*]I get errors on boot about disk devices not present
[*]Suspend does not work
[*]With a 4GB SSD drive, the disk manager claims the disk is failing
[*]FN Radio button does not work
[/LIST]

**Wireless does not work out of the box**
To fix the wireless you need to do the following:
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```
You had to do the same thing in Karmic. This is actually unacceptable, how can this issue be ongoing for 2 releases? Jaunty did not have this problem.

Here are 2 bug reports I have found which are related, yet with which one the actual issue lies I don't know. Will try and figure out and report back.

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/441492](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/441492)
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/455509](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/455509)


**I get errors on boot about disk devices not present**

On boot I get the following error
error: no such device: 9ce72834-f095-44d3-9674-1c8a582355d4
error: hd2,2 cannot get C/H/S values


Looking through my grub.cfg I found this:

insmod ext2
set root='(hd2,2)'
search --no-floppy --fs-uuid --set 9ce72834-f095-44d3-9674-1c8a582355d4

I am not familiar with grub2, does anyone know what this section does? I had a hunch that due to using a USB stick to install, grub has somehow gotten confused as to which drives the OS is installed on. So I tried running
```
sudo update-grub2
```

Now when it boots up I get this error:

error: no such device: 9b5a5f78-cf75-4915-ab47-39e6e8bf8760
error: hd1,2 cannot get C/H/S values

sudo blkid shows me this:
/dev/sda1: UUID="9ce72834-f095-44d3-9674-1c8a582355d4" TYPE="ext4" 
/dev/mmcblk0p1: LABEL="14GB-SD" UUID="C09D-4576" TYPE="vfat" 
/dev/mmcblk0p2: UUID="9b5a5f78-cf75-4915-ab47-39e6e8bf8760" TYPE="ext4" 

/dev/sda1 is root
/dev/mmcblk0p2 is the 4GB SD card partition which is mounted as **/usr**

Not sure how to proceed, has anyone else gotten a similar issue as this? Any ideas?

**Suspend does not work**

This one is the worst. Due to having an SD card in the machine while suspending, waking up from a suspend crashes the OS. This only started in Karmic :(

[A thread on MyDellMini has a suggested workaround]("http://www.mydellmini.com/forum/ubuntu-netbook-remix/14722-suspend-hibernate-mini-9-broken.html"), but in my case this does not work. The thread has a hack to unmount the sd card before suspending. But in my case I actually have /usr folder mounted to the sd card to free space on the SSD. Since I only have a 4GB SSD this is a necessity.

Does anyone how to successfully unmount and remount an SD card when doing a suspend action?


**With a 4GB SSD drive, the disk manager claims the disk is failing**

This is not so much a problem stopping me from using the device, just a slight shock at 1st and then an extreme annoyance. Despite what the immediate error (which pops up when you 1st boot your freshly installed netbook) tells you, the device is NOT failing.

Due to the error: your device is being used outside it's design parameters, I suspect that it's just giving a warning that having only 4GB or physical space is not the recommended minimum specs for ubuntu. I would suggest a WAY BETTER error to display which does not cause your users to freak out that their brand new SSD is already failing and spend countless hours trying to make dead sure that it's not. That was a fun weekend :(

Disabling the SSD from notifying when it's failing is a workaround, but now I won't know if the disk is REALLY failing.

**FN Radio button does not work**

Not the end of the world but still quite annoying that something as simple as FN Radio does not disable the bluetooth and wireless in this device. I'm thinking of adding the last 2 issues to the 100 paper cuts project. MAYBE in 6 months when Maverick is out these annoyances will be fixed. 

Regarding the other issues. Personally I think it's Canonical's best interest to make every effort to get them sorted. The Dell Mini's are exceptionally important in their word of mouth marketing plan, and right now the last 2 releases of Ubuntu has run quite shoddy. The type of users these devices are touted for are just not interested in fixing stuff like this. On the Dell Mini's, Ubuntu must just work.

Check back here soon, going to log/track down bug reports on all of these problems.

Any feedback/assistance/suggestions welcome.

---

### Post by yooy on 2010-05-08
About suspending, I'm surprised that the trick didn't work for you

It's possible that you did something wrong, so I'll explain it fully, no offense.

sudo gedit /usr/sbin/pm-suspend

go to the fist line which is not bashed (#), which is:

export STASHNAME=pm-suspend

just before this line, you add

umount /dev/mmcblk*


Hopes it helps

---

### Post by scross01 on 2010-05-09
I was having the same suspend issue with my AcerAspireOne  while SD cards are mounted. Adding the  umount command to the suspend script worked like a charm,Thanks!

I actually added the line to the start of the /usr/lib/pm-utils/bin/pm-action script which /usr/sbin/pm-suspend is linked to.

---

### Post by psypher on 2010-05-11
I had already tried that, just tried again now. Same issue, it suspends but when i move the mouse the screen unlock would come up and I would only get 3 characters of my passwd in and then it freezes. 

remember my USR folder is mounted ON the SD card. If I unmount it, how can the scripts run properly if they are in the usr folder?

---

### Post by yooy on 2010-05-11
> **psypher said:**
> . 

remember my USR folder is mounted ON the SD card. 

HO! I'm very sorry, I didn't get that point. 
Well, it's unusual. Did your configuration (I mean with the USR folder on the SDHC card) worked flawlessly with one of the previous versions of Ubuntnu? 

I know that it won't help but just for information Lucid run very easily on my 8Gb Dell mini 9, it logs in and logs out very quickly and the suspend problem was the only one I encountered until now. I installed lucid four days after the official release and after the usual first update, the hardware manager find the appropriate drivers for the wireless card.

---

### Post by psypher on 2010-05-11
Unfortunately no, on jaunty i had everything on the SSD. But i'm now installing more apps than before and using my netbook more so have been forced to use the SD for space. I just know that suspend worked on jaunty with the SD in, then it was just a separate storage device. Does anyone know how the SSD suspend works? Does it also umount the disk? If not then why does karmic and lucid crash when an SSD is installed? I need to figure out that bug instead of getting a workaround to work.

Boot speed is very quick. But sometimes it would be great to suspend for a little and resume with all the apps u had open.

With regards to the wireless drivers. I don't argue that it's very easy, for the average Ubuntu user, to fix the problem. I'm just annoyed that it's been ongoing for more than 6 months.

I just wish for just ONE release of ubuntu, they spend all their efforts JUST on bugs. No new features, nothing flashy, just fix bugs, as many as possible. Then at least we have something extremely stable and polished to build from. But whats happening now is they just keep piling on the features and less is being done bout the same issues people have been having for ages.

I don't know, am i thinking about this the wrong way?

---

### Post by yooy on 2010-05-11
> **psypher said:**
> 

I just wish for just ONE release of ubuntu, they spend all their efforts JUST on bugs. No new features, nothing flashy, just fix bugs, as many as possible. Then at least we have something extremely stable and polished to build from. But whats happening now is they just keep piling on the features and less is being done bout the same issues people have been having for ages.

I don't know, am i thinking about this the wrong way?

No, you're right but what you're describing looks like Debian. The thing is that there is no UNR with Debian yet and you'll have to compile yourself the drivers for the Broadcom wireless card (or change it). But anyway, a Debian netbook edition would look like what you're dreaming of. 
The thing is that Ubuntu works with a significant amount of repositories including a lot of things which are excluded in the Debian project because there are not fully compliant, not fully open source... More compatibility means easier installation for average guys but more bugs... For instance SD card were one of the thing which are a little bit difficult to have working flawlessly on Debian because Debian's people are working on the core of the OS, and well, if you want SD card you'll have to DIY. I tried lenny and love it but it was too much work for me to have it working with new devices. And Fedora has a lot of bug too. 

But in my opinion, we have to blame Dell and others for not helping a bit the development of linux OS. Dell for instance made a great move releasing the very good Dell mini 9 with ubuntu but unfortunately they choose to develop their own edition forgetting to spend enough money on it. And what was very stupid was to choose a wireless card with proprietary drivers. 

Anyway, my blabla  won't help you :-D and you're probably suffering reading my goofy English. IMHO you'd probably better to change your SSD, Supertalent have good 16 and 32Go SSD not very expansive. Add Ram and why not a better and more compatible wireless card. Eventually, for 100$ you'll have by yourself a splendid refurbished Dell mini 9 which is for me the best netbook released. Still looking for its replacement and probably upgraded it this way. But you'd probably think of that yet...

---

### Post by JEBB on 2010-05-12
Thus far I've encountered two problems with 10.04 on my Dell Mini 9 that may force me to go back to 9.04 from which I updated last week.  

The first is the sleep/suspend problem mentioned above, which was not a problem with 9.04.

The second is the inability to turn off the touch pad, also not a problem in 9.04.  The ability to turn off the touch pad is important with a Dell Mini 9 because it's touch pad is extremely sensitive and occupies a large percentage of the wrist rest area.   To do any 10-finger typing is nearly impossible with the touch pad on, at least for me.  (In fact to type this I had to go back to my MacBook.)

---

### Post by bajabaq on 2010-08-21
For the "Failing disk drive" problems - go into System->Administration->Software Sources and enable lucid-proposed (Updates, 3rd checkbox down). Get the proposed releases, install and reboot and it should go away

---

