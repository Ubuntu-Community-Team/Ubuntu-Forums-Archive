---
title: "kde 3.5.1, kde-devel is broken"
date: 2006-01-28
forum: Desktop Environments
---

### Post by Asraniel on 2006-01-28
I installed kde 3.5.1 from the "official" kubuntu reps, but now i cant install kde-devel anymore because it would break something. I hope this gets fixed, i would like to compile kde applications from source, and more important, develop something for kde.thx

---

### Post by magnusbb on 2006-01-28
3.5.1 isn't released yet.

---

### Post by Asraniel on 2006-01-28
but there is a kubuntu rep for it.... deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

but well, i had the same problem with kde 3.5 normal.

---

### Post by nrwilk on 2006-02-15
It's broken for me too under 3.5.1.  Are we screwed?  Should we downgrade to 3.5.0?

---

### Post by nrwilk on 2006-02-16
If I install kde-devel under 3.4.3, and then upgrade to 3.5.1, will the kde-devel packages still be valid, or would I need to download them again?

---

### Post by nrwilk on 2006-02-17
Anyone know the answer?  If I download kde-devel and THEN upgrade to 3.5.1, will the kde-devel packages be retained?  will I need to upgrade them?  Should I stick with 3.5.0?

---

### Post by Jucato on 2006-02-17
I'm not sure if downgrading would be a wise option. Is the 3.5.1 repository still enabled? What I did before was to install kdebase and kde-devel first before upgrading.

---

### Post by nrwilk on 2006-02-17
[QUOTE=Fenyx]I'm not sure if downgrading would be a wise option. Is the 3.5.1 repository still enabled? What I did before was to install kdebase and kde-devel first before upgrading.[/QUOTE]

That's exactly my question.  Does that work?  Or, will they be need to be upgraded too?  I've installed them under 3.5.  Can I upgrade to 3.5.1 having retained them?

---

### Post by Jucato on 2006-02-17
I think it would be best if kde-devel is upgraded too. But I'm not actually sure what you mean. Do you have kde-devel already installed? what version is installed/available? Mine is 5.44ubuntu2 (that's what it says in synaptic). I have the kde351 repository still enabled.

---

### Post by nrwilk on 2006-02-18
OK, here's what I have:
KDE 3.5.0
kde-devel 5:44ubuntu2

A couple days ago I had KDE 3.5.1 running, and the kde-devel packages were broken, they would not install at all.  I tried over a period of several days.  I had not disabled the 3.5.1 repository either.

I then had to reinstall for seperate reasons.  Which is why I now am running 3.5.0.

My question is:
Will I be able to use the packages contained in the kde-devel metapackage if I upgrade to 3.5.1, even though when I had run 3.5.1 before it wouldn't download due to having broken dependencies.

---

### Post by Jucato on 2006-02-18
I believe it will. just install kde-devel first before upgrading to KDE 3.5.1. That's what I did and it seems to be working fine. I'm not sure if doing it the otherway around breaks the kde-devel packages.

---

### Post by nrwilk on 2006-02-18
Is there any big reason to switch to 3.5.1?  I didn't really notice anything different about it while I had it installed.  I'd hate to install 3.5.1 and find that I can't use kde-devel.

---

### Post by Jucato on 2006-02-18
3.5.1 has some bugfixes. if you look around this KDE section of the forums, you might notice some threads where problems were solved by upgrading to 3.5.1. I don't think kde-devel will be unusable. Like I said, I'm using KDE 3.5.1 and have the kde-devel packages (Translation, Cervisia, KBugBuster KCacheGrind, Kompare, KUIViewer, Qt3designer, and Umbrello are the ones in KMenu).

---

### Post by nrwilk on 2006-02-18
Thanks for all the input, Fenyx!  I'm going to make the jump and upgrade to 3.5.1.

It did seem a bit more solid.

Hopefully the problem is soon fixed for those who want to download the kde-devel metapackage after having upgraded to 3.5.1.

---

### Post by Jucato on 2006-02-18
There is one aspect of this problem that I haven't thought about until now. kdebase (and the whole kde351 repository) is in breezy main. kde-devel on the other hand, is on breezy universe. It's quite possible that the universe repositories haven't been upgraded to 3.5.1, hence causing the conflict between the two versions. It's a possible theory... just wonder why it took me so long to think about it. :D

---

### Post by nrwilk on 2006-02-18
There you have it.

---

### Post by Jucato on 2006-02-20
nrwik, hope you haven't reinstalled yet. I might have another theory. By any chance, do you have kdebase and/or kdebase-dev installed?

---

### Post by nrwilk on 2006-02-20
Well, I had already reinstalled, but that was because I had a whole bunch of broken stuff which I wanted to get rid of.  Fresh installs are awesome.  But, I upgraded to 3.5.1 without any problems.  I just installed kde-devel before I upgraded.  The apps which were whining for it are compiling fine with the versions installed under 3.5 before upgrading to 3.5.1.

Also, yes I have both of the above mentioned packages installed.

---

### Post by Jucato on 2006-02-20
Oh i see. I was also thinking that kde-devel might not have upgraded properly if kdebase and/or kdebase-dev wasn't installed and upgrading to 3.5.1 before installing kde-devel.

Well, anyway thanks a lot. I tried making an "Upgrading to KDE 3.5.1" guide in the Kubuntu support section. That's why I was asking. Thanks again! :D

---

