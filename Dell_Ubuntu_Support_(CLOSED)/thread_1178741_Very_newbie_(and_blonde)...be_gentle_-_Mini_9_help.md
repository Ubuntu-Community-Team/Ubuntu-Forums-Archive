---
title: "Very newbie (and blonde)...be gentle - Mini 9 help needed."
date: 2009-06-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Teya on 2009-06-04
Hi. I am a complete nubface to linux and ubuntu. I was completely digging it...until day 2. I did upgrades and my little 4GB Mini pegged the HD out and now I have 500MB free. I did all the things I could find about dropping your cache DL files and my 4 GB system (which only registers 3.4GB per the df -Th in terminal) has sucked up so much I'm not sure what to do. So I figured, "Hey...I just got this 3 days ago...Dell.com can help." The chat service for the mini's told me that they couldn't help me and gave me a linux ubunto number that doesn't support the mini's who gave me another support number that gave the response of "reload your OS, but don't load any add-ons." And their tech supervisor told me that "if you bought it online you saw that it only had 4GB of HD and it will run" to which I told him that if I gave him a calculator with a 1 and a + and - sign, then it would run too. Just not effectively. 
 
So I am bowing to the masters of the all knowing...begging for people who are not microsoft babies like me. Hell, I'm an IT tech and I don't really know what to do. I jumped into the linux pool with no floaties.
 
...Help me Ubunto...you're my only hope...

---

### Post by anjilslaire on 2009-06-04
Clean the apt-cache with this command:
```

sudo apt-get clean

```

Then, set Synaptic to automatically delete the downloaded update files after installation:
Settings >Preferences >Files
"Delete downloaded packages after installation"

Also, do the following to remove any unneeded files:
```

sudo apt-get autoremove

```

---

### Post by snowpine on 2009-06-04
You are in the right place for help. These forums are very friendly and knowledgeable (though remember anyone can post here, so don't just blindly follow advice). Anjilslaire's suggestions are both good ones. (In case you don't know, the place to enter terminal commands is found under Applications-Accessories-Terminal, and Synaptic is under System-Administration.)

My only other suggestion to add is to pick up an inexpensive SD card for storing your documents and photos and stuff. A 4gb card will double your storage. :)

---

### Post by crewkid89 on 2009-06-04
Definately SD cards are so cheap nowadays it's almost silly not to have a few.  I always end up buying them for things like cameras and class projects and then they lay around.  After I got my mini I started putting videos, music, and other files on them.  I have even heard of some people mounting their /home partition on to an sd card but that's a little too advanced of a solution.

---

### Post by jaqrah on 2009-06-05
Welcome to the World of the Mini 9!

Follow Anjilslaire's good advice.

I highly recommend the following site:

[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

It has great information for your Mini 9.  The latest article about using command line coding is very applicable to your current situation.

> Does the same as clean but it only removes package files that can no longer be downloaded, and are largely useless (my preferred method)
[color=blue]sudo apt-get autoclean[/color]

Used to remove packages that were automatically installed to satisfy dependencies and that are no more needed (another favorite)
[color=blue]sudo apt-get autoremove[/color]

Frees up space by clearing out the local repository of retrieved package files
[color=blue]sudo apt-get clean[/color] 

If its in your budget, upgrade to a larger ssd.  Its a bit pricey but a good investment in my book.  Right now you can get a 16gb or a 32gb but soon you will be able to get a 64gb or a 128gb (see the following post)

[http://ubuntuforums.org/showthread.php?t=1175901](http://ubuntuforums.org/showthread.php?t=1175901)

---

### Post by Cowchip7 on 2009-06-05
Another option would be to uninstall the programs that you will never use. For example, my mini 9 came with a telephone program, a webcam program, etc. However, my mini doesn't have a webcam!!! So I used Synaptic to uninstall these unnecessary programs.

I even heard of some people uninstalling the Open Office programs. Fortunately for me, I have a 32gb HD in mine! :D

Good luck. (Buy an SD card!)

---

### Post by Teya on 2009-06-05
> **jaqrah said:**
> Welcome to the World of the Mini 9!
 
Follow Anjilslaire's good advice.
 
I highly recommend the following site:
 
[http://www.ubuntumini.com/](http://www.ubuntumini.com/)
 
It has great information for your Mini 9. The latest article about using command line coding is very applicable to your current situation.
 
 
 
If its in your budget, upgrade to a larger ssd. Its a bit pricey but a good investment in my book. Right now you can get a 16gb or a 32gb but soon you will be able to get a 64gb or a 128gb (see the following post)
 
[http://ubuntuforums.org/showthread.php?t=1175901](http://ubuntuforums.org/showthread.php?t=1175901)
 
 
I really appreciate everyone's help. I have been in the Microsoft IT business for the last 15 years, so i am very much behind the power curve. The 16GB Drive costs $90, and that defeats the purpose of me making it work. My friend's 9 is awesome, but he is only using like 1.7GB so there is plenty of free space. And I haven't used anything on the mini BUT the updates. =sighs= When I do a df - Th I get the following:
 
Filesystem Type Size Used Avail Use% Mounted on
/dev/sda2 ext3 3.4G 2.9G 418M 88% /
varrun tmpfs 501M 88K 501M 1% /var/run
varlock tmpfs 501M 0 501M 0% /var/lock
udev tmpfs 501M 36K 501M 1% /dev
devshm tmpfs 501M 0 501M 0% /dev/shm
lrm tmpfs 501M 1.9M 501M 1% /lib/modules/2.6.24-24-lpia/volatile
fuse.gvfs-fuse-daemon 3.4G 2.9G 418M 88% /home/teya.gvfs
 
 
 
OK, also, here are 2 other questions:
 
1. The new version that I have seen mentioned out there that will run on this system, will loading that from scratch make my space issue less?
 
2. If I use a disk duplicator and duplicate my friend's mini9 HD, is there a way to change the Admin name and PWD? 
 
I bow to the infinite wisdom of those who have dealt with the much nicer linux system for much longer then mine. It seems 3 days is not enough. LOL
 
Again, I very much appreciate the help. Dell seems to think that the solution of "don't update because ubuntu has so many updates" is a viable one. I think it's a crock of bull-pucky.

---

### Post by Cowchip7 on 2009-06-05
Xubuntu is a stripped down version of Ubuntu. It might solve your problem. However, I am unsure if it is 100% compatible with the Mini 9. Does anyone have experience with Xubuntu on the mini 9?

---

### Post by snowpine on 2009-06-05
If you want to stick with the pre-installed OS, I don't think you really have a "problem"--the computer works fine and you have 500mb free, correct?--you just don't have much space left over for personal documents. An SD card for extra storage will get around that problem.

If you are open to installing other operating systems (either a different release of Ubuntu or a non-Ubuntu Linux distro) then you have a whole world of possibilities. My highest recommendation goes to CrunchBang Linux. It is an unofficial "lightweight Ubuntu" that fits in about 2gb and runs very well on the Mini 9. It has a geeky, minimalist vibe that is not for everyone (but I love it). Also, a lot of users seem to love Ubuntu Netbook Remix 9.04 on the Mini 9 (I can't stand it personally). Here's a great site for more research: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

Personally, I am dual-booting two different Linux distros on my 8gb Mini 9: SliTaz on a 500mb partition and Arch on the remainder. I can't really recommend either of those distros for a new Linux user, however. Sticking with Ubuntu or one of its derivatives is probably your best bet for now.

---

### Post by Teya on 2009-06-05
So 500MB is good?  For MS it's not really great, that's why I'm so confused and wanting the help.  But if it is going to be enough for me to do the websurfing that I need to do, that will be fine.  I have a 250GB HD that I use for anything else.  I only actually want Pidgin and the web browser.  There is other stuff I could strip out?
 
AGAIN...you guys are awesome!!!  THANK YOU!!!

---

### Post by Teya on 2009-06-05
Is there a way to tell what programs I actually need and what I don't?  Would deleting some of them using the Synaptic Package Manager help?

---

### Post by snowpine on 2009-06-05
> **Teya said:**
> Is there a way to tell what programs I actually need and what I don't?  Would deleting some of them using the Synaptic Package Manager help?

Safest is to use the Add/Remove Programs application. It only lets you remove user applications, not mission-critical system packages (like Synaptic). I would start by removing OpenOffice if you don't need it; I think it is the biggest application in Ubuntu.

---

### Post by Talon2 on 2009-06-05
Here is what I would do:

- Save all files you need to keep to a flash drive or other backup storage.

- Installation 9.04 Netbook Remix:

    [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

- Install Restricted Extras

- Uninstall programs/stuff you won't use via:

    Adminstation > Snaptic Package Manager

- Add a sd drive to use as storage.

Background:  I have owned my Mini 9 for about 7 months now.  The Ubuntu 8.04 that came pre-loaded was a source of many problems.  I am of the opinion that it was not ready for prime time on netbooks.  9.04 Netbook Remix does appear to be ready for prime time.  I wiped 8.04, installed 9.04 NR and I currently can't find a single bug considering how I use the system.

---

### Post by jaqrah on 2009-06-05
I don't remember which apps are part of Dellbuntu (ubuntu 8.04 that came with your mini 9) but I removed the following from my 8.10 Ubuntu:

Games (its an all or nothing package)
Cheese (if you don't have a webcam)
Open Office apps
Gimp Image editor
Brasero (not burning any discs ;) )
Orca
f-spot
xsane (no scanning)

hope this list helps.

---

### Post by Cowchip7 on 2009-06-05
Unlike Talon2, I believe the Dell's lpia 8.04 is fine. Everything works out of the box and I have yet to have any problems. Just uninstall the programs you don't need and add an SD card... Voila!

If you don't mind having to deal with hiccups every now and again, you can download a vanilla ubuntu install.

---

