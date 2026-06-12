---
title: "create an option for a FAST startup"
date: 2009-06-06
forum: General Help
---

### Post by shuntya on 2009-06-06
I've already been trying for some weeks, tried lots of different methods, looked in many websites, downloaded and tried inx, DSL, FreeDOS.....

The idea is this:

I have a netbook, with Ubuntu netbook remix on it. It loads up pretty fast already.
Now, there is sometimes, in the subway or such, when I want to write something. Open my netbook, turn it on, write a text file (or edit one already created) and that's it.

So I don't need GUI, or network support, or multimedia, or.... anything but the ability to browse the file system and start vi or nano.

It would be nice if I could add an option in GRUB to select such a startup, and I've sucessfully set up a FreeDOS installation  in a separate partition which loads in about 5 seconds, but I can't browse my linux filesystem with that...

Is there a way of telling Ubuntu that I just want a VERY BASIC command line? I think not with grub, but maybe I can setup some menu after choosing Ubuntu who lets me choose between loading everything or just keeping the command line. As I said, no network, no MP3 player, no USB support.... If could be done, It should take very very few seconds to start. And that would be nice :) like opening a paper notepad to write something down.

Thanks !!!!

---

### Post by Confuseling on 2009-06-06
Does this help?

[http://ubuntuforums.org/showthread.php?t=843646](http://ubuntuforums.org/showthread.php?t=843646)

(Don't worry about the howto - read the rest of the thread, it seems it's unnecessary... Though note I haven't tried it myself)

---

### Post by shuntya on 2009-06-06
thanks !!! :)
it keeps loading lots of stuff I don't need, but it's definitely an improvement !!

EDIT: I'm doing some research on the kernel options to see how to edit them to make it load as fast as possible, I found this incomplete list, in case someone is interested:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

And  just found this very long, very complete, very complicated list :)
[http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php)

---

### Post by sdennie on 2009-06-06
Is there a reason you can't use suspend/resume for this?  A resume from suspend should take 5 or fewer seconds and you have your full desktop ready to go.  Most machines can stay suspended for several days on a full battery so, battery drain isn't really an issue.  In fact, it may be better on the battery than the battery drain of starting the OS (though, I have never measure this so, I don't know).

---

### Post by shuntya on 2009-06-06
Well, sometimes I have the laptop off for a long time, and I just want to turn it on for some minutes to write something, so I prefer to have it turned off. The suspend / resume is not a bad idea, anyway.

I just saw how fast can it boot up with FreeDOS and was thinking it could be a way of doing so with Ubuntu, too, without need of having a whole separate partition only for this.

Im investigating on how to tell the kernel I don't want to load network and other stuff, and I may end up having very fast boot times.

You remember when computers booted almost instantly? wasn't it nice? :)

Un saludo, compañero hispanohablante ! ;)

---

### Post by Confuseling on 2009-06-06
Personally, I'm dual booting with Moblin beta for exactly this reason. It boots RIDICULOUSLY quickly.

Obviously, if you don't have the space you don't have the space - but it's worth considering. It's still beta, but it's at the point where you can use it to look stuff up / take notes without hassle.

Good luck in your hacking enterprises, whatever you end up choosing!

---

### Post by shuntya on 2009-06-07
confuseling: Thanks for the tip !!!!

space is not a problem, what I can't is to boot up a FreeDOS partition, as I can't access my linux partition from there.

Downloading moblin now :) let's see how it works on VirtualBox !!!

---

### Post by shuntya on 2009-06-07
I'm thinking.... could it be possible to install a second kernel in some folder in my disk, compiled only with minimum disk browsing and vi / nano for editing? then add a link to it on grub.
That should be like 0.5 seconds boot time.....

---

### Post by blueridgedog on 2009-06-07
> **shuntya said:**
> I'm thinking.... could it be possible to install a second kernel in some folder in my disk, compiled only with minimum disk browsing and vi / nano for editing? then add a link to it on grub.
That should be like 0.5 seconds boot time.....

You could start with the moblin kernel...they have already done most of the work (or any of the the small linux kernels).

---

### Post by shuntya on 2009-06-07
Now that seems like a very very good option :)
So.... download moblin, get the kernel on my disk (not overwrite the one I already have) and tell it not to load the GUI... maybe even recompile the kernel and take out lots of unneeded stuff?

well, seems now I have some research to do, and lots to learn :) thanks for the advice !!!!! I will post my results when I got some. (lets say some weeks, hahah)

:)

---

