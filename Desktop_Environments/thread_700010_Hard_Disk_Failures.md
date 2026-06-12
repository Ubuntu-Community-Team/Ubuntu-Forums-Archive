---
title: "Hard Disk Failures"
date: 2008-02-17
forum: Desktop Environments
---

### Post by Jcink on 2008-02-17
This is just a general question really, not sure it fits into this category.

Some people have been telling me that Linux has a higher chance of disk failure than windows.

> <Person> just dont under ANY circumstance...i repeat, under ANY ANY ANY circumstance, i dont care if the world is ending here...reboot without using the shutdown thingie (ie, dont reboot/shutdown using the button unless specifically instructed to)
<Jcink> why is that?
<Person> because it screws up hard drives
<Person> believe me, i know....ive done it
<Person2> you can really screw up your HD
<Person2> ive done it too
<Person2> lol
<Person> more than once iirc
<Person> and screwed as in "it wont work even under windows, or at least not reliably"
<Person2> i lost a 1.5 gig raid to it
<Person2> ^^
<Person> i lost TWO 160gb to it
<Person2> eerrrr 1.5 TB raid
<Jcink> what about if you freeze up and have no choice ? :s
<Person> oh
<Person2> gig, WTF
<Person> ack
<Jcink> cuz i have frozen lots of times and have had to do that
<Person> jcink: thats precisely what happened
<Person> jcink: it froze up during an installation, couldnt do anything....rebooted, hard drive went to crap
<Person> linux is not like windows when it comes to this sort of thing
<Person> windows is VERY VERY resilient when it comes to this
<X> now you guys are just scaring me
<Person> linux is NOT
<Person> its much more resilient if restarted in time sof HD idleness
<Person> but if its running when you reboot it, assume your computer is dead unless it works ;)

Now, I'm just curious, but I find it hard to believe that Linux is worse when it comes to this. I'm new to Ubuntu though and still a bit new at Linux as a whole, however. 

I'm thinking that the risk is about the same no matter what operating system you use, and those are just bad experiences. 

I have a CentOS Linux server for about a year and a half now and there have been instances where it's locked up and I needed to hit the power button (Although, not many). Have not had problems. (knock on wood) Furthermore on some test computers, I have hit the power button several times and nothings happened. I've had Ubuntu for about a week, and while toying with it I think I've had about 12 lockups and needed to kill the power. 

And I did something extremely stupid last night because I had no idea what was going on (black screen boot... i could never tell, but I found out how to see it later) and thought it was frozen; I turned it off while it was doing a filesystem check TWICE :| and obviously i/o was in use.

So I'm thinking this is a general problem with just about any OS, and it is a rare situation; and obviously its always best to shut down with the software power button and not the computer's power button.

It's kind of scared me though what these two said, and the person who I was trying to show how to install Ubuntu at the time to a test PC so he could play with it. Then he got scared of losing his 80 gig hd due to what was just said. 

And I'm just asking since now I'm curious. Do those statements have any merit in regard to Linux being less robust against hard disk failures? Thanks in advance.

---

### Post by amohanty on 2008-02-17
> I'm thinking that the risk is about the same no matter what operating system you use, and those are just bad experiences. 

Bang on target! 
There are just too many variables to predict a system loss based on HDD failure, I tinker with my laptop a lot which means lots of hard reboots, yet have yet to lose a single file let alone the entire HDD. But then again, where I work, high end servers with SCSI drives occasionally (though very rarely) get bricked. It happens, its hard to tell why always, and its absolutely impossible to predict. As far as Windows is concerned, prior to 2000 and server 2003, as far as resilience to crashes was concerned, there wasnt any :)

---

### Post by information_entropy on 2008-02-18
The power button and the drive do not know what operating system you are running
The power button even works if no OS is installed


If you are running Ubuntu 

```
sudo apt-get install smartmontools

sudo smartctl -A /dev/sda

```

will display the actual condition of the drive
if smart drive monitoring is enabled

replace sda with the actual drive if it is sdb or sdc 

Ask your friends if you can have all of those no good drives:-)

---

### Post by Jcink on 2008-02-18
Thanks to both.

Learned something new. :)

---

