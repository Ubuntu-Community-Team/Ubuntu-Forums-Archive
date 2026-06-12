---
title: "[SOLVED] Multiseat in Gutsy"
date: 2007-10-20
forum: Desktop Environments
---

### Post by arcik on 2007-10-20
Hello everybody out there!

I have tried to configure multiseat on my machine before, but after some hours (maybe days) of trying to configure my xorg.conf properly, I gave up.

With the new configuration tools available under Gutsy, I think to have managed to get the configuration right. I tried to follow the instructions provided by josean ([http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)), but must have made a mistake somewhere, because I did not get the desired result.

After that, I tried the script offered at [http://en.wikibooks.org/wiki/Multiterminal_with_Xephyr](http://en.wikibooks.org/wiki/Multiterminal_with_Xephyr). Then, I couldn't even get into the text mode (?!), so I reinstalled the system.

As for josean's advice, I believe to have reached the end of step 4. Then, I edited the gdm.conf file (simply filled the file with josean's data in the server section and changed the hardware phys. references according to my configuration) and went for reboot. After that, the machine tried to start GUI three times (one could see three times NVIDIA logo on both screens) and then informed me that (I paraphrase here, because I didn't manage to write it down - it automatically disappeared) there were to many parameters set on line 49 (think so).

I tried to find a mistake on that line, but found out that I hadn't edited that one at all. I also checked the servers section but couldn't find anything wrong.


As you have probably figured out, I am not very experienced in computing and Linux stuff. However, I love using Ubuntu and it would be a great help for me, if I could get it set as multiseat. From what I have read on this topic, it is definitely possible and I feel I am very near to success.

Could anybody, please, help me? Many thanks beforehand!

My graphic card is Nvidia Quadro FX3450 (dual-head).
My current *xorg.conf* can be downloaded here: [http://ubuntu.sytebarvy.cz/xorg.conf.txt](http://ubuntu.sytebarvy.cz/xorg.conf.txt)
My current *gdm.conf* can be downloaded here: [http://ubuntu.sytebarvy.cz/gdm.conf.txt](http://ubuntu.sytebarvy.cz/gdm.conf.txt)

---

### Post by arcik on 2007-10-22
I **solved** my problem using *Userful Desktop Multiplier* ([http://userful.com/products/free-2-user-license](http://userful.com/products/free-2-user-license)). Absolutely recommendable and also in Gutsy repositories. An application like this should become a standard part of Ubuntu - what about including something similar in Hardy Heron? That would be great.

---

### Post by JonathanRRogers on 2008-02-20
Unfortunately, the Userful Desktop Multiplier is not Free Software and therefore cannot become a standard part of Ubuntu. A better solution would be to create an easy way to configure a multi-seat setup using Free Software as in this [HOWTO]("http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html"). I have set up two seats on a single video card using that approach, but there were several things that needed tweaking and I still don't have all my keys mapped correctly. I'm going to be looking for easier ways to get this set up.

By the way, I see Ubuntu packages on the Userful website, but I don't see anything related to that in standard Gutsy repositories. Where did you find it?

---

### Post by arcik on 2008-02-25
You're right, Jonathan, Userful - as it is - cannot be included, that's why I put "an application like this". Any interested programmers out there? :)

As far as I can see on my machine, the Userful packages are part of the multiverse repositories. This should be true, as it is also reported on the Userful website ([http://support.userful.com/wiki/index.php/How_To/Desktop_Multiplier_on_Ubuntu](http://support.userful.com/wiki/index.php/How_To/Desktop_Multiplier_on_Ubuntu)).

If you find a more elegant way to a multi-seat setup in Ubuntu, post it here, please. That would be great!

---

### Post by JonathanRRogers on 2008-02-25
Yeah, you're right that Userful does appear in the Add/Remove Applications. On my Hardy amd64 system, it says it can't be installed, so I assume it's x86 only. Earlier I had looked for userful in the [Ubuntu package search]("http://packages.ubuntu.com/search?keywords=userful&searchon=names&suite=all&section=all") where nothing with userful in the name appears, so I was surprised to see anything in Add/Remove Applications.

But, the more important issue is Userful being proprietary. I have been using a multiseat configuration for the last few days using the method in this [HOWTO]("http://netpatia.blogspot.com/2008/02/multiseat-computer-with-ubuntu-804.html"), which can be set up using only Free software included in Hardy. However, there are some significant problems I haven't figured out yet, such as changing the mouse speed and making the mouse wheel work. Also, it took quite a bit of time and isn't for beginners. I intend to keep working on the few remaining problems with my setup and then investigate how it could be made easier to set up. I do think this could be a killer feature of Ubuntu (or any other GNU/Linux desktop-oriented distribution) that could help set it apart from Windows and OSX in the minds of many potential users.

---

### Post by andersja on 2008-03-25
Jonathan, please keep us all updated about your efforts! I've been looking for a "userful"-like, free desktop multiplier solution for a while. There's a number of Ubuntu brainstorm entries on this subject as well, but noone seem to have been interested...

See e.g. 
[http://ubuntuforums.org/showthread.php?t=707796](http://ubuntuforums.org/showthread.php?t=707796)
[http://brainstorm.ubuntu.com/idea/3153/](http://brainstorm.ubuntu.com/idea/3153/)
[http://brainstorm.ubuntu.com/idea/383/](http://brainstorm.ubuntu.com/idea/383/)
[https://blueprints.launchpad.net/ubuntu/+spec/multi-monitor-config](https://blueprints.launchpad.net/ubuntu/+spec/multi-monitor-config)

---

