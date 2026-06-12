---
title: "i think i hate linux."
date: 2006-02-17
forum: Desktop Environments
---

### Post by rmg on 2006-02-17
hi everybody. i'm a longtime linux user. i've been a linux user for seven years and i've used linux exclusively on my own machine for five. i want to say, before i begin, that i have used slackware (when i first started), debian, gentoo, and now ubuntu and i would say ubuntu is hands down the best in terms of ease of use and things actually working correctly. in fairness, gentoo was pretty good too. debian was nightmarish, but i liked apt so much i used it anyway for many years.

now then, there are two applications that i want to make work. if they can be made to work properly, i will not hate linux. if not, i think i will.

the first is brahms, the kde midi composition program. i would so love this program to work. i've tried to get it to work on debian, gentoo, and now ubuntu with no success. it just crashes when you try to open the score. and there's no sound. (note: i am not using "kubuntu," which is why i'm posting here rather than in the kubuntu forum.) if i could get rosegarden to work, i might be satisfied with that instead, but it absolutely must have sound working correctly.

the second is blender. now blender seems to run the way it's supposed to (i'm no expert on it, my little brother turned me onto it, but he's a windows user, so obviously it works fine for him). the problem is that the interface is totally broken. it seems to be some kind of opengl thing, but the menus are broken and drawn completely incorrectly (partially transparent, behave somewhat strangely with respect to the mouse) and the icons and so on don't really show up. i don't know how to describe the brokenness, but it makes the program entirely unusable. presumably, this isn't normal behavior, so i would be interested to find out how to make it work properly. my video card is a matrox g450 or something like one.

please advise on this highly unfavorable state of affairs. i have no plans to switch to windows, but i certainly don't want to hate my operating system. i'm tired of it holding me back and keeping me down. i emplore you to help me out here.

---

### Post by angkor on 2006-02-17
Could you post a screenshot of Blender? I just installed it to try it out and it looks ok to me (yet I'm definately not an expert on Blender).

---

### Post by rmg on 2006-02-17
well, if there's some way i can upload them, sure. i don't have immediate access to any webspace, but i have some screenshots.

basically, there's a lot of artifacting, the icons are broken, and things that presumably should not be transparent are, making the menus difficult to read.

---

### Post by aysiu on 2006-02-17
[QUOTE=rmg]well, if there's some way i can upload them, sure. i don't have immediate access to any webspace, but i have some screenshots.

basically, there's a lot of artifacting, the icons are broken, and things that presumably should not be transparent are, making the menus difficult to read.[/QUOTE] Just upload it in your post. When you post, look at a section called **Additional Options** and then **Manage Attachments**.

---

### Post by rmg on 2006-02-17
okay, done, i think.

---

### Post by rmg on 2006-02-17
i just gave brahms another try and the problem is different now. the score opens after some cajoling, but the notes on the screen are completely broken. the bitmaps are sort of blown up and blocky and mixed up/broken. it's defintely not good.

and of course, no sound.

---

### Post by arctic on 2006-02-17
This sounds to me like a problem, caused by your graphic card or your Monitor (thus an Xorg problem) or presumably an I/O problem caused by the hardware not playing well with your motherboard...

Please check you systems /var/log folder for any error messages in the different files (messages, dmesg,..) and check if there is an xsession-error message. I guess you know how to read and troubleshoot them if you have used linux for seven years. Post everything that might look suspicious, so we can discuss this.

---

### Post by rmg on 2006-02-17
well, i looked into /var/log. a grep turns up no xsession errors nor does closer inspection of the xf86 logfile or any of the other usual suspects. indeed, the x log shows it likes my video card perfectly well -- as it damned well better: i got that thing just for linux.

my guess would be that there's some software problem related to opengl, like that it's not configured correctly. i've already wasted enough of my youth trying to fix things like this and i'm not going to try it again unless someone has a good idea of what's wrong. i'm pretty sure the brahms thing comes from the same error because the scores are basically opengl areas (if i remember the content of past segfault error messages correctly). the sound thing probably has something to do with artsd and/or broken midi support for my soundcard. of course, since they have this softsynth thing going on, you'd think my soundcard's midi would be irrelevant.

i can't believe i'm the only one in the world with these problems because i have a completely default install and my hardware is only unusual in that it is claimed to be particularly well supported.

---

### Post by rmg on 2006-02-18
word to all you hard searching mofos out there.

if you're trying to fix blender because the interface is breaking after you move your mouse the first time, i.e. turning from nice looking to grey and broken, it's not your fault: the ubuntu package you got is just broken. i had this problem, so i installed the binary package from blender.org (against my better judgement) and it friggin' worked! the interface is still slow and ghetto, but it does work.

the brahms thing continues to plague me however.

---

### Post by Hairy_Palms on 2006-02-18
im pretty sure i know how to get rosegarden4 working, first download and isntall automatix with
wget [http://beerorkid.com/automatix/automatix_5.4-2_i386.deb](http://beerorkid.com/automatix/automatix_5.4-2_i386.deb)
sudo dpkg -i automatix_5.4-2_i386.deb 
then tell it to do its thing on midi, then if you install rosegarden from synaptic it works, or at least it did for me.

---

### Post by nalmeth on 2006-02-18
yes, automatix can setup midi for you, if it hasn't been done. 

Debian sound system is complicated by a realtime-security issue, which can sometimes hamper certain functions or applications.  Especially the jack audio system. This may be causing you some problems aswell. 

If it helps, ubuntu seems to have solved this in the upcoming dapper release. I upgraded to dapper on a laptop, and jack came installed and setup. 

Try the midi setup with automatix, and if you 'hate' breezy, you could wait for dapper, upgrade now (change all instances of 'breezy' with 'dapper' in your /etc/apt/sources.list file --> sudo apt-get update, sudo apt-get upgrade), or live with what you can get.

Officially, dapper is not yet ready to be used for regular desktop use, but for bug-testing. Its due to be released in april

---

### Post by rmg on 2006-02-18
by god, it worked! that which i've sought for so long is now in my grasp... and now that i have it, i hardly know what to do. i love you, spartacus!

free at last, free at last, thank the lord almighty i'm free at last!

---

### Post by Tibor60 on 2006-02-18
Why not double boot with windows? You can save a lot on your nerves with a double-booting system. I use linux for two years, and I understand that it is a system for playing, undertanding how a PC and an OS works. But for a work without going mad you need a system on which you can simple log in and work. For my years with linux there was not a single day when I could work with linux without problems... linux is for problem-solvers. The printer is not printing, than the network is going out is business, or work 1-2week with the scanner to make work, etc,. etc., Play and collect experiments and knowledge with linux, but work with windows when you can not afford the time for the next problem-solving...

---

### Post by arctic on 2006-02-19
No offense, but Linux is not a system for playing around. It is a grown and mature Operating System. I use it since 2002 exclusively for professional work and I never ran into BIG problems. Actually I had more problems with my Windows systems (printers that were certified for WinME not working, Modems not connecting,...) than with any Linux distro I used or even OS2/Warp. It just depends on what hardware-mix you use when you use Linux.

---

### Post by Lord Illidan on 2006-02-19
[quote=Tibor60]Why not double boot with windows? You can save a lot on your nerves with a double-booting system. I use linux for two years, and I understand that it is a system for playing, undertanding how a PC and an OS works. But for a work without going mad you need a system on which you can simple log in and work. For my years with linux there was not a single day when I could work with linux without problems... linux is for problem-solvers. The printer is not printing, than the network is going out is business, or work 1-2week with the scanner to make work, etc,. etc., Play and collect experiments and knowledge with linux, but work with windows when you can not afford the time for the next problem-solving...[/quote]

I don't dual boot. Because Linux doesn't give me that much problems. True, maybe it is because I have the right hardware. But at least, it takes much less time than Windows to install and configure.

---

