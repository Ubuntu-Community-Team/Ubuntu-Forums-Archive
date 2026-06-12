---
title: "Compiz crashed after update"
date: 2011-04-04
forum: Desktop Environments
---

### Post by tybo42 on 2011-04-04
Hello,

This is the first thread I write, even though I've been using extensively the help of this forum. That's why I want to thank you all for your commitment to make Ubuntu accessible by everybody and provide a learning platform to this excellent OS.

My problem - I've had Compiz working pretty well for quite a long time on my machine (ubuntu 10.10 maverick... well I thought until now!! have we all just being updated to ubuntu 11.04, the Natty Narwhal????). Anyway, except for a small conflict with Docky, it was ok (when I would switch Ubuntu Off, a message would show up for few seconds saying that Docky needed compositing to work...). I wanted to use the package "tile" ans start messing around to install the compiz-unsupported package. That's when I realized that I had problem with my sources.list, and figured out that because of these problems I couldn't have that package to work... So, I erased from my sources.list all the lines talking about Feist or Gusty, since I'm working on Maverick I thought I didn't needed them, and that they were creating conflict. 

I updated, and now Compiz is not working at all. When I run "compiz --replace" a black stripe crosses the bottom of the screen, Docky gives continuously the message that it needs compositing, and actually all functionality associated with compiz as a window manager aren't working (even "moving window"...). I use metacity for now, and I don't have conflict... I just would like to get compiz to work again as I really liked my desktop cube!

I have to say that compiz-check runs ok (unless I let it disable compiz window manager, then it crashes), and when I run compiz I only get 

"compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png" 

which I don't think is the main problem.

Here is my sources.list -

# deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick universe
deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick-proposed restricted main universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security restricted main universe multiverse


I really need help, I already tried lots of stuff, I cannot document everything I did, but I'll be pleased to let you guys know what I've done, and would love you to tell what I should try...

Thanks in advance!!

Thibault

---

### Post by Sina_RJ on 2011-04-04
use fusion icon for reloading your window manager.
in that order the black line will disappear and everything would work.
i have this problem on 10.10 and this would fix it'i haven't upgrade to 11.04 so i don't know it'll work on that

EDIT: if it you don't know how to install or use it,go to general help search for docky problem,originally posted by myself,it's completely explained.
I hope that'll be helpful and work on 11.04 :)

---

### Post by tybo42 on 2011-04-04
Thanks for the reply. So I just tried that and have fusion icon working. I did reload the window manager, I saw some flickering and effectively docky is still working properly... not Compiz though. I still have no desktop effects. In the fusion icon, if I select "compiz" as the window manager, it keeps on doing the same stuff... any idea? 

As of my ubuntu... I haven't upgraded to 11.04, but it's still what showing in "system>about ubuntu". I'm not sure what happened.

---

### Post by Sina_RJ on 2011-04-04
no sry,i have no idea,i'm using that and that'll fix everything :(
i don't know what to do exactly,but we had this problem on 10.10 as well,try finding thread named problem with docky,last post by me,there is a suggestion from another user,that is another way,and related to compositing.
i have no more ideas,sorry if that doesn't work

if that worked don't remember to mark thread as solved ;)

---

### Post by tybo42 on 2011-04-04
ok thanks. You say you have seen the same problenm with ubuntu 10.10... was it solve? Because as I said, I don't think I've upgraded to 11.04 (I did nothing to do so), nothing changed since it appeared I'm 11.04...so I presume I'm still 10.10 actually.

Also I don't think Docky has anything to do with the problem... I think Compiz crashed and I can't have it to work again. I've been thinking that my video drivers crashed but I don't know how to actualize them... I have a Core Processor Integrated Graphics Controller. Any ideas how to reinstall the drivers?

---

### Post by Sina_RJ on 2011-04-06
you can use System-->Administration-->Additional Drivers
i think you can find it there

this thread will also help if i don't mistake
[http://ubuntuforums.org/showthread.php?t=1571583&highlight=docky+problem]("http://ubuntuforums.org/showthread.php?t=1571583&highlight=docky+problem")

---

### Post by tybo42 on 2011-04-06
Nope, the additional driver app does not find anything new... It is so weird cause I just install cleanly compiz again from scratch, and it still does the same - compiz --replace and nothing works, not even moving windows.

Do you think the fact that "about ubuntu" says I'm on 11.04, when I'm not, might create a conflict? I know that Compiz would not run in Unity for example... How can "downgrade" to 10.10?

---

### Post by tybo42 on 2011-04-06
Ok the version problem is solved, but compiz is still not working. I'm gonna start another thread with more explications about how that happened.

Should I close that one as "solved" or erase it?

---

### Post by Sina_RJ on 2011-04-06
no different :)
the boss will handle it if you do wrong ;)

---

### Post by tybo42 on 2011-04-06
Ok so I definitely solved my problem. The mistake i did was to erase the two sources about eyecandy. I just reinstalled them, and compiz works pretty well. The problem with ubuntu 11.04 is not a problem since I'm definitely running 10.10 (see another thread for that part). I still cannot run "tile" but i guess I'll see that later.

Thank you all!

T.

---

