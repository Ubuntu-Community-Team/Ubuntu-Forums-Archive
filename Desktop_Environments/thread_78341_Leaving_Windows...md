---
title: "Leaving Windows.."
date: 2005-10-18
forum: Desktop Environments
---

### Post by New_newbie on 2005-10-18
At first, don't mind my English. I'm from the Netherlands.

I am a MS Windows XP user, and I was thinking if it would be a good idea to use Linux from now on.

Computer Properties
Intel Pentium III Processor
664 MHx
128 MB of RAM
Harddisk: 9 GB

Is it a good decision to start using Ubuntu, or should I keep using Windos?

And if you think it's a good decision, could you tell me how to format my harddisk before installing Ubunutu. (2 GB is very litlle space, so I think it's better to format my harddisk)

Anybody can help me? Thanks.

---

### Post by YanH on 2005-10-18
What you could do to help your decision is to try out a Ubuntu Live disk before deciding to whether to install over windoze. This allows you to try out Ubuntu without affecting your hard disk. You can download this from [http://ubuntu.hands.com/releases/5.10/]("http://ubuntu.hands.com/releases/5.10/").

In terms of dual booting I would agree that your 2gb hard disk does appear a bit small.

The Ubuntu installer will format your hard disk for you if you decide to overwrite xp.

---

### Post by New_newbie on 2005-10-18
[QUOTE=YanH]What you could do to help your decision is to try out a Ubuntu Live disk before deciding to whether to install over windoze. This allows you to try out Ubuntu without affecting your hard disk. You can download this from [http://ubuntu.hands.com/releases/5.10/]("http://ubuntu.hands.com/releases/5.10/").

In terms of dual booting I would agree that your 2gb hard disk does appear a bit small.

The Ubuntu installer will format your hard disk for you if you decide to overwrite xp.[/QUOTE]


Thanks, I'll try it out. ;)

---

### Post by David Marrs on 2005-10-18
I would try to dual boot if you can because you never know quite how you'll take to Linux, or to Ubuntu. It's reassuring to know that the familiar is there in case you need it. I also second the recommendation to run the live CD. It will help you understand what (if anything) you need to do to make the transition easier.

---

### Post by kurtkraut on 2005-10-18
[QUOTE=YanH]What you could do to help your decision is to try out a Ubuntu Live disk before deciding to whether to install over windoze. This allows you to try out Ubuntu without affecting your hard disk. You can download this from [http://ubuntu.hands.com/releases/5.10/]("http://ubuntu.hands.com/releases/5.10/").

In terms of dual booting I would agree that your 2gb hard disk does appear a bit small.

The Ubuntu installer will format your hard disk for you if you decide to overwrite xp.[/QUOTE]

Trying out the Live CD is a good suggestion. But while you are testing Ubuntu Live CD you have to consider that running it from a CD is at least 5 times slower than a installed version. If you experience low performance, don't mind, you won experience that if you install it in your PC.

I've noticed many people that quited installing Ubuntu because they thought that it woul be as slow as Live CD is.

---

### Post by deathbyswiftwind on 2005-10-18
I would definatly install it. I am a linux newbie/mid level user. Ive tried it off and on for years. But I am very happy with Ubuntu. Especially the apt-get program. If Ubuntu doesnt do it for you, you could always download Xandros Linux which is pretty much windows kinda sluggish but it will give you some good learning. Also I recommend Linux for Dummies or a book along the lines even if its outdated somewhat you will still learn some commands needed I know it helped me out alot

---

### Post by matthias_k on 2005-10-18
2 GB is WAY too few space. I found myself resizing my root partition in Debian Sarge which was 5 GB soon enough, so don't make the same mistake and you'll safe yourself a lot of trouble.

Other than that, if you decide to install Ubuntu, you will probably want to have at least two partitions: A swap partition (Linux uses a separate partition for swap space, not just a file like Windows), and at least one partition to mount the root directory. You can also create a third partition to mount e.g. /home but I advise against it when you're not really sure how to size the partitions properly.

For the root partition you should be safe with 10GB, plus the space you will occupy with your personal stuff which goes in home, like downloads, videos, music, etc. I have mounted both on one big 76GB partition. That should do the job :)

---

### Post by eric71 on 2005-10-18
Another thing to consider is that 128 megs of ram is low to run Gnome or KDE.  It will definitely seem more sluggish at first than Windows.  There are more lightweight desktop environments and window managers that will be great on your hardware.  You might try installing Ubuntu (realizing it may be quite sluggish at first), enable the universe and multiverse repositories in Synaptic and installing xubuntu-desktop.  THis will give you a much leaner, faster desktop (Xfce - kind of like Gnome Jr.) and basic applications for your hardware.  Then you can remove most of gnome if you want (though it's nice to keep gnome-system-tools for graphical configuration utilities, and gnome-volume-manager to manage what happens when you insert media or usb drives, etc.

Ubuntu is so flexible, you can fins a set-up for any hardware you want.

---

### Post by jrev on 2005-10-18
I think you can install ubuntu and keep winxp 
I am running ubuntu 5.04 Hoary which is very stable 
you should see our wiki 
do you read french ?
[http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)
or [https://wiki.ubuntu.com/UserDocumentation:cool:](https://wiki.ubuntu.com/UserDocumentation:cool:) 
and of course [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by New_newbie on 2005-10-19
Well, I have installed Ubuntu now.

It's not that sluggish, but I have a problem.

I haven't managed to install programs on Ubuntu. For example, I tried to install Mplayer. I have read somewhere on the internet (google) that I have to search Mplayer with Synaptic and install the Packages after that. Well, Synaptic didn't find anything.
After that I tried to install Realplayer. I had download the .bin file (to the Desktop), opened a terminal.

cd Desktop
...@Computer:~/Desktop$ sudo ./RealPlayer10GOLD.bin
Password:
sudo: ./RealPlayer10GOLD.bin: command not found

And thank you all for all of the advice btw.

---

### Post by Spie on 2005-10-19
Take a look at [Easy Ubuntu]("http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23"). That's a small program that installs all the basic things on your Ubuntu system. Also Realplayer and codecs for Mplayer.....

---

### Post by New_newbie on 2005-10-19
[QUOTE=Spie]Take a look at [Easy Ubuntu]("http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23"). That's a small program that installs all the basic things on your Ubuntu system. Also Realplayer and codecs for Mplayer.....[/QUOTE]

Thanks a lot!

---

### Post by Cathbard on 2005-10-19
Welcome to Linux. I suggest you have a look at [The Ubuntu Guide]("http://ubuntuguide.org/")
It was written for Hoary but it will still lead you in the general direction.
(Is the breezy one almost ready?)
You may also want to try [Easy Ubuntu]("http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23")
It's a great tool for the noob.

Linux may take a bit to learn, esp. if you have "bad" Winblows habits but it is worth the effort.

---

### Post by gaz_666 on 2005-10-19
i am also new to linux as a whole, im ordering a laptop to install it to and get to know it on before i install it on the big pc and destroy windoze once and for all. anyone got some minimum sys requirements i should look for?

---

### Post by skirkpatrick on 2005-10-19
Breezy contains a page that is almost identical to the Unofficial Guide.  Go to System->Help and select the Starter Guide.

The biggest problem you'll find with laptops is proper support for wifi and battery status.

---

### Post by gaz_666 on 2005-10-19
[QUOTE=skirkpatrick]The biggest problem you'll find with laptops is proper support for wifi and battery status.[/QUOTE]

hmmm, not good, wanted it wireless aswell.

---

### Post by Cathbard on 2005-10-19
Don't despair!!  WiFi will work on a lot of cards. It's usually a good idea to do a bit of research before buying any hardware, this is particularly true when using Linux.

Here's two links for you to look at:

[List of Linux Compatible WLAN]("http://www.linux-wlan.org/docs/wlan_adapters.html.gz")
[Linux WiFi]("http://www.linuxhomenetworking.com/linux-hn/wmp11-linux.htm")


(Edit) That list isn't the one I thought it was. I did have a more up to date one but I seem to have lost it. Anybody got a better one?

---

### Post by Cathbard on 2005-10-19
OK, here's a better one. I shou;d have known LinuxQuestios would have the answer.

[WiFi list at LinuxQuestions]("http://www.linuxquestions.org/hcl/index.php?cat=10")
[Compatible Hardware list]("http://www.linuxquestions.org/hcl/index.php")

---

### Post by gaz_666 on 2005-10-20
thats great, thanks, im as green as the grass when it comes to linux.

---

