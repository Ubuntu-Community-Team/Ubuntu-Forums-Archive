---
title: "Help! Slow Gaming performance in mi laptop Toshiba L45-b"
date: 2016-06-24
forum: Gaming &amp; Leisure
---

### Post by Jos_bernales on 2016-06-24
Hi guys! well im changing from windows because i dont like it, i dont know much about linux but im open to learn. hope some of you help me T_T... hahaha 

i have a  performance issue playing dota 2 from Valve/steam, i have tried to initiate steam in big picture mode but, the performance is poor too :(, Videos in HD too, and any other "demanding" and "stressfull" situation for my computer D:!

i have a Toshiba L-45b  Intel® Core&#8482; i5-5200U CPU @ 2.20GHz, Intel® HD Graphics 5500 (Broadwell GT2), 6gb of RAM and 700gb of Hard Disk...

i dont know what cause a drop of fps, it last not much but enough to see me death in team fights hahahah. when i unplug the "alimentation cable" from my laptop it recover his performance but, later it comes again that fps drop.

maybe some cool linux master can help ? :D! i will forever gratefull

i installed Ubuntu 16.04 LTS

---

### Post by oldrocker99 on 2016-06-24
Which version of Ubuntu are you using? The Unity desktop is pretty resource-intensive; Xubuntu, Lubuntu or Ubuuntu MATE (My perferred version) are all a lot lighter-weight than Unity or GNOME. That **may** well up your framerates.

---

### Post by Jos_bernales on 2016-06-26
man! thks for answering! i installed Lubuntu... doesnt changes much the Framerates...

and my version of ubuntu is 16.04 LTS ...??? i think?

and how do i install ubuntu MATE?

---

### Post by Omar_Jair on 2016-06-26
Ubuntu MATE can be installed like any other Ubuntu Distros with a LIVE USB or an installation DVD. It's easier to configure but the update process will be slow, also if you want a good performance you can choose to start steam only in your session manager with this info ([http://www.howtogeek.com/132549/6-tips-for-improving-game-performance-with-steam-on-linux/](http://www.howtogeek.com/132549/6-tips-for-improving-game-performance-with-steam-on-linux/)).

---

### Post by T.J. on 2016-06-27
> **Jos_bernales said:**
> Hi guys! well im changing from windows because i dont like it, i dont know much about linux but im open to learn. hope some of you help me T_T... hahaha  

Absolutely!  That is why we are here, and always happy to assist.

 > 

i have a  performance issue playing dota 2 from Valve/steam, i have tried to initiate steam in big picture mode but, the performance is poor too :(, Videos in HD too, and any other "demanding" and "stressfull" situation for my computer D:!

i have a Toshiba L-45b  Intel® Core&#8482; i5-5200U CPU @ 2.20GHz, Intel® HD Graphics 5500 (Broadwell GT2), 6gb of RAM and 700gb of Hard Disk...
 


I say this with the greatest respect intended, so please do not misunderstand me or think I am rude.  

Laptops with Intel chipsets (in general) are not the best gaming devices in the world.  Games are generally optimized for AMD or Nvidia chipsets.  That said, you might have some luck if you tinker with your settings.  Last I read, Intel's OpenGL drivers were not quite up to par with AMD's or Nvidia's, so you may have to wait for Intel to update them to get decent performance.

---

### Post by Jos_bernales on 2016-06-27
THks man, all of you are awesome; Btw no rudeness detected in your words, just pure truth... hahahah i just bought it with super effort last year and im dissapointed y_y...!!!, one last question, how am i supposed to know when my open gl drivers provided from intel are ready for ubuntu :3?

AAAnd for the guy up there, i already installed the steam in the session manager, but the performance still be like potato computer D:!

PD: long live PC mater Race! hahaah

PD2: sorry for my english D:

---

### Post by mastablasta on 2016-06-28
you can get more info on tracking development here: [SIZE=2]https://www.x.org/wiki/IntelGraphicsDriver/

you can try upgrading the drivers using PPA (xorg edgers for example or oibaf), you can try upgrading the kernel only or you can try a beta version of the OS which has newer kernel (just to see if it performs better).

[/SIZE]

---

### Post by T.J. on 2016-06-28
> **mastablasta said:**
> you can get more info on tracking development here: [SIZE=2]https://www.x.org/wiki/IntelGraphicsDriver/

you can try upgrading the drivers using PPA (xorg edgers for example or oibaf), you can try upgrading the kernel only or you can try a beta version of the OS which has newer kernel (just to see if it performs better).

[/SIZE]


That's a good idea, Mastablasta.  I hesitate to recommend it myself due to the possibility of breakage from lack of testing, then again if you have nothing to lose, why not?

---

### Post by mastablasta on 2016-06-29
sure, things can break with test version, but they seem to be broken already :P

another option is to simply install another distro with newer kernel (&drivers). Manjaro should be easy enough for the new users. I am not sure where OpenSUSE LEAP is with it's kernel but might also be an option. Fedora also had newer kernel.

---

### Post by Jos_bernales on 2016-06-29
i think i will install Ubuntu Mate, but dont know from where to download (and wich version D:). my plan is to create a booteable USB then install it to my computer. 

could someone tell me please from where i can download Ubuntu MATE?. and it is better decision to install Ubuntu Mate or to "update kernel and PPA and  the other things"?? xD

and finally, all the things you told me up, i didnt understand much and im afraid to break my PC D:, so if someone could tell me step by step y will gratefull forever and ever XD

---

### Post by T.J. on 2016-06-30
> **mastablasta said:**
> sure, things can break with test version, but they seem to be broken already :P

another option is to simply install another distro with newer kernel (&drivers). Manjaro should be easy enough for the new users. I am not sure where OpenSUSE LEAP is with it's kernel but might also be an option. Fedora also had newer kernel.


I have my doubts that will make much difference.  16.04 has the 4.4 kernel.  The latest is 4.6, which isn't horribly different.  I'd recommend reading the release notes on 4.5 and 4.6 before deciding to do anything.  Why jump off a cliff unless you are sure you are going to get something out of it? If Jos does need a newer kernel, there are better ways to get it.  I could compile it for 16.04 myself if necessary.

In my opinion, switching to Manjaro or Fedora is bad advice.  Please understand that I'm not picking on you specifically, but an LTS like 16.04 (or a heavily tested version like Debian) is much better than using a rapid release, bleeding edge, or rolling release version.   A lot of new Linux users do not understand the difference and give up on Linux because they run into bugs.  Rapid releases (every six months) rolling releases, and bleeding edge releases are generally best handled by developers and advanced users willing to deal with problems.  

Fedora is bleeding edge through and through.  Manjaro is based on Arch - which is somewhat bleeding edge, but on top of that, Manjaro is also a rolling release. As for OpenLEAP, IMHO - it was a terrible release. I say that as a fan of OpenSUSE. It's buggy and I advise new users to steer clear of it for a while. They went through a big transition with the last release. It didn't even boot properly on my hardware, which pretty much boots everything.

In good conscience, I highly recommend NOT using any of these unless you understand fully what you are getting into.  I'm not alone in this. Even Mark Shuttleworth recommends sticking to an LTS rather than regular 6 month Ubuntu release unless you are a developer.

---

### Post by T.J. on 2016-06-30
> **Jos_bernales said:**
> i think i will install Ubuntu Mate, but dont know from where to download (and wich version D:). my plan is to create a booteable USB then install it to my computer. 

could someone tell me please from where i can download Ubuntu MATE?. and it is better decision to install Ubuntu Mate or to "update kernel and PPA and  the other things"?? xD

and finally, all the things you told me up, i didnt understand much and im afraid to break my PC D:, so if someone could tell me step by step y will gratefull forever and ever XD


You can install Mate on your existing Ubuntu without reinstalling or making a USB as long as you have Internet access.  The easy way is to open a terminal:

[I]sudo apt-get install ubuntu-mate-desktop

[/I]After it finishes, restart and you can select Mate at the login screen.

As for your other questions, I am not certain.  I'll need to review the release notes on the newer kernels before I can answer them.  I can tell you that the odds of actually damaging your computer are very low as long as you stick with an LTS and not use any PPAs. (A PPA is a "use at your own risk" proposition.) I wouldn't concern yourself with it any more than you would Windows.  The worst case scenario might be reinstalling your OS if you break the wrong files.  Just be sure that you always backup important files regularly and you can pretty much never go wrong.  That's always good advice, even on Windows.

---

### Post by Jos_bernales on 2016-07-02
Bros! i installed an app called "3D Acceleration", i try to customize some settings and it all  went ultra smooth!, better than my previous version in windows :D... buuuut i think it can run better if i install Mate, my next question is if i will get any problem if i install Mate, this because i already installed another Desktop theme called Lubuntu.

---

### Post by oldrocker99 on 2016-07-02
No, you shouldn't have any problems if you install MATE. You select it at the login screen.

```
sudo apt-get install mate-desktop
```

---

### Post by T.J. on 2016-07-02
> **Jos_bernales said:**
> Bros! i installed an app called "3D Acceleration", i try to customize some settings and it all  went ultra smooth!, better than my previous version in windows :D... buuuut i think it can run better if i install Mate, my next question is if i will get any problem if i install Mate, this because i already installed another Desktop theme called Lubuntu.


Just a heads up.  Mate does not use hardware acceleration on the desktop by default.  You can fix this by using the mate-tweak package.

---

### Post by Jos_bernales on 2016-07-02
> **T.J. said:**
> Just a heads up.  Mate does not use hardware acceleration on the desktop by default.  You can fix this by using the mate-tweak package.

please tell me mooooar :-k:-k:-k  

Ubuntu Master Race!! XD

i get confused with that "you can fix this by using the Mate-tweak package", that phrase captivate my attention hahahah

---

### Post by T.J. on 2016-07-02
Mate was not originally designed with hardware acceleration. You get some acceleration automatically from your driver, but you will notice window tearing.  When you install the Mate desktop: *sudo apt-get install ubuntu-mate-desktop *it installs mate-tweak.  Mate-tweak can be used to turn on Compton or Compiz, an add-on OpenGL compositor.  That should eliminate the tearing and give your desktop windows the ability to synchronize with OpenGL.

---

### Post by Jos_bernales on 2016-07-22
hello guys! well im a bit disappointed... i dont know what to do... my Team fights online in Dota 2 are about 9 o 7 FPS.... im runnig mate, i activate the compiz via mate tweak, the aplication 3d acceleration its complicated to use.. i dont understand how to use it hahahaha well sorry guys for bothering you

how can i improve the performance for real T_T? i read about this "play on linux" app but i think it will run other games even slower... 
some help? can i use some command to give you information about and some of you can help me?

please i believe in ubuntu!
PD: sorry for being a noob y_y

---

### Post by mastablasta on 2016-07-22
for starters - do not use compiz when playing. in fact do not use it at all.

---

### Post by Jos_bernales on 2016-07-22
hmmm that didn't work tho... even i get worse performance D:! 

what to do next D:?

---

