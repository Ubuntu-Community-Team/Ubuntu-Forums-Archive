---
title: "Problems with intel HD 4000 (solved after upgrade to 12.04)"
date: 2013-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abdorefky on 2013-04-28
[SIZE=3]hi , i am having strange spikes when i activate gnome menu (it have water effect) or moving from panel menu to another .  even [/SIZE][SIZE=3]writting [/SIZE][SIZE=3]freez sometimes [SIZE=3]for 3 sec and  display 8 letter u wrote once ! [/SIZE]
last thing which lead me to write this topic , is that a youtube video is spiking too !!

this is the out put of $ lshw |grep VGA :
00:02.0 VGA compatible controller: Intel Corporation Device 0166 (rev 09)

how to test my vga ? or to get any more info 
i tried to install intel graphis but it required this " dependency is not satisfiable libglib2.0-0 (>= 2.31.18) 
1: can i install intel graphic's on my ubuntu 11.10 ? 
2: how to test my vga performance ?[/SIZE]

**[SIZE=3]## notice that my vga should be installed since my dell laptop came with  ubuntu installed on it [/SIZE]**(here is some photos) 


[IMG][[IMG]http://img94.imageshack.us/img94/8410/delldrivers.png[/IMG]]("http://imageshack.us/photo/my-images/94/delldrivers.png/")  Uploaded with [ImageShack.us]("http://imageshack.us")[/IMG]

[SIZE=3]as u can see the dell recovery too ( do u think they forgot intel driver or what ? )[/SIZE]
[IMG][IMG]http://imageshack.us/a/img14/585/dellrecovery.png[/IMG][/IMG]

---

### Post by abdorefky on 2013-04-29
how come no one know any thing ? 
if i am at wrong section then move me !!

---

### Post by Kopkins on 2013-04-29
You will find that complaining about not getting helped will usually only delay getting helped even further, because no one wants to help someone who expects to be helped immediately after they post. On the forums is is considered poor conduct to bump your thread more than once per day. Where I live, I've only been awake for about 4 hours. While your post was 15 hours ago, I was asleep for most of that time. Please realize that the support you get from here is from people all around the world who are VOLUNTEERS. No one is obligated to help you, but we will if we can. And just because no one posts immediately, it doesn't mean that no one knows a sulotion. I only check the forums every few days, and I suspect that most members down check more than onec per day. So if they don't see your post then they won't reply to it right away. Anyway, let's get started.

Can you expand on the "spikes"? I'm guessing you mean CPU spikes. How high does the cpu go? When I watch youtube videos my CPU "spikes" too. It goes up to about 60% until the video finishes buffering. Same with using the water effect. 

Has this behavior always existed or did it just begin? 

What kind of hardware are you running? What kind of computer? How old is it?

EDIT: If you have Intel HD 4000 you must have a new processor. If you do, why are you using an older version of ubuntu? Also, I would consider thinking of upgrading to a more current release like 12.04, because 11.10 is reaching end of life in may, just a few weeks away, when it will no longer recieve updates.

Good luck,

Kopkins

---

### Post by abdorefky on 2013-04-30
Dell - inspiron 5520
i3-3110M , 4 GB ram 1600 MHZ , temp is 51 
my cpu usage while playing a video is   9-15 %  at 1200 MHZ . that the load on buffering and playing at the same time .

---

### Post by Kopkins on 2013-04-30
Can you try booting in fallback graphics mode? Select the recovery entry in the grub menu while booting, then select resume boot. See if your issues are still there. I would also see if you can reproduce the problem on a live cd. Try a live cd of 12.04 or something. 9-15% is pretty normal in my book as far as streaming and buffering video goes, but freezing is not. 

Good Luck,

Kopkins

---

### Post by abdorefky on 2013-04-30
this behavior exist from the beginning  , 
the spike's that happened is that screen display hang for 2 or 3 sec !!

the youtube videos started to hang every 20 sec , it was clear since i installed dark shine theme , but the hang on happened on the video only , and the video sound continue playing while the video screen hang !!!!

but the typing also hang !! while you typing u will find the screen hang and for 3 sec u see nothing of what u are still typing and suddenly many letter appear once !! . this could not happened on pentium !!! 

btw , what's your pc hardware ? u already have a high pc usage unlike me .

---

### Post by abdorefky on 2013-04-30
i have edited post 4 to include laptop model 
alright i will try a live cd , stupid from me that i haven't tried that .

i have no idea about fallback graphics mode ;/ . also my grub doesn't show up . because i only have ubuntu 

u asked why i dont upgrade . u can find all the info here 
[http://ubuntuforums.org/showthread.php?t=2136677](http://ubuntuforums.org/showthread.php?t=2136677)

---

### Post by Kopkins on 2013-04-30
Try holding shift after the bios passes, I think that should bring up the grub menu. 

I have a Macbook Pro 8GB RAM intel i5-sandybridge

---

### Post by abdorefky on 2013-04-30
what a great key to show the grub menu
now i can log into previous version also got rest ubuntu to factory setting
but i can't find fallback graphics mode.
-----------
i have tried ubuntu 12.10 remix , and it work perfectly :( . but i can't upgrade also 
how can i know that intel driver is installed or not ? should i install driver or shouldn't since 12.10 worked with out installed driver

---

### Post by abdorefky on 2013-04-30
i had downloaded system profiler to display my laptop information and it gave me those 

**display **:
       resolution : 1366x768
       vendor     : the X.org foundation 
       verion      : 1.10.4

**OpenGL** :
            vendor     :unkown
           renderer    :unkown
             version    :unkown
 Direct rendering    : NO

---

### Post by abdorefky on 2013-04-30
[IMG]http://img259.imageshack.us/img259/4347/xorg.png[/IMG]

---

### Post by Kopkins on 2013-04-30
> **abdorefky said:**
> what a great key to show the grub menu
now i can log into previous version also got rest ubuntu to factory setting
but i can't find fallback graphics mode.
-----------
i have tried ubuntu 12.10 remix , and it work perfectly :( . but i can't upgrade also 
how can i know that intel driver is installed or not ? should i install driver or shouldn't since 12.10 worked with out installed driver

There isn't a setting for it. You just have to boot into recovery mode. Then select resume boot and you will be on the fallback graphics.

---

### Post by abdorefky on 2013-05-01
the fall back mode force me to log into gnome classic. which have no effect at all.and i can't test the bug there . 
does the xorg eror on the pictuer i sent mean something ?

---

### Post by Kopkins on 2013-05-02
I don't know. I don't know much about xorg. I could keep googling it, but so could you. At this point you know as much as I and I'm not going to keep looking for answers on the internet. You'll have to do research yourself or wait for someone else to help. 

Good Luck

---

### Post by abdorefky on 2013-05-02
thx for your help , btw have you managed to fix your spike's ?

---

### Post by abdorefky on 2013-05-02
can u send me a pic of the your x diagnose report , like the one i sent ?

---

### Post by abdorefky on 2013-05-02
that Xorg report i sent , adding a new line each time the menu hang 
looks like i am finally detected the problem :)

---

### Post by oldfred on 2013-05-02
Is this system BIOS or UEFI?

One Dell user mentioned sputnik, which I had not heard of. I guess it is a ppa of all the fixes needed for Dell systems. 
And somewhere was a comment that 13.04 now has all of the features of sputnik in it. So you can use 12.04 and add sputnik or 13.04.

---

### Post by abdorefky on 2013-05-04
i have AHCI BIOS

this dell spuntik is a ppa that has all the fix's for Dell XPS and not for my inspiron 
here is detalis about them 
[https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel](https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel)
[https://launchpad.net/~canonical-hwe-team/+archive/sputnik-policykit](https://launchpad.net/~canonical-hwe-team/+archive/sputnik-policykit)
what they mean by policykit ? 

i tried to contact dell teams at the lunchpad , but so far only poweredge answered me (which i found that its for servers) 
i am trying to contact other teams like dell team , 

what is that lunchpad any way **? can i trust them ?**

---

### Post by oldfred on 2013-05-04
Launchpad is a site for software. You need to decide if the uploader is someone you trust.

Have you seen this?
[http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)

---

### Post by abdorefky on 2013-05-05
i read the link but he have much problems than i have, any way , my update manager finaly pormated me to upgrade to  12.04
[http://ubuntuforums.org/showthread.php?t=2142437](http://ubuntuforums.org/showthread.php?t=2142437)

---

### Post by abdorefky on 2013-05-07
Problem solved after upgrading to ubuntu 12.04 and i am sure that the error was the OpenGL because it wasn't installed on 11.10 and i found its data on 12.04 

ty for help every one

---

### Post by Kopkins on 2013-05-08
That's great to hear about your success. Now you don't have to worry about it again for a long time since you are on LTS now. 

Kopkins

---

