---
title: "Deep Freeze"
date: 2009-04-20
forum: General Help
---

### Post by Exciterusa on 2009-04-20
There is a program called deep freeze, by faronics. Dot com for their website. 
What the program does is when you turn it on, a user can install, delete, infect do whatever they want and when you reboot everything is the way it was before they logged on. 
There are versions of deep freeze for Windows, Mac, and Linux. However the only linux version is for SUSE.
I was wondering if there were a way to setup ubuntu to setup a user, with the programs and settings that you want that would basically do the same thing. Reset everything on a reboot. This would be used in a public computer environment.

Thanks in advance.

---

### Post by Chainz on 2009-04-20
When searching for answer use keyword: kiosk
You'll find lots of answers ;)

---

### Post by Chainz on 2009-04-22
I just came to the new idea on how to make such a "kiosk" yourself.


[LIST=1]
[*]First you need (or probably just want, but not necessary) to create your own, customized Ubuntu LiveCD ISO.

Simple, just use Reconstructor, see: 
[INDENT][http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=29&Itemid=39]("http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=29&Itemid=39")[/INDENT]

Also lots of information on this can be found here:
[INDENT][http://maketecheasier.com/reconstructor-creating-your-own-ubuntu-distribution/2008/07/05]("http://maketecheasier.com/reconstructor-creating-your-own-ubuntu-distribution/2008/07/05")[/INDENT]


[*]Second, you just need to copy this ISO contents onto the hard drive like you were trying to install from your new created ISO to the hard drive, but at the end you will just keep on starting this liveCD from hard drive and each time you start it, it will be clean, because Live Session saves no data :)

See information here:
[INDENT][https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")[/INDENT]

Just part: Using LiveCD, points 1 to 3

[/LIST]



Just let me know if you have questions, I believe I might be not clear enough ;)

---

### Post by Exciterusa on 2009-06-20
> **Chainz said:**
> I just came to the new idea on how to make such a "kiosk" yourself.


[LIST=1]
[*]First you need (or probably just want, but not necessary) to create your own, customized Ubuntu LiveCD ISO.

Simple, just use Reconstructor, see: 
[INDENT][http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=29&Itemid=39]("http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=29&Itemid=39")[/INDENT]

Also lots of information on this can be found here:
[INDENT][http://maketecheasier.com/reconstructor-creating-your-own-ubuntu-distribution/2008/07/05]("http://maketecheasier.com/reconstructor-creating-your-own-ubuntu-distribution/2008/07/05")[/INDENT]


[*]Second, you just need to copy this ISO contents onto the hard drive like you were trying to install from your new created ISO to the hard drive, but at the end you will just keep on starting this liveCD from hard drive and each time you start it, it will be clean, because Live Session saves no data :)

See information here:
[INDENT][https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")[/INDENT]

Just part: Using LiveCD, points 1 to 3

[/LIST]



Just let me know if you have questions, I believe I might be not clear enough ;)

Ok, does that also allow you to change the image at anytime? Or do you have to create a new image if you want to install a program or just update the system?

---

### Post by Chainz on 2009-07-09
Not sure, that you'd just need to test I guess...

---

### Post by jahst on 2009-10-18
Hi,

I talk about a way to "deep freeze" a users account on this post..
You can easily change the script to "deep freeze" an entire PC.. but for my uses, this is enough. Been working great for years... but only been used on friends and students computers.. so not sure how strong it is in the wild.
Feedback would be appreciated.

Hope it helps.

[http://ubuntuforums.org/showthread.php?t=1294501]("http://ubuntuforums.org/showthread.php?t=1294501")

---

### Post by kasatmaya.wordpress.com on 2010-08-11
there is a bash script code to make a linux **deep freeze** system.
i used it in my linux mint system which based on the *Ubuntu Linux* distribution and it's working great for me. 
you can download the script here:
[http://www.linuxdedicatedwarnet.com/Deep_freeze.html](http://www.linuxdedicatedwarnet.com/Deep_freeze.html)

---

### Post by grg3 on 2010-10-19
There is a similar "deep freeze" script posted here: [http://users.telenet.be/mydotcom/howto/linuxkiosk/deepfreeze.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/deepfreeze.htm)

I have used this script and some of the ideas in the Ubuntu Kiosk discussed and it works great. The only caveat that I have is that you do not want to run the restore script without a backup in place. I have solved that problem with a script that checks for the existence of the backup tar file before restoring.

---

